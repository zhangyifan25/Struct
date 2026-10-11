# HMI2073 & HST1042

Public benchmark data for **zero-shot astronomical image denoising**, covering two typical regimes: solar magnetograms and deep-field imaging. All samples are provided as 512×512 arrays for direct algorithm use.

This repository redistributes **processed files only**. The original observations belong to the respective instrument teams and archives; please cite the papers below when using the data.

---

## Purpose

Astronomical images rarely come with clean references, which limits supervised denoising. These sets are meant for:

- evaluating zero-shot / unpaired denoising on **real observations**;
- covering two scenes:
  - **HMI2073** (solar LOS magnetograms): disk-scale structure and active regions;
  - **HST1042** (Hubble XDF patches): very faint background with numerous weak galaxies and point sources.

Use `images/*.npy` as the formal input. `png/` is for browsing only; `raw_fits/` keeps the matching source FITS for provenance.

| Dataset | Samples | Formal data |
|---------|---------|-------------|
| `HMI2073/` | 2073 | `images/*.npy` |
| `HST1042/` | 1042 | `images/*.npy` |

Folder meaning: `raw_fits/` original FITS; `images/` 512×512 `.npy`; `png/` grayscale previews aligned with `images/`.

---

## Collection and processing

### 1. HMI2073 (solar LOS magnetograms)

1. Product: SDO/HMI series **`hmi.M_720s`** (LOS magnetogram, not continuum).
2. Source: Stanford **JSOC** — http://jsoc.stanford.edu/
3. Sampling: from **2015-06-01** to **2026-10-05**, **one frame every 2 days** on a global time grid (prefer a complete FITS near 00:00 TAI), **2073** frames; off-grid and duplicate files removed.
4. Processing: center-crop to square, nearest-neighbor resize to **512×512**, save as `float32` `.npy`. Off-limb / invalid pixels are NaN; use `np.isfinite(img)` as the valid region.

### 2. HST1042 (Hubble eXtreme Deep Field)

1. Product: XDF HLSP science mosaics (`*_sci.fits`), **14** files (ACS/WFC 30mas×5, ACS/WFC 60mas×5, WFC3/IR 60mas×4).
2. Source: STScI **MAST** — https://archive.stsci.edu/prepds/xdf/
3. Patching: **512×512**, **stride 512 (no overlap)**; simple valid-fraction / variance filtering yields **1042** patches:
   - `A_acs30mas`: 736  
   - `B_acs60mas`: 170  
   - `C_wfc3ir`: 136  
4. Processing: each patch saved as `float32` `.npy` with a matching `.png` preview.

---

## Download

Large binaries are **not** stored in the git tree. Get the processed datasets from [Releases](https://github.com/zhangyifan25/Struct/releases):

| Asset | Contents |
|-------|----------|
| `HMI2073.tar.gz` | HMI2073 `images/` + `png/` + README (~1.1 GB) |
| `HST1042.tar.gz` | HST1042 `images/` + `png/` + README (~1.2 GB) |

```bash
tar -xzf HMI2073.tar.gz
tar -xzf HST1042.tar.gz
```

Source FITS (`raw_fits/`) are omitted from the release due to size; regenerate from the linked archives if needed. Code will be added after paper acceptance.

## Citation

Please cite the original data papers (and your own method paper) when using these sets:

```bibtex
@article{scherrer2012hmi,
  author  = {Scherrer, P. H. and Schou, J. and Bush, R. I. and Kosovichev, A. G.
             and Bogart, R. S. and Hoeksema, J. T. and Liu, Y. and Duvall, T. L., Jr.
             and Zhao, J. and Title, A. M. and Schrijver, C. J. and Tarbell, T. D.
             and Tomczyk, S.},
  title   = {The Helioseismic and Magnetic Imager ({HMI}) Investigation
             for the {Solar Dynamics Observatory} ({SDO})},
  journal = {Solar Physics},
  year    = {2012},
  volume  = {275},
  number  = {1--2},
  pages   = {207--227},
  doi     = {10.1007/s11207-011-9834-2}
}

@article{pesnell2012sdo,
  author  = {Pesnell, W. Dean and Thompson, B. J. and Chamberlin, P. C.},
  title   = {The {Solar Dynamics Observatory} ({SDO})},
  journal = {Solar Physics},
  year    = {2012},
  volume  = {275},
  number  = {1--2},
  pages   = {3--15},
  doi     = {10.1007/s11207-011-9841-3}
}

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

See also [`HMI2073/README.md`](HMI2073/README.md) and [`HST1042/README.md`](HST1042/README.md).
