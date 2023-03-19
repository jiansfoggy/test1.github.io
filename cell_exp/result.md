---
sort: 3
---

# Results

We did experiments on the certain theme. This table shows the results.

|                             | Crafts Hobbies | Day Time TV Shows | Movie Genres  | School Subjects |
|-----------------------------|----------------|-------------------|---------------|-----------------|
| Fold Num                    | 11             | 14                | 11            | 13              |
| Accuracy                    | 29/32          | 36/41             | 30/35         | 35/39           |
|                             | 90.63%         | 85.37%            | 85.71%        | 89.74%          |
| F1                          | 93.03%         | 85.00%            | 88.37%        | 90.47%          |
| AUC                         | 0.6042         | 0.4952            | 0.6122        | 0.5294          |
| Label Ratio 0/1 (Unit: set) | 28960/14282    | 6363/7660         | 29530/18636   | 25506/24367     |
|                             | 202.77%        | 83.07%            | 158.46%       | 104.7%          |
| Male/Female                 | 11/21          | 11/30             | 10/25         | 11/28           |
|                             | 90.91%/90.48%  | 90.91%/83.33%     | 70%/92%       | 81.82%/92.86%   |
| Sensitivity                 | 0.9091         | 0.9091            | 0.7           | 0.8182          |
| Specificity                 | 0.9048         | 0.8333            | 0.92          | 0.9286          |
| MCI/NC                      | 20/12          | 20/21             | 21/14         | 22/17           |
|                             | 100%/75%       | 85%/85.71%        | 90.48%/78.57% | 86.36%/94.12%   |
| Sensitivity                 | 1              | 0.85              | 0.9048        | 0.8636          |
| Specificity                 | 0.75           | 0.8571            | 0.7857        | 0.9412          |

MC-ViViT achieves over 85% accuracy on all four themes. The highest one is 90.63% from Crafts Hobbies. 
The accuracy of School Subjects reaches 89.74%, which is close to 90%. 
Three of the F1 Scores are more than 88%, only the F1 score of Day Time TV Shows is 85%. 
The accuracy and F1 Score solidly support that MC-ViViT has robust performance. 
The other evidence comes from AUC Score. The average AUC of all four themes is 0.56. 
Given that not all the clips has MCI features in the video, even for subjects with MCI, it is reasonable to predict parts 
of their video sequences as NC. 
Due to this reason, some subjects will be correctly predicted as MCI with low scores.