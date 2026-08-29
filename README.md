# Delay Network-based Artificial Reverberators

A curated list of papers and code on delay-network-based artificial reverberation. This repository collects references and implementations for Feedback Delay Networks (FDN) and Scattering Delay Networks (SDN). It is a living resource and will be updated as new work appears.

*Made public on Friday, November 14th, 2025. Last edit to the list on August 29th, 2026.*

## Contents

- [Toolboxes and libraries](#toolboxes-and-libraries)
- [Feedback Delay Networks](#feedback-delay-networks)
    - [Machine learning optimization](#fdn-ml)
- [FDNs for Spatial Audio](#fdns-for-spatial-audio)
    - [Machine learning optimization](#dir-fdn-ml)
- [Scattering Delay Networks](#scattering-delay-networks)
    - [Machine learning optimization](#sdn-ml)
- [Early Reverbs and FDN Theory](#early-reverbs-and-fdn-theory)
- [Other resources](#other-resources)
- [Acknowledgements](#acknowledgements)
- [Contributing](#contributing)

### Legend

| Column | Meaning |
| :-- | :-- |
| **Content type** | The kind of contribution: *theory and analysis*, *informed design* (parameters set from physical/room quantities), *parameter estimation / optimization* (parameters fitted to a target), or *attenuation-filter design*. |
| **Notes** | Companion code, audio examples, practical caveats, and requirements. |

---

<a id="toolboxes-and-libraries"></a>
## 🔧 Toolboxes and libraries

| Reference | Description | Language | Repository |
| :-- | :-- | :-- | :-- |
| S. J. Schlecht. "**FDNTB: The Feedback Delay Network Toolbox.**" International Conference on Digital Audio Effects (DAFx), 2020. | Comprehensive FDN toolbox: special feedback matrices, topologies, attenuation filters, modal decomposition and examples. | Matlab | [fdnToolbox](https://github.com/SebastianJiroSchlecht/fdnToolbox) |
| G. Dal Santo, G. M. De Bortoli, K. A. Prawda, S. J. Schlecht, & V. Välimäki. "**FLAMO: An Open-Source Library for Frequency-Domain Differentiable Audio Processing.**" ICASSP, 2025. | Frequency-domain differentiable audio processing. Contains differentiable implementations of common LTI audio modules with learnable parameters. | PyTorch | [flamo](https://github.com/gdalsanto/flamo) |
| G. Dal Santo, K. A. Prawda, S. J. Schlecht, & V. Välimäki. "**FLARE: An Open-Source Library for RIR Synthesis and Analysis in PyTorch.**" AES International Conference on AI and Machine Learning for Audio, 2025. | Room impulse response synthesis and analysis in PyTorch (built on FLAMO). Contains classes for differentiable FDN and grouped FDN implementations. | PyTorch | [flare](https://github.com/gdalsanto/flare) |
| S. J. Schlecht, J. Bai, et al. "**pyFDN**", 2026 | Python library for designing, analyzing, and optimizing FDNs. | Python, PyTorch | [pyFDN](https://artificial-audio.github.io/pyFDN/index.html) |
---

<a id="feedback-delay-networks"></a>
## 📝 Feedback Delay Networks

| Reference | Content type | Main contributions | Notes |
| :-- | :-- | :-- | :-- |
| M. Chemistruck, K. Marcolini, & W. Pirkle. "**Generating matrix coefficients for feedback delay networks using genetic algorithm.**" 133rd AES Convention, 2012. | Parameter estimation | Uses a genetic algorithm to generate/optimize feedback-matrix coefficients to improve reverberation characteristics. | — |
| S. J. Schlecht & E. A. P. Habets. "**Time-varying feedback matrices in feedback delay networks and their application in artificial reverberation.**" J. Acoust. Soc. Am., 2015. | Informed design | Introduces time-varying feedback matrices to modulate pole locations, break temporal patterns, and model air movement. Shows unitary feedback-matrix modulation is guaranteed stable. | [fdnToolbox](https://github.com/SebastianJiroSchlecht/fdnToolbox/blob/5f0c29b42e3682463cd0a0a75d32149949247731/Examples/example_timeVaryingFDN.m#L4) (Matlab). Practical considerations in [this paper](https://aes2.org/publications/elibrary-page/?id=17679). |
| J. Coggin & W. Pirkle. "**Automatic design of feedback delay network reverb parameters for impulse response matching.**" 141st AES Convention, 2016. | Parameter estimation | Automatic optimization based on a genetic algorithm for analysis–synthesis matching. | — |
| S. J. Schlecht & E. A. P. Habets. "**Feedback Delay Networks: Echo Density and Mixing Time.**" IEEE/ACM TASLP, 2017. | Theory and analysis | Explains echo density and mixing time and how they depend on FDN parameters, with emphasis on delay lengths. | [fdnToolbox](https://github.com/SebastianJiroSchlecht/fdnToolbox/blob/5f0c29b42e3682463cd0a0a75d32149949247731/External/echoDensity.m#L27) (Matlab). |
| S. J. Schlecht & E. A. P. Habets. "**Accurate Reverberation Time Control in Feedback Delay Networks.**" DAFx, 2017. | Attenuation-filter design | Constrained nonlinear least-squares optimization to align attenuation filters with a target reverberation time across frequencies. Shows filter-approximation error propagates nonlinearly to T60. | [fdnToolbox](https://github.com/gdalsanto/fdnToolbox/blob/974bd97e57f8cdaf56b58946521c4a4b1185b666/graphicEQ/absorptionGEQ.m#L1) (Matlab). Requires a target RT. |
| K. Prawda, V. Välimäki, & S. J. Schlecht. "**Improved reverberation time control for feedback delay networks.**" DAFx, 2019. | Attenuation-filter design | GEQ design with an additional high-shelf filter and an optimization method based on a frequency-dependent weighting matrix that accounts for nonlinear error propagation. | Requires a target RT. |
| S. J. Schlecht & E. A. P. Habets. "**Modal Decomposition of Feedback Delay Networks.**" IEEE/ACM TASLP, 2019. | Theory and analysis | Connects the FDN's modal representation to its parameters. Presents a pole-finding algorithm. | [fdnToolbox](https://github.com/SebastianJiroSchlecht/fdnToolbox/blob/5f0c29b42e3682463cd0a0a75d32149949247731/Examples/example_dss2pr.m#L3) (Matlab). |
| J. Shen & R. Duraiswami. "**Data-driven feedback delay network construction for real-time virtual room acoustics.**" Audio Mostly, 2020. | Parameter estimation | Data-driven approach that automatically generates a pre-tuned FDN for any room described by a set of room parameters. | — |
| S. J. Schlecht & E. A. P. Habets. "**Scattering in Feedback Delay Networks.**" IEEE/ACM TASLP, 2020. | Informed design | Generalizes the feedback matrix to arbitrary lossless filter-feedback matrices to increase echo density. Introduces the "velvet" feedback matrix for very dense IRs at minimal cost. | [fdnToolbox I](https://github.com/SebastianJiroSchlecht/fdnToolbox/blob/5f0c29b42e3682463cd0a0a75d32149949247731/Examples/example_scatteringFDN.m#L4) and [II](https://github.com/SebastianJiroSchlecht/fdnToolbox/blob/5f0c29b42e3682463cd0a0a75d32149949247731/Examples/example_absorptionScatteringFDN.m#L4) (Matlab). |
| O. Das & J. S. Abel. "**Grouped feedback delay networks for modeling of coupled spaces.**" J. Audio Eng. Soc., 2021. | Informed design | Architecture where groups of delay lines share different target decay rates, used to model multi-stage decay in coupled rooms. | [GFDN](https://github.com/orchidas/GFDN) (C++ plugin). |
| I. Ibnyahya & J. D. Reiss. "**A method for matching room impulse responses with feedback delay networks.**" 153rd AES Convention, 2022. | Informed design + parameter estimation | Genetic algorithm for frequency-independent parameters, a method to extract early reflections, and informed design of the frequency-dependent filters. | [MatchReverb](https://github.com/ilias-audio/MatchReverb) (Matlab). |
| O. Das, S. J. Schlecht, & E. De Sena. "**Grouped feedback delay networks with frequency-dependent coupling.**" IEEE/ACM TASLP, 2023. | Informed design | Extends the GFDN with frequency-dependent coupling between groups; shows how paraunitary feedback matrices can emulate diffraction at the aperture connecting rooms. | [GFDN](https://github.com/orchidas/GFDN) (C++ plugin). |
| S. J. Schlecht, J. Fagerström, & V. Välimäki. "**Decorrelation in Feedback Delay Networks.**" IEEE/ACM TASLP, 2023. | Theory and analysis | Analyzes the multichannel correlation induced by FDNs; shows it depends primarily on the feedforward paths, and that filter feedback matrices improve decorrelation. | — |
| S. J. Schlecht, M. Scerbo, E. De Sena, & V. Välimäki. "**Modal Excitation in Feedback Delay Networks.**" IEEE Signal Processing Letters, vol. 31, pp. 2690–2694, 2024. | Theory and analysis | Method for computing modal shapes of an FDN of large order with a moderate number of delay lines; guides the choice of input/output points along the delay lines. | — |
| V. Välimäki, K. Prawda, & S. J. Schlecht. "**Two-Stage Attenuation Filter for Artificial Reverberation.**" IEEE Signal Processing Letters, 2024. | Attenuation-filter design | State-of-the-art design combining a first-order low-shelf pre-filter with a one-third-octave GEQ. | [Two_stage_filter](https://github.com/KPrawda/Two_stage_filter) (Matlab). Uses [Liski's GEQ](https://www.dafx17.eca.ed.ac.uk/papers/DAFx17_paper_94.pdf). |

<a id="fdn-ml"></a>
### 🤖 Machine learning optimization

| Reference | Content type | Main contributions | Notes |
| :-- | :-- | :-- | :-- |
| S. Lee, H.-S. Choi, & K. Lee. "**Differentiable artificial reverberation.**" IEEE/ACM TASLP, vol. 30, pp. 2541–2556, 2022. | Parameter estimation | Differentiable FDN and differentiable Filtered Velvet Noise, with a parameter-estimation network for analysis–synthesis and blind estimation trained end to end. | [Unofficial implementation](https://github.com/gdalsanto/diff-delay-net) (Python). First of its kind. [Audio examples](https://sh-lee97.github.io/DAR-samples/). |
| G. Dal Santo, K. Prawda, S. J. Schlecht, & V. Välimäki. "**Differentiable Feedback Delay Network for colorless reverberation.**" DAFx, 2023. | Parameter optimization | Optimizes the FDN gain parameters to reduce metallic artifacts and increase temporal density, allowing fewer channels for a smooth response. | [diff-fdn-colorless](https://github.com/gdalsanto/diff-fdn-colorless/tree/dafx23) (dafx23 branch, Python). [Audio examples](http://research.spa.aalto.fi/publications/papers/dafx23-colorless-fdn/). |
| G. Dal Santo, B. Alary, K. Prawda, S. J. Schlecht, & V. Välimäki. "**RIR2FDN: An improved room impulse response analysis and synthesis.**" DAFx, pp. 230–237, 2024. | Informed design + parameter optimization | Pipeline to design a smooth-sounding FDN matching a given RIR, with improved energy-decay estimation; evaluated with a perceptual study. | [rir2fdn](https://github.com/gdalsanto/rir2fdn) (Python + Matlab filter design). [Audio examples](http://research.spa.aalto.fi/publications/papers/dafx24-rir2fdn/). |
| A. I. Mezza, R. Giampiccolo, E. De Sena, & A. Bernardini. "**Data-driven room acoustic modeling via differentiable feedback delay networks with learnable delay lines.**" EURASIP J. Audio Speech Music Process., 2024(1), 51. | Parameter optimization | Time-domain optimization of FDN parameters, including the delay lines; introduces the echo-density-profile loss. | — |
| A. I. Mezza, R. Giampiccolo, & A. Bernardini. "**Modeling the frequency-dependent sound energy decay of acoustic environments with differentiable feedback delay networks.**" DAFx, pp. 238–245, 2024. | Parameter optimization | Extends the above to frequency-dependent FDNs with a mel-scale energy-decay-relief loss and differentiable wideband attenuation/output filters. | — |
| G. Dal Santo, K. Prawda, S. J. Schlecht, & V. Välimäki. "**Optimizing tiny colorless feedback delay networks.**" EURASIP J. Audio Speech Music Process., 2025(1), 13. | Parameter optimization | Improves the colorless-FDN work by making the optimization iFFT-free, with feedback-matrix, input- and output-gain optimization. | [diff-fdn-colorless](https://github.com/gdalsanto/diff-fdn-colorless/tree/main) (Python). [Audio examples](http://research.spa.aalto.fi/publications/papers/eurasip-colorless-fdn/). |
| I. Ibnyahya & J. D. Reiss. "**Differentiable Attenuation Filters for Feedback Delay Networks.**" DAFx, 2025. | Attenuation-filter design | Optimizes a parametric equalizer (IIR second-order sections) with parameters shared across delay lines, reducing the number of required sections. | [iir_match](https://github.com/ilias-audio/iir_match) (Python). |
| O. Das, G. Dal Santo, S. J. Schlecht, V. Välimäki, & Z. Cvetković. "**Differentiable Grouped Feedback Delay Networks for Learning Coupled Volume Acoustics.**" IEEE Trans. Audio Speech Lang. Process., vol. 34, 2026. | Parameter optimization | Differentiable GFDN trained on measured RIRs to match late-reverberation profiles of coupled-volume spaces; enables spatial interpolation and real-time parameter updates for XR. | arXiv:2508.06686. |
| P. Götz, G. Dal Santo, S. J. Schlecht, V. Välimäki, & E. A. P. Habets. "**Matching Reverberant Speech Through Learned Acoustic Embeddings and Feedback Delay Networks.**" ICASSP, 2026. | Parameter estimation | Parameter-estimation network solving the reverberant-signal-matching task with a differentiable FDN, reproducing frequency-dependent decay and direct-to-reverberation ratio. | [Audio examples](https://www.audiolabs-erlangen.de/resources/2026-ICASSP-RMS). |
| G. Dal Santo, K. Prawda, S. J. Schlecht, & V. Välimäki. "**Learning Filters in Feedback Delay Networks from Noisy Room Impulse Responses.**" Submitted to J. Audio Eng. Soc., 2026. | Attenuation-filter design | Noise-aware optimization of recursive attenuation filters when the target RIR contains background noise; guidelines for robust gradient-based tuning at low SNR. | Preprint. |

---

<a id="fdns-for-spatial-audio"></a>
## 📝 FDNs for Spatial Audio

| Reference | Content type | Main contributions | Notes |
| :-- | :-- | :-- | :-- |
| J. Anderson & S. Costello. "**Adapting artificial reverberation architectures for B-format signal processing.**" Ambisonics Symposium (Graz), 2009. | Perceptually motivated design | B-format spatial reverb: early reflections via cascaded delay stages, late reverb via a delay network and a steering gain. | Core algorithm works in A-format, requiring B-to-A conversion at the input. Many practical considerations. |
| S. J. Schlecht & E. A. P. Habets. "**Sign-Agnostic Matrix Design for Spatial Artificial Reverberation with Feedback Delay Networks.**" AES Conf. on Spatial Reproduction, 2018. | Informed design + optimization | Optimization method for finding a close unilossless, spatially-aware feedback matrix by relaxing the target-matrix phase and focusing on the sign-agnostic component. | Applications in aesthetic reverbs, coupled rooms, and SDN. [Audio examples](https://www.audiolabs-erlangen.de/resources/2018-AES-SpatialFDN) and animations. |
| B. Alary, A. Politis, S. J. Schlecht, & V. Välimäki. "**Directional feedback delay network.**" J. Audio Eng. Soc., 2019. | Informed design | Multichannel delay lines in the Ambisonics domain with directional attenuation; a directional weighting transform modifies the energy distribution over time. | — |
| B. Alary & A. Politis. "**Frequency-dependent directional feedback delay network.**" ICASSP, 2020. | Informed design | Multichannel delay lines encoded for a set of directions, with direction- and frequency-dependent attenuation. Reduces the delay-line count versus the 2019 method. | Simplifies the processing of the 2019 paper. |

<a id="dir-fdn-ml"></a>
### 🤖 Machine learning optimization

| Reference | Content type | Main contributions | Notes |
| :-- | :-- | :-- | :-- |
| R. Giampiccolo, A. I. Mezza, & A. Bernardini. "**Differentiable MIMO Feedback Delay Networks for Multichannel Room Impulse Response Modeling.**" DAFx, pp. 278–285, 2024. | Parameter optimization | Extends data-driven single-channel FDN optimization to the multiple-input–multiple-output case for spatial/space-time processing. | — |
| R. Giampiccolo, A. I. Mezza, M. Pezzoli, S. Koyama, A. Bernardini, & F. Antonacci. "**Modeling the Impulse Response of Higher-Order Microphone Arrays using Differentiable Feedback Delay Networks.**" DAFx, pp. 180–187, 2025. | Parameter optimization | Spatially-informed loss function to optimize FDNs and learn the energy distribution in space and in the time-frequency domain. | [Audio examples](https://polimi-ispl.github.io/hom-dfdn/). |

---

<a id="scattering-delay-networks"></a>
## 📝 Scattering Delay Networks

| Reference | Content type | Main contributions | Notes |
| :-- | :-- | :-- | :-- |
| E. De Sena, H. Hacıhabiboğlu, & Z. Cvetković. "**Scattering Delay Network: An Interactive Reverberator for Computer Games.**" 41st AES International Conference: Audio for Games (London), 2011. | Informed design | First presentation of the SDN: a scalable reverberator, inspired by digital waveguide meshes and FDNs, whose structure follows the geometry of the simulated room. | — |
| E. De Sena, H. Hacıhabiboğlu, Z. Cvetković, & J. O. Smith. "**Efficient synthesis of room acoustics via scattering delay networks.**" IEEE/ACM TASLP, vol. 23, no. 9, pp. 1478–1492, 2015. | Informed design | Full journal treatment: parameters derived from room geometry, first-order reflections exact. Energy decay and echo density close to the image method at one-to-two orders of magnitude lower cost. | [sdn-matlab](https://github.com/enzodesena/sdn-matlab). |
| M. Scerbo, O. Das, P. Friend, & E. De Sena. "**Higher-Order Scattering Delay Networks for Artificial Reverberation.**" DAFx, 2022. | Informed design | Improves SDN accuracy via node placement for exact higher-order reflections, redesigned scattering matrices, and pruned connections. Validated with objective metrics and a listening test. | — |
| L. Vinceslas, M. Scerbo, H. Hacıhabiboğlu, Z. Cvetković, & E. De Sena. "**Low-Complexity Higher Order Scattering Delay Networks.**" IEEE WASPAA, 2023. | Informed design | Generalized SDN that renders reflections accurately up to a chosen order, handling spherical spreading and node placement, at the cost of a standard SDN. | — |
| M. Scerbo, L. Savioja, & E. De Sena. "**Room Acoustic Rendering Networks with Control of Scattering and Early Reflections.**" IEEE/ACM TASLP, 2024. | Informed design + theory | Stability-preserving feedback-matrix design for accurate scattering control, plus arbitrary-order early reflections. Connects delay networks to Acoustic Radiance Transfer. | — |
| M. Fontana, G. Presti, D. Fantini, F. Avanzini, & A. Reyes-Lecuona. "**A Highly Parametrized Scattering Delay Network Implementation for Interactive Room Auralization.**" DAFx, pp. 286–293, 2024. | Implementation | Real-time SDN plugin with interactive geometry and absorption control, air absorption, and mono/stereo/binaural/Ambisonics output with OSC control. | [Real-time-SDN](https://github.com/LIMUNIMI/Real-time-SDN) (C++/JUCE). |

<a id="sdn-ml"></a>
### 🤖 Machine learning optimization

| Reference | Content type | Main contributions | Notes |
| :-- | :-- | :-- | :-- |
| A. I. Mezza, R. Giampiccolo, E. De Sena, & A. Bernardini. "**Differentiable Scattering Delay Networks for Artificial Reverberation.**" DAFx, 2025. | Informed design + optimization | Makes the scattering matrices and absorption filters differentiable, fitting them by gradient descent to a target RIR's energy decay and frequency-dependent reverberation times. | [differentiable-sdn](https://github.com/ilic-mezza/differentiable-sdn). |

---

<a id="early-reverbs-and-fdn-theory"></a>
## 📝 Early Reverbs and FDN Theory

| Reference | Year | Notes |
| :-- | :--: | :-- |
| M. R. Schroeder & B. F. Logan. "**Colorless artificial reverberation.**" J. Audio Eng. Soc. | 1961 | Cascade of allpass filters. |
| M. R. Schroeder. "**Natural-sounding artificial reverberation.**" J. Audio Eng. Soc. | 1962 | Parallel comb filters with series allpass filters. Known as the **Schroeder reverb**. |
| M. A. Gerzon. "**Synthetic stereo reverberation, parts I and II.**" Studio Sound. | 1971 / 1972 | Feedback delay network — multichannel allpass reverberator. |
| J. A. Moorer. "**About this reverberation business.**" Computer Music Journal. | 1979 | Lowpass filters within comb filters to model high-frequency damping; sparse FIR filter for early reflections. |
| J. Stautner & M. Puckette. "**Designing multi-channel reverberators.**" Computer Music Journal. | 1982 | "Consolidates" Gerzon's reverb. |
| J.-M. Jot & A. Chaigne. "**Digital delay networks for designing artificial reverberators.**" 90th AES Convention. | 1991 | Introduces delay-proportional attenuation filters. |
| J.-M. Jot. "**An analysis/synthesis approach to real-time artificial reverberation.**" ICASSP. | 1992 | Explains how to design attenuation and tone-corrector filters from a target RIR. |
| W. G. Gardner. "**A real-time multichannel room simulator.**" J. Acoust. Soc. Am. | 1992 | Nested allpass filters. |
| W. G. Gardner. "**The virtual acoustic room.**" Master's thesis, MIT. | 1992 | Diffuse reverberators for small/medium/large rooms based on nested allpass filters. |
| J. Dattorro. "**Effect design, part 1: Reverberator and other filters.**" J. Audio Eng. Soc. | 1997 | Tutorial-style paper with a complete design, coefficient values and practical insights. |
| D. Rocchesso & J. O. Smith. "**Circulant and elliptic feedback delay networks for artificial reverberation.**" IEEE Trans. Speech Audio Process., vol. 5, no. 1, pp. 51–63. | 1997 | Lossless FDNs can be built from any feedback matrix with unit-modulus eigenvalues and linearly independent eigenvectors. Introduces the circulant matrix for efficient implementations. Note that eq. (29) is flawed, as noted in the appendix of S. J. Schlecht's PhD thesis. |
| D. Rocchesso. "**Maximally diffusive yet efficient feedback delay networks for artificial reverberation.**" IEEE Signal Process. Lett., vol. 4, no. 9, pp. 252–255. | 1997 | Uses Galois sequences arranged in a circulant matrix to maximize echo density in the time response. |

---

<a id="other-resources"></a>
## 📚 Other resources

- "Artificial Reverberation" chapter of Miller Puckette's *Theory and Techniques of Electronic Music* — [book](https://msp.ucsd.edu/techniques/latest/book-html/node111.html) (December 2006)
- "Efficient Reverb Rendering for Auditory Scenes" by Jean-Marc Jot — [DAFx17 tutorial](https://youtu.be/C_bxtks51-A?si=x_BPDsJtgBdcPDL5)
- "Getting started with reverb design" by Sean Costello — [ValhallaDSP blog](https://valhalladsp.com/2021/09/22/getting-started-with-reverb-design-part-2-the-foundations/)
- "On reverb design" by Sean Costello — a talk on the history of artificial reverberators and how he designs a reverb algorithm — [talk](https://www.youtube.com/watch?v=aJLhqfHrwsw&t=2744s) (March 2019)
- "Designing the Make Noise Erbe-Verb — Reverb Design Lecture" by Tom Erbe — [lecture at UCSB](https://www.youtube.com/watch?v=Il_qdtQKnqk) (2019)
- "Let's Write a Reverb" by Geraint Luff — [ADC 21](https://youtu.be/6ZK2Goiyotk?si=XysVxnFTHcDsqNJV)
- "Feedback Delay Networks for Artificial Reverberation" by Sebastian J. Schlecht — [CCRMA seminars 22](https://youtu.be/gRiZX7C6zJo?si=FlxqVlEkYb_WVqQE)
- "Odd Challenges of Using Deep Learning in Designing a Feedback Delay Network Reverb" by Wojciech Kacper Werkowicz and Benjamin Whateley — [ADC 23](https://youtu.be/5URLvwFmlb0?si=3VOe2wKouemxzxCP)
- "Building Flexible Audio DDSP Pipelines: A Case Study on Artificial Reverb" by Gloria Dal Santo — [DAFx25 tutorial](https://github.com/gdalsanto/dafx25-ddsp-tutorial)
- "Modern Feedback Delay Networks for Realistic and Creative Reverberation" by Gloria Dal Santo — [ADC 25](https://www.youtube.com/watch?v=P604tjJURLc)

---

<a id="acknowledgements"></a>
## 🤝 Acknowledgements

This list is largely inspired by:

- S. J. Schlecht. "Feedback Delay Networks in Artificial Reverberation and Reverberation Enhancement." PhD thesis, 2018.
- B. Alary. "Analysis and Synthesis of Directional Reverberation." PhD thesis, Aalto University, 2021.
- V. Välimäki, J. D. Parker, L. Savioja, J. O. Smith, & J. S. Abel. "Fifty years of artificial reverberation." IEEE TASLP, 2012.

<a id="contributing"></a>
## 🫶 Contributing

Contributions are welcome! Thank you for helping keep this list up to date. The easiest flow for adding references is:

1. Fork the repository.
2. Create a branch with a descriptive name.
3. Edit `README.md` and add your reference as a new row in the appropriate table.
4. Commit your change with a short message.
5. Push your branch and open a pull request against the `main` branch.

Notes:

- Avoid promotional or non-technical entries; keep the list a factual resource.
- By contributing, you confirm you have the right to share the bibliographic information and links you provide.
- We don't want this to become a tier list. Please try to be as objective as possible.

If you have questions about the contribution format or want help making larger structural edits (e.g., converting tables to a machine-readable format), please open an issue or mention it in your PR. Thanks!
