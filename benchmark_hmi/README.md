# AstroDenoise-HMI-LOS

SDO/HMI line-of-sight (LOS) magnetograms for zero-shot astronomical image denoising.

## Purpose

Long-baseline, fixed-cadence real solar magnetograms for testing denoising on disk-scale structure and active regions. Valid pixels are finite values: `np.isfinite(image)` (off-limb is NaN).

## Collection

- **Product**: `hmi.M_720s` (LOS magnetogram)
- **Source**: http://jsoc.stanford.edu/
- **Sampling**: 2015-06-01 → 2026-10-05, one frame every 2 days, **2073** images
- **Processing**: center-crop + resize to 512×512, `float32` `.npy`

```text
raw_fits/yYYYYmMM/*.fits
images/yYYYYmMM/*.npy
png/yYYYYmMM/*.png
```

## Citation

```bibtex
@article{scherrer2012hmi,
  author  = {Scherrer, P. H. and Schou, J. and Bush, R. I. and others},
  title   = {The Helioseismic and Magnetic Imager ({HMI}) Investigation
             for the {Solar Dynamics Observatory} ({SDO})},
  journal = {Solar Physics},
  year    = {2012},
  volume  = {275},
  pages   = {207--227},
  doi     = {10.1007/s11207-011-9834-2}
}

@article{pesnell2012sdo,
  author  = {Pesnell, W. Dean and Thompson, B. J. and Chamberlin, P. C.},
  title   = {The {Solar Dynamics Observatory} ({SDO})},
  journal = {Solar Physics},
  year    = {2012},
  volume  = {275},
  pages   = {3--15},
  doi     = {10.1007/s11207-011-9841-3}
}
```
