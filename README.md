# Coastal Resilience Challenge

## Overview

This project was developed for the **Coastal Resilience Challenge** organized by EY. The objective was to create a model capable of identifying and classifying different types of buildings in altered images. The approach was centered on a divide-and-conquer strategy, utilizing a two-stage model with intermediate image processing to enhance prediction accuracy.

## Methodology

### Model 1: Area Identification

The first model focuses on identifying residential and commercial zones within the images. Instead of concentrating on individual buildings, the model analyzes clusters of buildings and their surroundings. The process is subdivided into three geographical categories:
- **Countryside**
- **Suburbs**
- **City**

These categories are determined based on the proportion of green or brown pixels in the image. The model is further divided into six sub-models to manage the complexity and enhance the accuracy of predictions.

### Model 2: Building Classification

The second model takes the altered images produced by Model 1 and classifies the buildings within the identified zones into four types. This model operates on images that have been pre-labeled and altered according to the zones detected by Model 1.

### Image Alteration for Communication

To ensure effective communication between Model 1 and Model 2, the images are altered using an intermediate code. This code changes the hue of regions within the image based on their classification as either residential or commercial zones.

![Image Alteration](link_to_image) 
*Figure 1: Example of an image after alteration by Model 1.*

## Limitations and Future Perspectives

Despite the promising approach, there are several limitations and areas for improvement:
- **Data Labeling:** The model's performance is limited by the small number of labeled images (around 80). Increasing the dataset size could significantly improve results.
- **Image Processing:** The hue alteration technique results in the loss of chrominance information. A better approach could involve using RGBA images and conveying zone information via the alpha channel. This would require modifying the YOLO architecture to accommodate the additional channel.
- **Alternate Architectures:** Experimentation with U-Net architectures with four channels did not yield satisfactory results, but further refinement could be beneficial.
- **Image Enhancement:** Techniques like the Hough transform could be used to enhance building contours, improving detection accuracy.
- **Data Augmentation:** Using Generative Adversarial Networks (GANs) could help generate more training data, enhancing the model's robustness.

## Results

The model was designed to perform well with limited training data, focusing on suburban areas. Although the small dataset was a significant constraint, the model managed to function, achieving a Mean Average Precision (MAP) of 0.23 on the test data.

![Test Image Identification](link_to_image)
*Figure 2: Example of building identification on a test image.*
