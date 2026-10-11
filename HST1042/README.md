# HST1042

Hubble eXtreme Deep Field (XDF) patches for zero-shot astronomical image denoising (**1042** patches).

## Purpose

Very deep, low-SNR real deep-space patches for testing denoising while preserving faint galaxies and point sources.

## Collection

- **Product**: XDF HLSP, all **14** `*_sci.fits` (ACS 30mas / ACS 60mas / WFC3-IR)
- **Source**: https://archive.stsci.edu/prepds/xdf/
- **Patching**: 512×512, stride 512 (no overlap), **1042** patches  
  - `A_acs30mas`: 736 · `B_acs60mas`: 170 · `C_wfc3ir`: 136
- **Processing**: `float32` `.npy` plus matching `.png`

```text
raw_fits/*.fits
images/{A_acs30mas,B_acs60mas,C_wfc3ir}/<tag>/*.npy
png/   # same tree as images/
```

## Citation

```bibtex
@article{illingworth2013xdf,
  author  = {Illingworth, G. D. and Magee, D. and Oesch, P. A. and Bouwens, R. J.
             and Labb{\'e}, I. and Stiavelli, M. and van Dokkum, P. G. and Franx, M.
             and Trenti, M. and Carollo, C. M. and Gonzalez, V.},
  title   = {The {HST} e{X}treme {D}eep {F}ield ({XDF}): Combining All {ACS}
             and {WFC3}/{IR} Data on the {HUDF} Region into the Deepest Field Ever},
  journal = {The Astrophysical Journal Supplement Series},
  year    = {2013},
  volume  = {209},
  number  = {1},
  pages   = {6},
  doi     = {10.1088/0067-0049/209/1/6}
}
```
