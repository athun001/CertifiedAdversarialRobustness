# Certified Adversarial Robustness

  
**Average Certified Radius is a Poor Metric for Randomized Smoothing**

**Summary**
+ Authors discourage the use of Average Certified Radius (ACR) to certify robustness of neural networks by claiming that improvement on easy examples contributes more to the metric than hard examples, reduce accuracy on hard inputs. By discarding hard data during training, data reweighting with certified radius and incorporating PGD attack, authors are able to achieve SOTA ACR thereby highlighting the need of a different metric. 

**Contributions**
+ Authors are able to increase ACR by showing that improvement on easy samples could contribute more than 1000 times to ACR than same magnitude of improvement on hard samples.
+ They showed empirically as well as theorectically why ACR is a bad metric. First such work to highlight this.
+ They explained why it is better to report highest achieveable certified accuracy at specified radii.
  
**Strengths and weaknesses** (2-3 bullets for each)
+ Weaknesses
  -  Since Authors compared results with MACER paper, Table 2 should have added the gradient norm ratio for MACER.
  -  Existing papers which authors mention use other metrics than ACR to report their results. Authors could have incorporated these metrics when comparing results.

+ Strengths
  -  Using the Adaptive (PGD) attack on sphere should give better empirical robustness as compared to SOTA randomized smoothing based techniques such as SmoothAdv, Consistency, SmoothMix or CAT-RS.
  -  Technique successfully increases the ACR with small modifications to original Cohen paper.
      
**My opinions**

+  Can using PGD as part of SmoothAdv, Consistency, SmoothMix or CAT-RS help increase ACR?
+  Can incorporating PGD in Detection as Regression paper help improve the metrics?


* Randomized Smoothing of All Shapes and Sizes
* Incremental Randomized Smoothing (IRS) https://arxiv.org/abs/2305.19521 
* Certified Adversarial Robustness via Randomized α-Smoothing for Regression Models
* Input-Specific Robustness Certification for Randomized Smoothing
* Higher-Order Certification for Randomized Smoothing
* Certified Robustness for Networks with Structured Outputs
* Provable defenses adversarial polytype
* DetectorGuard: Provably Securing Object Detectors against Localized Patch Hiding Attacks
* Certified defense via randomized smoothing
* Certifiably Robust Object Detection against Patch Hiding Attacks via Patch-agnostic Masking
* Detection as Regression: Certified Object Detection by Median Smoothing.
* Certified Defense to Image Transformations via Randomized Smoothing
* certified defenses against adversarial examples
* certified adversarial robustness for free
* SoK: Certified Robustness for Deep Neural Networks
* Certified Training: Small Boxes are All You Need
* Certified Robustness Under Bounded Levenshtein Distance
* On Using Certified Training towards Empirical Robustness
* Certified Adversarial Robustness via Partition-based Randomized Smoothing
* Adaptive Randomized Smoothing: Certified Adversarial Robustness for Multi-Step Defences
* Certified Robustness via Dynamic Margin Maximization and Improved Lipschitz Regularization
* Projected Randomized Smoothing for Certified Adversarial Robustness
* Towards Better Certified Segmentation via Diffusion Models
* Raising the Bar for Certified Adversarial Robustness with Diffusion Models
* Certified Adversarial Robustness Within Multiple Perturbation Bounds
* Certified Robustness to Adversarial Examples with Differential Privacy
* Towards Fast Computation of Certified Robustness for ReLU Networks
* Theoretically Principled Trade-off between Robustness and Accuracy
* Efficient Neural Network Robustness Certification with General Activation Functions
* Accelerating Certified Robustness Training via Knowledge Transfer.
* Rethinking Lipschitz Neural Networks and Certified Robustness: A Boolean Function Perspective
* Certified Patch Robustness via Smoothed Vision Transformers
* Provably robust deep learning via adversarially trained smoothed classifiers
* on the effectiveness of interval bound propagation for training verifiably robust models.
* Adaptive Diffusion Denoised Smoothing : Certified Robustness via Randomized Smoothing with Differentially Private Guided Denoising Diffusion
* Deep unsupervised learning using nonequilibrium thermodynamics
* Denoising diffusion probabilistic models
* Improving denoising diffusion probabilistic models
* Diffusion models for adversarial purification.
* Reducing Certified Regression to Certified Classification for General Poisoning Attacks
* Denoised smoothing: a provable defense for pretrained classifiers
* Adversarially robust generalization requires more data
* PERCEPTUAL ADVERSARIAL ROBUSTNESS: DEFENSE AGAINST UNSEEN THREAT MODELS
* Elucidating the design space of diffusion based generative models
