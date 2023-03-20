---
sort: 1

images:
  - https://github.com/jiansfoggy/test1.github.io/blob/develop/cell_strct/ViViT-TE.png
---

# Dataset Introduction

**Internet-Based Conversational Engagement Clinical Trial (I-CONECT) Study** dataset. 

```note
**I-CONECT Study** is funded by the National Institute on Aging (NIA). 
It studies the brain functions in older adults, the effect of social interaction on the mind and brain, and the 
prophylaxis of memory decline and dementia.

Website:[https://www.i-conect.org/](https://www.i-conect.org/)
```

```note
- **I-CONECT Study** was to explore how social conversation can help improve memory and may prevent dementia or Alzheimer’s disease 
in older adults. 
- It followed research participants over the age of 75 in the Portland, Atlanta or Detroit
metro areas for about six months. 
- I-CONECT Study totally convened 187 participants and recruited different study team members to do 30-minute long chats with them 
4 times a week.
- All participants connected with the research team using senior-friendly technology for 
fun and engaging conversations in the comfort of their own home over a period of 6 months. 
```

In I-CONECT Study, 86 participants are labeled as NC, while 101 people are marked as MCI. Participants had conversation 
about 161 themes, such as SummerTime, HealthCare, Military Service, Television Technology, etc. 
The answers were filmed as a video. 
In each video, it starts with casual chatting, then formally shares story based on given theme, finally stops 
the interview by casual chatting again. 
The middle part contains more valuable features than the beginning and the ending parts. 

The follows are the details of researched themes. Subject Number is the total number of videos in the corresponding theme. 
Male/Female and MCI/NC shows the gender distribution and the category distribution. 
Frame Number is the total image number of each theme after converting from videos to frames.

|                | Crafts Hobbies | Day Time TV Shows | Movie Genres | School Subjects |
|----------------|----------------|-------------------|--------------|-----------------|
| Subject Number | 32             | 41                | 35           | 39              |
| Male/Female    | 11/21          | 11/30             | 10/25        | 11/28           |
| MCI/NC         | 20/12          | 20/21             | 21/14        | 22/17           |
| Frame Number   | 691872         | 859872            | 770656       | 797968          |

We used sequence-based approaches rather than frame-based ones to load the dataset, and extracted facial features via a 
dynamic approach. The response variable is boolean value. `1` represents NC. `0` denotes MCI.

# Data Processing

The facial features of Interviewees are valuable to our research.  
However, every video has complex background and interviewers' face, which has negative influence on predicting results.
To address this problem, we created the following cleaning instructions.

> 1. Drop the first 3 minutes and the last 2.5 minutes of each video. 
> 2. Apply EasyOCR[[Code](https://github.com/JaidedAI/EasyOCR)][[Demo](https://www.jaided.ai/easyocr/)] to detect the subject ID in the upper part of each frame.
> 3. If the subject ID gets detected, we go to step 4. Otherwise, we drop the frame and capture the next one.
> 4. Utilize RetineFace[[Paper](https://arxiv.org/abs/1905.00641)][[Code](https://github.com/serengil/retinaface)] to 
> crop the participants' facial images.
> 5. For cropped images, calculate the area of detected faces and the Intersection over Union (IoU) of them. If `IoU < 0.05`, 
> we kept the bigger face. Otherwise, drop both and go on.
> 6. Manually delete the interviewers' faces.

---

For the sake of taking advantage of videos thoroughly and predicting better, we select **K-fold Cross Validation**. 

```tip
$$K=\left \lfloor N_{Video}/L_{Fold} \right \rfloor$$,

where $$N_{Video}$$ and $$L_{Fold}$$ are the video number of the selected theme and that of each fold. We set $$L_{Fold}=3$$.
The videos in each fold belongs to different participants. 
```

---

To catch temporal information, MC-ViViT uses sequentially multi frames as the input. 

Let `L` be the number of consecutive frames in a divided segment, `N` represent the number of total frames.
$$\left \lfloor N/L \right \rfloor$$ is the number of segments for each video.
Thus, we cut each video into a certain number of fixed-length segments as inputs. 

```tip
Usually, L=16. It is validated in many related papers.
```

---

The Tubelet Embedding divides each segment into small cubes, and changes the input unit from 2D patch to 3D cube, 
which contains temporal information.

![ViViT](./ViViT-TE.png 'Backbone')

These cubic patches are non-overlapping. 
If the tensor shape of one video clip is `[T,H,W,3]`, where `T` is the frame numbers, `H` and `W` are the height of 
width of each frame, `3` represents the RGB channels. 
Then, the tensor size of each cubic patch is `[t,h,w,3]`. 
`t`, `h`, and `w` are the size of corresponding temporal, height, and width dimensions. 
$$n_{t}=\lfloor\frac{T}{t}\rfloor$$, $$n_{h}=\lfloor\frac{H}{h}\rfloor$$, and $$n_{w}=\lfloor\frac{W}{w}\rfloor$$ denote 
the token number of respective temporal, height, and width dimensions.