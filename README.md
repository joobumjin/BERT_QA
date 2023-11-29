# BERT_QA

Bumjin Joo 

November, 2023

Learning experience; it looks like model saving works way better in PyTorch than TensorFlow.

In terms of results, I used a pretrained HuggingFace DistilBertForQuestionAnswering model.

This model performs very well on the dataset and task. Though the model is likely overfitting, as evidenced by the very erratic training loss but still extremely good validation metrics, it seems to perform in line with expectations based upon both the provided figures in the handout as well as the fact that I am using a pretrained base.

In terms of technical implementation details, I ran out of memory every time I needed to iterate through the batches of a second data loader after having traversed through a first one (e.g. when I attempt to get validation loss in train after already having trained in the same Runtime instance). Therefore, I downloaded the weights after each trainstep and used that checkpoint for evaluation. I tried really hard to spam memory freeing everywhere, but to no avail. I also tried extra Google Cloud GPUs, but I couldn't get more than 1 so my GPU memory remained at 15GB.

I thought it would be interesting to use the general DistilBert model and apply my own classifier heads ontop of that model's outputs. However, due to time constraints from debugging the above issues, I ran out of time to do so.