---
sort: 1
bibliography: ./ref.bib
csl: elsevier.csl
---

# Research Background

Alzheimer’s disease (AD) and related dementias (ADRD) are national public health issues with pervasive challenges for 
older adults, their families, and caregivers. 
AD/ADRD is not only ranked as the sixth-leading cause of death in the U.S., but the COVID-19 pandemic has increased the 
number of deaths related to the disease <cite data-cite="S1_5-AD_Facts_2021"></cite> [@S1_5-AD_Facts_2021]. 
Symptoms of AD/ADRD usually begin with Mild Cognitive Impairment (MCI) and include early onset memory loss, cognitive 
decline, and impairments with verbal language and visual/spatial perception. 
Approximately 12-18% of people age 60 or older are living with MCI in the U.S. 
Although older adults with MCI have the ability to independently perform most daily living activities such as eating, 
shopping, and bathing without help, the National Institute on Aging (NIA) estimated that 10 to 20% of senior people with
MCI will develop dementia over a one-year period [@S1_6-MCI_Intro_2021].
 
Magnetic Resonance Imaging (MRI) & Positron Emission Tomography (PET) scanning and neuropsychic examination are often 
used for detection of AD and dementia. 
These methods prove to be challenging for early MCI individuals given that the brain’s structural changes at this point 
might be harder to detect [@S1_7-MCI_Dialogue_2020].
Using accurate, non-invasive, and cost-efficient diagnostic technology has the potential to bolster the early detection 
of MCI and AD. A 2019 study proposed that early detection of AD would enable a reduction of neuropsychiatric symptoms, 
decrease healthcare costs, and improve quality of life [@S1_9-BEAT-IT_2019]. Studies have shown that MCI can affect 
the patterns of speech, language and face-to-face communication in older adults [@S1_8-MCI_CrossModel_2023]. 

# Past Works

Past works **emphasize** on the follows:

- Use the **traditional machine learning** (ML) methods to predict the MCI from normal cognition (NC), such as Support Vector 
Machine (SVM), Decision Tree, PCA+SVM, and K-means cluster.
- Use the **CNN-based** models to predict the MCI from NC, such as Inception-ResNet-V2, deep temporal–spatial networks, 
TMSAU-Net, and three-stream network.
- Research on the **medical image dataset**, such as brain Magnetic Resonance Imaging (MRI).
- Research on the **demographic information**, **patient interviews**, and **online structured datasets**.
- Research on the **facial features** extracted from videos, such as head pose, action units, eye gaze, and lip activity. They are
sort of manual crafted statistics.
- Film the **human reaction** to the certain questions and research the videos.

The **drawbacks** of the above:

- Traditional ML algorithms are <u>weak</u> to extract complete and craft features. They also <u>rely on</u> the structured datasets, 
which are not always easy to access.
- CNN-based models are <u>weak</u> to collect global spatial features. They also <u>rely on</u> multi-stream structure or 3D 
convolutional operation to extract the temporal information, which <u>costs more</u> computational source.
- The medical image datasets are <u>hard</u> to access. The demographic information, patient interviews, online structured 
datasets, and extracted facial features don't contain enough information. The human reaction films are less objective. 
The subject may act or reply based on the <u>default answers in purpose</u>.