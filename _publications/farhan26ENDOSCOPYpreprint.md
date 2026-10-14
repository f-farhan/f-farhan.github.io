---
layout: publication
title: "Beyond Accuracy: A Leakage-Safe and
Anatomy-Aware Evaluation of Gastrointestinal
Endoscopy Classification"
description: "Accurate brain tumor diagnosis depends on early detection, yet most publicly available magnetic resonance imaging (MRI) datasets and the deep learning models benchmarked on them are drawn from Western populations, leaving South Asian clinical settings comparatively underserved. This paper reports a systematic benchmarking study on Publicly Available MRI Dataset for Radiological Analysis and Modeling (PMRAM), a Bangladeshi brain MRI dataset, for the four-class problem of separating glioma, meningioma, pituitary tumor and tumor-free scans. We fine-tuned seven pretrained convolutional neural networks (CNN) (ResNet18, ResNet50, VGG16, VGG19, EfficientNet-B1, MobileNetV2, and DenseNet121), each under three optimizers (AdamW, Adam, and SGD) with a cosine-annealed learning rate, giving 21 CNN configurations. To probe whether global self-attention adds value on this data, we evaluated four Vision Transformer (ViT) variants (ViT-Base, ViT-Small, DeiT-Base and BEiT-Base) under the same optimizer protocol, adding 12 further configurations. The five strongest configurations were then re-assessed with Stratified 5-Fold Cross-Validation to confirm that their accuracy was not an artifact of a single fortunate split. ResNet50 with AdamW gave the best cross-validated result, 98.74% mean accuracy, narrowly ahead of the leading transformer. Taken together, the experiments show that transfer learning, paired with disciplined validation, already reaches clinically encouraging accuracy on a modest regional dataset, and they set the stage for our planned work on explainable AI (XAI) and hybrid CNN–Transformer models.High classification accuracy in gastrointestinal (GI)
endoscopy does not necessarily indicate that a model has learned
transferable pathology cues, particularly when augmentation
lineage, dataset provenance, and anatomical context are not
explicitly controlled. This study audits GastroEndoNet, a fourclass
endoscopy dataset containing gastroesophageal reflux disease
(GERD), GERD Normal, Polyp, and Polyp Normal images, from
dataset construction through representation learning. A sourcefamily-
controlled benchmark was first used to separate the effect
of clean augmentation volume from transformed-sibling leakage.
Exposing training to augmented siblings of held-out sources
increased Macro-F1 by approximately 0.126, whereas an equalsized
clean augmentation expansion improved Macro-F1 by only
about0.010. Cross-version hash analysis further showed that
all 4,004 unique primary images in version3 were already
present in version 1, with strongly class-asymmetric removals.
Under leakage-safe evaluation, anatomy was substantially easier
to decode than pathology, and disease representations transferred
poorly across anatomical branches. Explicit anatomy–
pathology factorization substantially improved cross-anatomy
transfer, yielding GERD→Polyp and Polyp→GERD Macro-F1
gains of 0.491±0.022 and 0.436±0.021, respectively, while direct
four-class Macro-F1 decreased modestly by0.018 on average.
These findings show that reliable endoscopy benchmarking
requires auditing source dependence, dataset provenance, and
representation transferability in addition to reporting aggregate
classification accuracy."
authors: Sourav Dey, Dibakar Roy, Nushrat Jahan Mim, <b>Faisal Farhan</b>, Farhan Zawad.
pdf: 
image: farhan26ENDOSCOPYpreprint.png
display: <b>Submitted for publication</b> at- 29th International Conference on Computer and Information Technology. Submission ID:#2814.
year: 2026 
# doi: 
tags: [preprint, artificial-intelligence, deep-learning, representation learning, ]

# suppmat: 
abstract: "Accurate brain tumor diagnosis depends on early detection, yet most publicly available magnetic resonance imaging (MRI) datasets and the deep learning models benchmarked on them are drawn from Western populations, leaving South Asian clinical settings comparatively underserved. This paper reports a systematic benchmarking study on Publicly Available MRI Dataset for Radiological Analysis and Modeling (PMRAM), a Bangladeshi brain MRI dataset, for the four-class problem of separating glioma, meningioma, pituitary tumor and tumor-free scans. We fine-tuned seven pretrained convolutional neural networks (CNN) (ResNet18, ResNet50, VGG16, VGG19, EfficientNet-B1, MobileNetV2, and DenseNet121), each under three optimizers (AdamW, Adam, and SGD) with a cosine-annealed learning rate, giving 21 CNN configurations. To probe whether global self-attention adds value on this data, we evaluated four Vision Transformer (ViT) variants (ViT-Base, ViT-Small, DeiT-Base and BEiT-Base) under the same optimizer protocol, adding 12 further configurations. The five strongest configurations were then re-assessed with Stratified 5-Fold Cross-Validation to confirm that their accuracy was not an artifact of a single fortunate split. ResNet50 with AdamW gave the best cross-validated result, 98.74% mean accuracy, narrowly ahead of the leading transformer. Taken together, the experiments show that transfer learning, paired with disciplined validation, already reaches clinically encouraging accuracy on a modest regional dataset, and they set the stage for our planned work on explainable AI (XAI) and hybrid CNN–Transformer models.High classification accuracy in gastrointestinal (GI)
endoscopy does not necessarily indicate that a model has learned
transferable pathology cues, particularly when augmentation
lineage, dataset provenance, and anatomical context are not
explicitly controlled. This study audits GastroEndoNet, a fourclass
endoscopy dataset containing gastroesophageal reflux disease
(GERD), GERD Normal, Polyp, and Polyp Normal images, from
dataset construction through representation learning. A sourcefamily-
controlled benchmark was first used to separate the effect
of clean augmentation volume from transformed-sibling leakage.
Exposing training to augmented siblings of held-out sources
increased Macro-F1 by approximately 0.126, whereas an equalsized
clean augmentation expansion improved Macro-F1 by only
about0.010. Cross-version hash analysis further showed that
all 4,004 unique primary images in version3 were already
present in version 1, with strongly class-asymmetric removals.
Under leakage-safe evaluation, anatomy was substantially easier
to decode than pathology, and disease representations transferred
poorly across anatomical branches. Explicit anatomy–
pathology factorization substantially improved cross-anatomy
transfer, yielding GERD→Polyp and Polyp→GERD Macro-F1
gains of 0.491±0.022 and 0.436±0.021, respectively, while direct
four-class Macro-F1 decreased modestly by0.018 on average.
These findings show that reliable endoscopy benchmarking
requires auditing source dependence, dataset provenance, and
representation transferability in addition to reporting aggregate
classification accuracy."
---
