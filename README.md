# Medical-VQA

FUSION MODEL:
VQA involves a comparison of the semantic information present in the image and 
the question, there is a need to jointly represent the features from both modalities. 
This is usually accomplished through a fusion layer that allows cross-modal 
interaction between image and text features to generate a fused multimodal 
representation.
In fusion models the information from the text and image encoders are fused into 
a combined representation to perform the downstream task.
In this approach, we employ 'Late Fusion.' The concept behind late fusion 
involves fine-tuning pretrained text and image transformer models because they 
are easier to train.
FUSION ARCHITECTURE:
