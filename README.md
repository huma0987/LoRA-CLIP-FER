LoRA-Enhanced CLIP for Cross-Dataset Facial Emotion Recognition
Overview

This project explores Facial Emotion Recognition (FER) using a parameter-efficient adaptation of the CLIP ViT-B/32 vision transformer enhanced with LoRA (Low-Rank Adaptation). The model is trained on RAF-DB and evaluated on SFEW and FER+ to analyze cross-dataset generalization under domain shift, perceptual ambiguity, and noisy emotion labels.

Key Contributions

Fine-tuned a vision-language foundation model (CLIP) for FER
Integrated LoRA adapters into attention layers for lightweight optimization
Demonstrated cross-dataset semantic generalization
Achieved competitive accuracy with < 2% trainable parameters
Conducted a multi-domain qualitative and quantitative evaluation

Problem Statement

Traditional CNN-based FER systems perform well on curated datasets but fail to generalize to real-world images due to noise, occlusion, emotional ambiguity, and annotation inconsistency. This project investigates whether LoRA-enhanced CLIP can preserve emotional semantics across datasets without full model retraining.

Research Hypothesis

LoRA-enhanced CLIP can achieve better cross-dataset generalization than conventional FER architectures by preserving pretrained semantic priors while updating only a small subset of parameters.

Architecture

Input Image → Frozen CLIP ViT-B/32 + LoRA → Image Embedding → Linear Head → Emotion Prediction

Only LoRA weights and the classification head are trained, keeping the backbone frozen

Datasets
Dataset	         Purpose		Domain Characteristics
RAF-DB	         Training	        Curated, expert-labeled facial images
SFEW 2.0	       Cross-dataset test	Wild, movie frames with pose/lighting variations
FER+	           Noisy label test	    Crowd-sourced emotional annotations, perceptual ambiguity


Results Summary
Dataset		Accuracy	Macro-F1	      Notes
RAF-DB		83.31%		59.78           Strong source-domain learning
SFEW		44.78%		33.66           Partial generalization under domain shift
FER+		56.88%	        21.17	        Confusion due to noisy emotional distribution


Qualitative Predictions

The model maintains emotional priors on SFEW but collapses toward neutral predictions on FER+ due to perceptual label ambiguity.






