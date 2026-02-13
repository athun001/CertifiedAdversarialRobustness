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
+  While [IRS Paper] demonstrates significant speedups (4.1x) in certifying quantized models using ACR as a metric, [ACR Paper] argues that ACR itself may be a flawed metric, suggesting that future work should evaluate IRS using 'worst-case certified accuracy' instead.

---

# Certified Robustness Reading Plan

A curated reading list focusing on the evolution of Certified Robustness in Deep Learning, specifically emphasizing Randomized Smoothing, Generative/Diffusion-based defenses, and structured outputs. 

---

## Phase 1: Foundations & Surveys
* SoK: Certified Robustness for Deep Neural Networks
* Adversarially robust generalization requires more data
* Theoretically Principled Trade-off between Robustness and Accuracy

## Phase 2: The Randomized Smoothing Revolution
* Certified defense via randomized smoothing
* Certifying confidence via randomized smoothing
* Provably robust deep learning via adversarially trained smoothed classifiers
* Randomized Smoothing of All Shapes and Sizes
* Black-box certification with randomized smoothing: A functional optimization based framework

## Phase 3: Beyond $\ell_2$ Norms (Transformations & Patches)
* Certified Defense to Image Transformations via Randomized Smoothing
* Tss: Transformation-specific smoothing for robustness certification
* Certified Robustness Under Bounded Levenshtein Distance
* PERCEPTUAL ADVERSARIAL ROBUSTNESS: DEFENSE AGAINST UNSEEN THREAT MODELS
* Certified Patch Robustness via Smoothed Vision Transformers
* Certified Adversarial Robustness via Partition-based Randomized Smoothing

## Phase 4: Structured Outputs (Regression, Detection, Segmentation)
* Certified Robustness for Networks with Structured Outputs
* Certified Adversarial Robustness via Randomized α-Smoothing for Regression Models
* Detection as Regression: Certified Object Detection by Median Smoothing
* Reducing Certified Regression to Certified Classification for General Poisoning Attacks
* Certifiably Robust Object Detection against Patch Hiding Attacks via Patch-agnostic Masking
* DetectorGuard: Provably Securing Object Detectors against Localized Patch Hiding Attacks
* Towards Better Certified Segmentation via Diffusion Models

## Phase 5: The Diffusion Era (Denoised Smoothing)
* Deep unsupervised learning using nonequilibrium thermodynamics
* Denoising diffusion probabilistic models
* Improving denoising diffusion probabilistic models
* Elucid
