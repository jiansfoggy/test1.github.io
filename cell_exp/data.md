---
sort: 1
---

# Dataset Introduction

**Internet-Based Conversational Engagement Clinical Trial (I-CONECT) Study** dataset. 

```note
**I-CONECT Study** is funded by the National Institute on Aging (NIA). 
It studies the brain functions in older adults, the effect of social interaction on the mind and brain, and the 
prophylaxis of memory decline and dementia.

Website:[https://www.i-conect.org/](https://www.i-conect.org/)
```

I-CONECT was to explore how social conversation can help improve memory and may prevent dementia or Alzheimer’s disease 
in older adults. In this study, it followed research participants over the age of 75 in the Portland, Atlanta or Detroit
metro areas for about six months. All participants connected with the research team using senior-friendly technology for 
fun and engaging conversations in the comfort of their own home over a period of 6 months. I-CONECT Study convened 187 
participants and recruited different study team members to do 30-minute long chats with them 4 times a week for 6 months.
86 participants are labeled as NC, while 101 people are marked as MCI. Participants had conversation about 161 themes, 
such as SummerTime, HealthCare, Military Service, Television Technology, etc. The answers were filmed as a video. In each 
video, it starts with casual chatting, then formally shares story based on given theme, finally stops the interview by 
casual chatting again. The middle part contains more valuable features than the beginning and the ending parts. 

The follows are the details of researched themes. Subject Number is the total number of videos in the corresponding theme. Male/Female 
and MCI/NC shows the gender distribution and the category distribution. Frame Number is the total image number of each 
theme after converting from videos to frames.

|                | Crafts Hobbies | Day Time TV Shows | Movie Genres | School Subjects |
|----------------|----------------|-------------------|--------------|-----------------|
| Subject Number | 32             | 41                | 35           | 39              |
| Male/Female    | 11/21          | 11/30             | 10/25        | 11/28           |
| MCI/NC         | 20/12          | 20/21             | 21/14        | 22/17           |
| Frame Number   | 691872         | 859872            | 770656       | 797968          |

We used sequence-based approaches rather than frame-based ones to load the dataset, and extracted facial features via a 
dynamic approach. The response variable is boolean value. $1$ represents NC. $0$ denotes MCI.

# Data Processing

