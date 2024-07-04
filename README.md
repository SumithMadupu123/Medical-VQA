# Medical-VQA

## FUSION MODEL:

VQA involves a comparison ofthe semantic informationpresentinthe image and the question, there is a need to jointly represent the features from both modalities. This is usually accomplished through a fusion layer that allows cross-modal interaction between image and text features to generate a fused multimodal representation.
In fusion models the information from the text and image encoders are fused into a combined representation to perform the downstream task.
In this approach, we employ 'Late Fusion.' The concept behind late fusion involves fine-tuning pretrained text and image transformer models because they are easier to train.

## FUSION ARCHITECTURE:

REFER TO fusionArchitecture.png

• A text transformer (BERT) to encode the question and generate 
embeddings
• An image transformer (ViT) to encode the image and generate features
• A reasonably simple fusion layer that concatenates the textual and image 
features and passes them through a linear layer to generate an intermediate 
output



## WORKING OF MODEL:


### Input Processing

Model receives an image and corresponding question as input
• **Text Processing**: Preprocessing and tokenization of text are done using a 
pre-trained ‘BERT base-uncased’ model.
•  **Image Processing**: The image is initially divided into patches for further 
analysis by using ‘google/vit-base-patch 16-224-in21k’ model.

### Text Encoding (BERT):

• The question is processed to obtain an encoded text representation.
• **BERT Attention**: BERT attention is applied to the question, enabling the 
model to capture contextual information within the textual input.
• The output of this BERT encoder is the features (numeric values) of the 
question that we provided.

### Image Encoding (ViT)

• It divides input images into fixed-size patches, linearly embeds them, and 
utilizes a transformer encoder to capture both local and global 
dependencies.
• The attention mechanism in the Vision Transformer (ViT) is a key 
component that enables the model to focus on relevant information within 
images.
• Feed-Forward Processing: Each patch undergoes feed-forward processing, 
contributing to the overall encoding of the image.
• The output of the ViT is the features (numeric values) of the image that we 
provided

### Fusion Layer

• In this fusion layer we fuse the features of text and image.
• In this layer we use pooler output of the text encoder and image encoder.
• This layer concatenates the pooler output from the text and image encoders, 
which are then passed to a linear layer to produce an intermediate output.

### Classifier

A classifier, which is a fully connected network with output having the 
dimensions equal to that of the answer-space.
VQA is represented as a multiclass classification task in our model. Thus, cross-entropy loss becomes a natural choice for the loss function to be minimized.

### Output:

The final output is the classified answer from the answer-space, reflecting the 
model's understanding and response to the input image and question.

