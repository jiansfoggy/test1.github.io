---
sort: 1

images:
  - https://github.com/jiansfoggy/test1.github.io/blob/develop/cell_strct/ViViT-TE.png
  - https://github.com/jiansfoggy/test1.github.io/blob/develop/cell_strct/ViViT-FE.png
---

# Video Vision Transformer (ViViT)

Tubelet Embedding helps to cut the input sequence into smaller segments, which can be processed independently. 

<p align="center" width="100%">
    <img src="https://drive.google.com/file/d/1sjqrpz487K68y_kQ9v4ml_JifPajNnpR/view?usp=sharing">
</p>

![Tubelet Embedding](ViViT_TE.png 'Tubelet Embedding')

Use the ViViT-FE backbone to extract the features from the tubelets.

<p align="center" width="100%">
    <img src="https://drive.google.com/file/d/1-Rq4p5DiyAx_UM9xvdOITj0OuqEP-9Ui/view?usp=sharing">
</p>

![ViViT](ViViT_FE.png 'Backbone')

{% for image in page.images %}
say sth
![test image {{ forloop.index }}]({{ image }})
{% endfor %}
