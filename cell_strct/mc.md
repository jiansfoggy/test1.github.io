---
sort: 2
---

# Multi-branch Classifier (MC)

Inspired by Inception Module and multi-models, MC takes multi-branch structure to provide different views and enrich 
representation as well. 
Different from Inception Module and multi-models, MC only does linear projection at each branch instead of convolutional 
operation or the neural network. 
In detail, MC consists of four FC layers. 

![Multi-branch Classifier](ViViT-AMLP.png)

The dimension change is $$64\rightarrow 16\rightarrow [8,8,8,8]\rightarrow$$ concatenate to $$32\rightarrow num\_class$$, 
where $$num\_class$$ represents the number of class. 
In our experiment, it is `2`. 
When we convert the dimension from `16` to `32`, the above figure shows that we apply multi-branch structure to convert the 
dimension to `8` and repeat `4` times. 
Then, we concantenate them as a 32-dimensional tensor. 
With this structure, MC can provide more features and view the object from different angles.

