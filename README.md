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




---
  
**Incremental Randomized Smoothing (IRS)**

**Summary**
+ Randomized smoothing is a scalable incomplete deterministic certification that offers statistical guarantees on neural network robustness. But it is slow, to achieve high statistical guarantees, the technique uses monte carlo smoothing which can be equated to generating few thousand isotropic gaussian noises and adding it to every image during inference to evaluate neural network robustness. If a neural network approximation such as quantization or pruning is used, this technique has to be repeated again. Instead, authors cleverly using a cache of top predicted class index, seeds for gaussian corruptions and lower confidence bound come up with a simple technique that reuses the certification guarantees for original smoothed model to certify this approximated model with very few samples.

**Contributions**
+ Can achieve 4.1x certification speedup over certification that applies randomized smoothing of approximate model from scratch.
+ In some cases, IRS besides taking less certification time to obtain same ACR, can achieve higher ACR. (If we are limited by budget).
  
**Strengths and weaknesses** (2-3 bullets for each)
+ Weaknesses
  -  When 20% network is pruned, slowdown is observed in 3 of the 9 cases and in 3 cases the improvement is marginal. Typically in most of the literature, pruning is more than 30% to notice improvement in storage performance. IRS might not be a feasible solution if network is pruned more than 50%.
  -  In the paper, authors mention they only focus on quantization and pruning as neural network approximiations. In section 5, authors mention that quantization yields smaller zeta values making IRS more effective for quantization. Paper should not have included pruning as neural network approximation
  -  Authors mentioned this, algorithm requires cache of top predicted class index, seeds for gaussian corruptions and lower confidence bound. This might grow in size if same technique were to be applied to other tasks such as object detection.
  -  Paper uses ACR as a metric. ACR can be misleading as shown in paper: ACR is a poor metric for randomized smoothing.

+ Strengths
  -  IRS can offer really good speedups for higher values of noise on quantized models.
  -  The technique can possibly be applied even on network approximations such as distilled models.
      
**My opinions**

+  Authors could have leveraged structured pruning like 2:4 to get improved performance on nvidia gpus.
+  Will this work for other forms of quantization like int4?

---


* Randomized Smoothing of All Shapes and Sizes

* Certified Adversarial Robustness via Randomized α-Smoothing for Regression Models
* Certifying confidence via randomized smoothing.
* Black-box certification with randomized smoothing: A functional optimization based framework.
* Tss: Transformation-specific smoothing for robustness certification.
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
