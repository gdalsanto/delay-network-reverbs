# Delay Network-based Artificial Reverberators

A curated list of papers and code on delay-network-based artificial reverberation. This repository collects references and implementations for Feedback Delay Networks (FDN) and Scattering Delay Networks (SDN). It is a living resource and will be updated as new work appears.

Note: This repository has been made public on Friday, November 14th, 2025. You should expect it to grow in the following days. 

### Toolboxes and libraries
| **Reference** | **Description** |  **language** | **Repository** |
| :------------------------ | :--------------: |  :--------------: |  :--------------: | 
| S. J. Schlecht. "FDNTB: The feedback delay network toolbox." International Conference on Digital Audio Effects (DAFx), 2020. | Comprehensive FDN toolbox: special feedback matrices, topologies, attenuation filters, modal decomposition and examples. | Matlab | [fdnToolbox](https://github.com/SebastianJiroSchlecht/fdnToolbox) | 
| G. Dal Santo, G. M. De Bortoli, K. A. Prawda, S. Schlecht, & V. Välimäki. "FLAMO: An Open-Source Library for Frequency-Domain Differentiable Audio Processing." (ICASSP 2025). | Frequency-domain differentiable audio processing. Contains differentiable implementations of common LTI audio modules with learnable parameters. | PyTorch | [flamo](https://github.com/gdalsanto/flamo) | 
| G. Dal Santo, K. A. Prawda, S. Schlecht, & V. Välimäki. "FLARE: An Open-Source Library for RIR Synthesis and Analysis in PyTorch." (AES AI/ML for Audio, 2025). | Room Impulse Response synthesis and Analysis in PyTorch (based on FLAMO). Contains classes for differentiable FDN and grouped FDN implementations. | PyTorch | [flare](https://github.com/gdalsanto/flare) |

## **Feedback Delay Networks** 
| **Reference** | **Year** | **Content Type** | **Main Contributions** | **Code** | **Notes** |
| :------------------------ | :--------------: | :------------------ | :------------------ | :-------------------------------- | :-------------------------------------------------------- | 
| M. Chemistruck, K. Marcolini, & W. Pirkle. "Generating matrix coefficients for feedback delay networks using genetic algorithm." Proceedings of the 133rd Audio Engineering Society Convention. | 2012 | Parameter estimation | Uses a genetic algorithm to generate or optimize feedback matrix coefficients for FDNs to improve reverberation characteristics. | .. | .. |
| S. J. Schlecht and E. A. P. Habets. "Time-varying feedback matrices in feedback delay networks and their application in artificial reverberation." The Journal of the Acoustical Society of America. | 2015 | Informed design | Introduce time-varying feedback matrices to modulate pole locations to break temporal patterns, and model air movement | .. | Practical considerations in [this paper](https://aes2.org/publications/elibrary-page/?id=17679) | 
| J. Coggin & W. Pirkle. "Automatic design of feedback delay network reverb parameters for impulse response matching." Proceedings of the 141st Audio Engineering Society International Convention (AES). | 2016 | Parameter estimation | Proposes an automatic optimization method based on a genetic algorithm for analysis–synthesis matching. | .. | .. |
| S. J. Schlecht and E. A. P. Habets. "Feedback Delay Networks: Echo Density and Mixing Time." IEEE/ACM Transactions on Audio, Speech, and Language Processing. | 2017 | Theory and Analysis | Explains echo density and mixing time and how these depend on FDN parameters, with emphasis on delay lengths | .. | .. | 
| S. J. Schlecht and E. A. P. Habets. "Accurate Reverberation Time Control in Feedback Delay Networks." Proceedings of the International Conference on DAFx. | 2017 | Attenuation filters optimization | Constrained nonlinear least-squares optimization to align attenuation filters with a target reverberation time across frequencies | .. | Requires target RT | 
| K. Prawda, V. Välimäki, and S. Schlecht. "Improved reverberation time control for feedback delay networks." Proceedings of the International Conference on DAFx. | 2019 | Attenuation filters optimization | Presents a GEQ design that incorporates an additional high-shelf filter and an optimization method based on a frequency-dependent weighting matrix. | .. | Requires target RT |
| S. J. Schlecht and E. A. P. Habets. "Modal Decomposition of Feedback Delay Networks." IEEE/ACM Transactions on Audio, Speech, and Language Processing. | 2019 | Theory and Analysis | Discusses the connection between the FDN's modal representation and its parameters. Presents a pole finding algorithm | .. | .. | 
| J. Shen & R. Duraiswami. "Data-driven feedback delay network construction for real-time virtual room acoustics." PervasiveHealth: Pervasive Computing Technologies for Healthcare. | 2020 | Parameter estimation | Propose a data-driven approach to automatically generate a pre-tuned FDN for any given room described by a set of room parameters. | .. | .. |
| S. J. Schlecht and E. A. P. Habets. "Scattering in Feedback Delay Networks." IEEE/ACM Transactions on Audio, Speech, and Language Processing. | 2020 | Informed design | Generalizes the feedback matrix to arbitrary lossless filter-feedback matrices to increase echo density. Introduces the "velvet" feedback matrix for very dense IRs at low cost. | .. | Presents the velvet feedback matrix which can create ultra-dense impulse responses at a minimal computational cost | 
| O. Das & J. S. Abel. "Grouped feedback delay networks for modeling of coupled spaces." J. Audio Eng. Soc. | 2021 | Informed design | Architecture where groups of delay lines sharing different target decay rates. Used to model multi-stage decay | .. | .. | 
| Ibnyahya, I., & Reiss, J. D. (2022, October). A method for matching room impulse responses with feedback delay networks. In Audio Engineering Society Convention 153. | 2022 | Informed design + Parameter estimation | Uses genetic algorithm to find frequency-independent parameters. Present a method to extract early reflection. Informed design for frequency-dependent filters. | [MatchReverb](https://github.com/ilias-audio/MatchReverb) | ..  
| O. Das, S. J. Schlecht & E. De Sena. "Grouped feedback delay networks with frequency-dependent coupling." IEEE/ACM Transactions on Audio, Speech, and Language Processing. | 2023 | Informed design | Expands previous work on GFDN by introducing frequency-dependent coupling among the various FDN groups. | .. | .. | 
| S. J. Schlecht, J. Fagerström, and V. Välimäki. "Decorrelation in Feedback Delay Networks." IEEE/ACM Trans. Audio Speech Lang. Process. | 2023 | Theory and Analysis | Analysis of multichannel correlation induced by FDNs | .. | .. | 
| S. J. Schlecht, M. Scerbo, E. De Sena and V. Välimäki, "Modal Excitation in Feedback Delay Networks," in IEEE Signal Processing Letters, vol. 31, pp. 2690-2694, 2024 | 2024 | Analysis | Presents a method for computing modal shapes of an FDN having a large order and a moderate number of delay lines. | .. | ..
| V. Välimäki, K. Prawda, and S. J. Schlecht. "Two-Stage Attenuation Filter for Artificial Reverberation." IEEE Signal Processing Letters. | 2024 | Informed design of attenuation filters | SOTA design consisting of a first-order low-shelf filter and one-third-octave GEQ | - | Uses the [J. Liski's GEQ](https://www.dafx17.eca.ed.ac.uk/papers/DAFx17_paper_94.pdf)
| **Machine Learning Optimization**
| S. Lee, H. S. Choi, Lee K., "Differentiable artificial reverberation." IEEE/ACM Transactions on Audio, Speech, and Language Processing 30 (2022): 2541-2556. | 2022 | Parameter estimation | Presents a differentiable FDN, along with differentiable Filtered Velvet Noise. Introduces a parameter estimation network for analysis-synthesis and blind estimation task in an end-to-end manner. | [Unofficial implementation](https://github.com/gdalsanto/diff-delay-net) | First of its kind. Online [audio examples](https://sh-lee97.github.io/DAR-samples/) available. | 
| G. Dal Santo, K. Prawda, S. J. Schlecht, and V. Välimäki. "Differentiable Feedback Delay Network for colorless reverberation." International Conference on Digital Audio Effects (DAFx23), Copenhagen, Denmark, Sept. 4-7 2023  | 2023 | Parameter optimization | Optimize the gain parameters of the FDN to reduce metallic artifacts and increase temporal density. Using this optimization allows the redeuction of the number of channels needed for a smooth response. | [diff-fdn-colorless](https://github.com/gdalsanto/diff-fdn-colorless/tree/dafx23) dafx23 branch | Online [audio examples](http://research.spa.aalto.fi/publications/papers/dafx23-colorless-fdn/) available. |
| Dal Santo, G., Alary, B., Prawda, K., Schlecht, S., & Välimäki, V. (2024, September). RIR2FDN: An improved room impulse response analysis and synthesis. In International Conference on Digital Audio Effects (pp. 230-237). University of Surrey. | 2024 | Informed design + Parameter optimization | Present a pipeline to design a smooth-sounding FDN to match a given RIR. Evaluates the results with a perceptual study. | [rir2fdn](https://github.com/gdalsanto/rir2fdn) | Online [audio examples](http://research.spa.aalto.fi/publications/papers/dafx24-rir2fdn/) available. Now this approach |  
| Mezza, A. I., Giampiccolo, R., De Sena, E., & Bernardini, A. Data-driven room acoustic modeling via differentiable feedback delay networks with learnable delay lines. EURASIP Journal on Audio, Speech, and Music Processing, 2024(1), 51. | 2024 | Parameter optimization | Presents a method for optimizing FDN parameters based on the lumped-element model. Introduces the echo density profile loss to optimize delay lines along with the other FDN parameters. | .. | .. |
| Mezza, A. I., Giampiccolo, R., & Bernardini, A. (2024). Modeling the frequency-dependent sound energy decay of acoustic environments with differentiable feedback delay networks. In Proceedings of the 27th International Conference on Digital Audio Effects (DAFx24) (pp. 238-245). | 2024 | Parameter optimization | Extends the author's previous work to frequency-dependent FDNs. | .. | .. |
| Dal Santo, G., Prawda, K., Schlecht, S. J., and Välimäki, V. "Optimizing tiny colorless feedback delay networks," EURASIP Journal on Audio, Speech, and Music Processing, 2025(1), 13. | 2025 | Parameter optimization | Improved the previous colorless FDN work by making the optimization iFFT-free. | [diff-fdn-colorless](https://github.com/gdalsanto/diff-fdn-colorless/tree/main) | Online [audio examples](http://research.spa.aalto.fi/publications/papers/eurasip-colorless-fdn/) available | (GitHub) 
| I. Ibnyahya, and J. Reiss. "Differentiable Attenuation Filters for Feedback Delay Networks." 28th International Conference on Digital Audio Effects (DAFx25), 2025. | 2025 | Attenuation filters optimization | Optimization of a parameteric equilizer to reduce the number of required second-order sections. | [irr_match](https://github.com/ilias-audio/iir_match) | ..
| Götz, P., Santo, G. D., Schlecht, S. J., Välimäki, V., & Habets, E. A. (2025). Matching Reverberant Speech Through Learned Acoustic Embeddings and Feedback Delay Networks. arXiv preprint arXiv:2510.23158. | Under review | Parameter estimation | Present a parameter estimation network to solve the reverberant signal matching task with a differentiable FDN. | .. | Online [audio examples](https://www.audiolabs-erlangen.de/resources/2026-ICASSP-RMS) available  

### **FDNs for Spatial Audio**
| **Reference** | **Year** | **Content Type** | **Main Contributions** | **Code** | **Notes** |
| :------------------------ | :--------------: | :------------------ | :------------------ | :-------------------------------- | :-------------------------------------------------------- | 
| J. Anderson and S. Costello. "Adapting artificial reverberation architectures for B‑format signal processing." Proc. Ambisonics Symposium (Graz, Austria). | 2009 | .. | .. | .. | .. | 
| S. J. Schlecht and E. A. P. Habets. "Sign-Agnostic Matrix Design for Spatial Artificial Reverberation with Feedback Delay Networks." | 2018 | .. | .. | .. | .. | 
| B. Alary, A. Politis, S. J. Schlecht & V. Välimäki. "Directional feedback delay network." AES: Journal of the Audio Engineering Society. | 2019 | .. | .. | .. | .. | 
| B. Alary, & A. Politis, "Frequency-dependent Directional feedback delay network." In: IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP). | 2020 | .. | .. | .. | .. |
| **Machine Learning Optimization** 
| Giampiccolo, R., Mezza, A. I., & Bernardini, A. "Differentiable MIMO Feedback Delay Networks for Multichannel Room Impulse Response Modeling," In Proceedings of the 27th International Conference on Digital Audio Effects (DAFx24) (pp. 278-285). | 2024 | .. | .. | .. | .. | 
| Giampiccolo, R., Mezza, A. I., Pezzoli, M., Koyama, S., Bernardini, A., & Antonacci, F., "Modeling the Impulse Response of Higher-Order Microphone Arrays using Differentiable Feedback Delay Networks", In Proceedings of the International Conference on Digital Audio Effects (DAFx25) (pp. 180-187). | 2025 | .. | .. | .. | .. | 
| Scerbo, M., Schlecht, S. J., Ali, R., Savioja, L., & De Sena, E., "Efficient Multichannel Auralization Based on the Modal Decomposition of Acoustic Radiance Transfer (MoD-ART)," in IEEE Transactions on Audio, Speech, and Language Processing. | 2025 | .. | .. | .. | .. | 
| .. | .. | .. | .. | .. | .. | 

## Scattering Delay Networks
| **Reference** | **Year** | **Parameter Design** | **Application** | **Code** | **Notes** |
| :------------------------ | :--------------: | :------------------ | :------------------ | :-------------------------------- | :-------------------------------------------------------- | 
| E. De Sena, H. Hacıhabiboğlu, Z. Cvetković & J. O. Smith. "Efficient synthesis of room acoustics via scattering delay networks." IEEE/ACM Transactions on Audio, Speech, and Language Processing. | 2015 | Informed | .. | .. | .. | 
| M. Scerbo, O. Das, P. Friend & E. De Sena. "Higher-Order Scattering Delay Networks for Artificial Reverberation." 25th International Conference on Digital Audio Effects (DAFx). | .. | .. | .. | .. | .. | 
| L. Vinceslas, M. Scerbo, H. Hacıhabiboğlu, Z. Cvetković & E. De Sena. "Low-Complexity Higher Order Scattering Delay Networks." IEEE Workshop on Applications of Signal Processing to Audio and Acoustics (WASPAA). | .. | .. | .. | .. | .. | 
| .. | .. | .. | .. | .. | .. | 
| .. | .. | .. | .. | .. | .. | 
| **Machine Learning Optimization**
| Mezza, A. I., Riccardo G., and Alberto B., "Differentiable Scattering Delay Networks for Artificial Reverberation." Proceedings of the International Conference on Digital Audio Effects (DAFx25). 2025. | 2025 | .. | .. |
| .. | .. | .. | .. | .. | .. | 

## Early Reverbs
| **Reference** | **Year** | **Notes** |
| :------------------------ | :--------------: |  :-------------- | 
| M. R. Schroeder and B. F. Logan. "Colorless artificial reverberation." J. Audio Eng. Soc. | 1961 | Cascade of allpass filters |
| M. R. Schroeder. "Natural-sounding artificial reverberation." Journal of the Audio Engineering Society. | 1962 | Combination of parallel comb filters with series allpass filtes. Known as the **Schroeder reverb** |
| M. A. Gerzon. "Synthetic stereo reverberation, parts I and II." Studio Sound. | 1971(I), 1972(II) | Feedback delay network - multichannel allpass reverberator | 
| J. A. Moorer. "About this reverberation business." Computer Music Journal. | 1979 | Introduces lowpass filters within comb filters to model high frequency damping. Uses a sparse FIR filter to model early reflections | 
| J. Stautner and M. Puckette. "Designing Multi-Channel Reverberators." Computer Music Journal. | 1982 | "Consolidates" Gerzon's reverb | 
| W. G. Gardner. "A real-time multichannel room simulator." J. Acoustical Society of America. | 1992 | Nested allpass filters |
| W. G. Gardner. "The virtual acoustic room." Master's thesis, MIT. | 1992 | Diffuse reverberators for small/medium/large rooms, based on nested allpass filters |
| J.-M. Jot and A. Chaigne. "Digital delay networks for designing artificial reverberators." Proc. 90th Conv. Audio Eng. Soc. |1991 | Introduces the concept of delay-proportionalattenuation filters |
| J.-M. Jot. "An Analysis/synthesis approach to real-time artificial reverberation." Proc. ICASSP. | 1992 | Explains how to design attenuation and tone corrector filters from a target RIR |
| J. Dattorro. "Effect design, part 1: Reverberator and other filters." J. Audio Engineering Society. | 1997 | Tutorial-like paper with complete design, coefficient values and practical insights |
| .. | .. | .. |


### Other resources

- "Efficient Reverb Rendering for Auditory Scenes" by Jean Marc Jot [DAFx17 Tutorial](https://youtu.be/C_bxtks51-A?si=x_BPDsJtgBdcPDL5)
- Sean Costello's "Getting started with reverb design" [ValhallaDSP blog](https://valhalladsp.com/2021/09/22/getting-started-with-reverb-design-part-2-the-foundations/). 
- "Let's Write a Reverb" by Geraint Luff  [ADC 21](https://youtu.be/6ZK2Goiyotk?si=XysVxnFTHcDsqNJV)
- "Feedback Delay Networks for Artificial Reverberation" by Sebastian J. Schlecht [CCRMA seminars 22](https://youtu.be/gRiZX7C6zJo?si=FlxqVlEkYb_WVqQE)
- "Odd Challenges of Using Deep Learning in Designing a Feedback Delay Network Reverb" by Wojciech Kacper Werkowicz and Benjamin Whateley [ADC 23](https://youtu.be/5URLvwFmlb0?si=3VOe2wKouemxzxCP)
- "Building Flexible Audio DDSP Pipelines: A Case Study on Artificial Reverb" by Gloria Dal Santo [DAFx25 Tutorial](https://github.com/gdalsanto/dafx25-ddsp-tutorial)


### Acknowledgements

This list is largely inspired by:

- S. J. Schlecht. "Feedback Delay Networks in Artificial Reverberation and Reverberation Enhancement" (PhD thesis, 2018).
- B. Alary. "Analysis and Synthesis of Directional Reverberation" (PhD thesis, Aalto University, 2021).
- V. Välimäki, J. D. Parker, L. Savioja, J. O. Smith, & J. S. Abel. "Fifty years of artificial reverberation" (IEEE TASLP, 2012).

## Contributing

Contributions are welcome! Thank you for helping keep this list up to date. The easiest flow for adding references is:

1. Fork the repository.
2. Create a branch with a descriptive name.
3. Edit `README.md` and add your reference as a new row in the appropriate table.
4. Commit your change with a short message.
5. Push your branch and open a pull request against the `main` branch. 

Notes:

- Avoid promotionalor non-technical text in entries; keep the list a factual resource.
- By contributing, you confirm you have the right to share the bibliographic information and links you provide. 
- We don't want this to become a tier list. Please try to be as objective as possible. 

If you have questions about contribution format or want help making larger structural edits (e.g., converting tables to a machine-readable format), please open an issue or mention it in your PR. Thanks!
