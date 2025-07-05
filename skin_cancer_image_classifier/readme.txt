# Skin Cancer Image Classifier (CNN with PyTorch)

This project builds a convolutional neural network (CNN) to classify skin cancer images using PyTorch. It demonstrates best practices in model development, data augmentation, training pipelines, and evaluation, all centered on a real-world medical imaging task.

## Context

With a focus on healthcare AI and deep learning, this project simulates a production-grade workflow for classifying skin lesions. The dataset contains labeled images of benign and malignant cases, and the goal is to assess model performance and stability using both visual and quantitative metrics.

While the dataset is not proprietary clinical data, it represents a strong proxy for showcasing image classification techniques commonly applied in dermatology, radiology, and digital pathology.

## Technologies Used

- Python  
- PyTorch (CNNs, model training loops)  
- torchvision (ImageFolder, transforms, augmentation)  
- matplotlib and seaborn (KDE plots, visual inspection)  
- pandas and numpy (metric tracking and analysis)  
- PIL (image manipulation and loading)  
- tqdm (training progress visualization)

## What This Project Covers

- End-to-end deep learning pipeline for binary image classification  
- Data loading with ImageFolder and preview using random sampling  
- Augmentation with TrivialAugmentWide and resizing  
- Custom CNN architecture (TinyVGG) for image classification  
- Training and validation loops with accuracy and loss tracking  
- Model comparison (baseline vs augmented)  
- Prediction and visualization on external image  
- Score distribution analysis using KDE plots  
- Early preparation for deployment-friendly utilities (predict-and-plot)

## Key Takeaways

- Demonstrates how CNNs can be applied to medical image classification  
- Highlights the value of augmentation for generalization  
- Reinforces importance of visual and metric-based model evaluation  
- Shows how to test models on unseen external images for real-world inference

## Future Enhancements

- Extend to multi-class classification or segmentation tasks  
- Experiment with pretrained models (for example ResNet or EfficientNet)  
- Package as a REST API or deploy via Streamlit or Gradio  
- Introduce model explainability using Grad-CAM or SHAP  
- Add model monitoring hooks for drift detection and real-time scoring

This project showcases applied deep learning for healthcare and reflects best practices in training and evaluating medical AI models.
