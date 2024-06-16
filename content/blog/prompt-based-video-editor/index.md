---
title: 'AI-Powered Sports Press Conference Video Editor'
summary: 'A smart video editor that can extract and compile clips from a long sports conference video to aid creative professionals, in the sports industry, to get videos directly relating to their topical articles.'
date: 2024-06-10
authors:
  - admin
tags:
  - Projects
image:
  caption:
---

{{< toc mobile_only=true is_open=true >}}

AILA in collaboration with Twelve Labs hosted a Multimodal AI hackathon on June 9-10, 2024. One problem statement was to develop a prompt-based video editor to aid sports journalists in extracting topical clips from any one long sports press conference video on YouTube. My team finished 3rd overall amongst initially 20+ teams, and then 15 teams who completed the challenge to the standard of a demo. The tool is our team's IP and is currently unavailable until released as a product.

Our team comprised of [Aditya Vadalkar](https://www.linkedin.com/in/aditya-vadalkar/), [Hritik Agrawal](https://www.linkedin.com/in/hritik-agrawal-6945b3248/), [Shubham Maheshwari](https://www.linkedin.com/in/shubham-m27/), [Soham Bhokare](https://www.linkedin.com/in/sohambhokare/), and [myself](https://www.linkedin.com/in/shauryasikt/).

### Introduction

In the age of digital media, sports press conferences generate a vast amount of content that needs to be processed, summarized, and highlighted efficiently. This poses a challenge in video processing and retrieval.

### Initial Experiments

My team experimented with several video processing APIs. However, in this field of reporting where speed is of the essence, video processing took a long time. It took about more than twice the duration of the original video for its indexing and processing of embeddings.

#### Strategy

We strategized that a press conference can be perceived as a conversation between the individual panelists and all the interviewers who can be collectively treated as one interviewer. This is helpful as in such a case, the conversation in the form of audio or transcript is enough as an information source to index important data. Video processing is superfluous in this use case, and hence was discarded for the most part.

### Methodology

The URL to the YouTube video is first input to the chatbot. The entire video editing pipeline to extract relevant clips to the prompt was modeled by our team as follows:

#### 1. Audio Transcription

We stripped the audio from the downloaded YouTube video. Then the conversation was transcribed using AWS Transcribe which has speaker diarization enabled to identify what lines were spoken by which individual. The transcript was designed to be a json file with the following attributes for each line spoken:

1. Start time
2. End time
3. Speaker ID (integer label encoding)
4. Transcript (line spoken)

Consecutive entries with the same speaker ID were concatenated to improve coherence.

#### 2. Speaker Identification

First, we evaluated the Z-score of all the individuals' speaking durations from the preliminary transcript. Individuals above an empirically determined Z-score threshold were deemed as panelists.

As a robust strategy to handle conferences with multiple speakers, we used AWS Rekognition to identify speaker names from randomly sampled video frames of each panel speaker determined. Then the panelists were attributed their names in the transcript and all other speakers were attributed as one interviewer.

#### 3. Retrieval Augmented Generation (RAG)

In the processed transcript, alternating interviewer and panel speaker entries were paired to introduce Question-Answer pairing information before being indexed by the vectorstore. This is essential to retain the context of the panelist's answer from the interviewer's question. The vectorstore and the user prompt are sent to the RAG engine.

Then 2 different RAG branches with their unique conversational memories were created - one for objective query prompts and one for subjective. Objective query prompts are focused on some person or incident and relevant lines can be easily retrieved as QA pairs. Subjective prompts follow a theme like highlights, memorable moments, quotes etc. Subjectively relevant lines can be retrieved through extensive prompt engineering of the LLM, by virtue of the internal chunking of the vectorstore. The LLM used in this project is GPT-4o.

Finally, a sanity checker RAG engine is implemented to weed out any transcipt segments unrelated to the user prompt. It also provides a concise text summary for the final transcript.

#### 4. Clipping and Compilation

The retrieved transcript segments from RAG can be used to find the start and end timestamps of the clips required from the original video. These clips are then compiled together in chronological order.

#### 5. Feedback

The compiled short video of the relevant clips is output to the user. If unhappy, the user can give a feedback to the chatbot and it will loop to the RAG step with this new prompt. Thanks to the memory of the conversation, a suitably edited clip is output again until the user is satisfied.

#### 6. User Interface (UI)

The UI, designed using Flask due to Python compatibility, resembles a chatbot that initially takes the YouTube URL and then subsequently interacts via user queries regarding the video segments required.

### Demo

1. Demo for objective queries can be found [here](https://www.youtube.com/).
2. Demo for subjective queries can be found [here](https://www.youtube.com/).

### Conclusion

We built an industry-standard fast and accurate prompt-based video editor for sports conferences by focusing on the audio as the primary source of information. The fact worth notice is that our tool was the fastest in the competition as it takes about 10% of the initial video's duration for processing as opposed to the state-of-the-art video processor used by everyone that takes about 2.5 times the intial video's duration for processing. This speed would give sports journalists an edge in getting their material quicker than competitors in a fast-paced competitive market. 

#### Limitations
1. Chat history is implemented with basic functionality in RAG.
2. Interviewee face obstruction can lead to inaccurate face identification.
3. Access to age-restricted YouTube videos is not supported.
4. Only YouTube URLs are accepted for video link inputs.

#### Future Work
1. Chat history can be implemented in sanity checker.
2. Add subtitles to generated highlights.
3. Use metadata of YouTube videos that provide heatmaps helpful for summary/highlights generation.
4. Expand URL inputs to support more platforms.
5. Add support for translation of the output video to reach a multi-lingual market.