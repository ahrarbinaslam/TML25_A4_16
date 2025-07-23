# TML25_A4_16

# Explainability (TML Assignment 4 – Team 16)

This repository contains the implementation for Assignment 4 of the TML25 course. The main objective is to explore and compare multiple explainability techniques such as **Network Dissection**, **Grad-CAM**, and **LIME** on a pretrained ResNet-50 using ImageNet images. The assignment is divided into four tasks doing in a comparative evaluation of the different methods.

---

## Objective

To gain a deeper understanding of model interpretability by generating and analyzing visual explanations for predictions made by convolutional neural networks (CNNs). The goal is to evaluate the overlap, efficiency, and distinctiveness of different explainability techniques.

---

## Team Members

## Ahrar Bin Aslam
## Muhammad Mubeen Siddiqui


---

## Task 1: Network Dissection

We applied Network Dissection to analyze which interpretable concepts are captured by the internal units of a pretrained ResNet-50. Using activation maps and a concept-annotated dataset, we identified neurons linked to visual features offering a semantic understanding of the network's learned representations.

---

## Task 2: Grad-CAM

In this task, we used Grad-CAM to generate heatmaps that highlight the most important regions for the network’s predictions. The method computes the gradients of the target class with respect to feature maps of the final convolutional layer. The resulting activation maps were saved and later thresholded to binary masks for comparison in Task 4.

---

## Task 3: LIME

Using LIME (Local Interpretable Model-agnostic Explanations), we generated local surrogate models by perturbing input superpixels and observing changes in predictions. A Quickshift segmentation was used, and a Ridge regressor fitted the perturbed predictions. The top 10 superpixels influencing the top-1 class prediction were retained for each image.

**Task 3 Results:**
- Average LIME Computation Time: `3.36 seconds`
- IoU on LIME: `0.3206986647682452`
- LIME provided high-resolution, interpretable masks focused on object details.

---

## Task 4: IoU Comparison – LIME vs Grad-CAM

We compared the binary masks from LIME and Grad-CAM using the Intersection over Union (IoU) metric to evaluate how much both methods agree in localizing relevant regions.

### Methodology:
- Grad-CAM masks were obtained by thresholding the top 20% of intensity values.
- LIME masks were resized and thresholded using binary segmentation.
- IoU was computed per image and averaged over all samples.

### Results:

| Image                        | IoU Score |
|-----------------------------|-----------|
| West_Highland_white_terrier | 0.1025    |
| American_coot               | 0.1692    |
| racer                       | 0.1343    |
| flamingo                    | 0.1007    |
| kite                        | 0.1391    |
| goldfish                    | 0.0924    |
| tiger_shark                 | 0.1971    |
| vulture                     | 0.0790    |
| common_iguana               | 0.1101    |
| orange                      | 0.0739    |
| **Average IoU (Team16)**    | **0.1198** |

---

## Discussion & Insights

The observed average IoU of 0.1198 indicates that LIME and Grad-CAM highlight different regions, with only partial overlap. This aligns with their core design differences—Grad-CAM captures class-level spatial importance, whereas LIME focuses on interpretable, local perturbation-driven features.

We noticed that:
- Simple objects like `tiger_shark` and `American_coot` had higher IoUs, implying better agreement.
- More complex images like `orange` and `vulture` showed lower overlap, likely due to clutter or less discriminative boundaries.

---

## Conclusion

This assignment provided valuable experience in applying and comparing three major explainability methods. We gained practical insights into how convolutional networks make decisions, how different techniques interpret those decisions, and how to critically analyze their alignment.

---
