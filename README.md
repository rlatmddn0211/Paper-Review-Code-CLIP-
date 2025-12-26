# CLIP: Zero-shot Prediction & Linear Probing Implementation

This repository contains an implementation of **OpenAI's CLIP (Contrastive Language-Image Pre-training)** model to verify its capabilities in Zero-shot Prediction and Linear Probing tasks using the CIFAR-100 dataset.

The goal of this project is to understand the **multimodal alignment** between image and text features and to analyze the efficiency of **transfer learning** using a frozen backbone.

1. Zero-shot Prediction (Zero-shot_Prediction.py)
This script demonstrates the capability of CLIP to classify images without any explicit training on the CIFAR-100 dataset.

Method: Calculates cosine similarity between the image embedding and text embeddings of class labels (e.g., "a photo of a {label}").

Result: predicts the class label with the highest similarity score.

Output Example :
Top predictions:

           snake: 65.32%
          turtle: 12.45%
    sweet_pepper: 3.21%
          lizard: 1.89%
       crocodile: 0.95%
2. Linear Probing (Linear-Probe_Evaluation.py)
This script evaluates the quality of visual representations learned by CLIP.

Method: Freezes the pre-trained CLIP image encoder (ViT-B/32) and trains a simple Logistic Regression classifier on the extracted features.

Dataset: CIFAR-100 (Train/Test split)

Result: Achieves high accuracy with minimal training cost, demonstrating robust feature extraction capabilities.

Output Example:
# Training Logistic Regression...
[LibLinear]...
Accuracy = 78.31%

Key Findings (Study Notes)
Through this implementation, I verified the following:

Multimodal Alignment: CLIP successfully aligns visual and textual features in a shared embedding space, enabling effective zero-shot inference.

Representation Quality: Even without fine-tuning the backbone, the features extracted by CLIP (ViT-B/32) are highly discriminative, achieving competitive accuracy with a simple linear classifier.

Prompt Engineering: The text prompt format (e.g., "a photo of a {label}") plays a crucial role in zero-shot performance.
