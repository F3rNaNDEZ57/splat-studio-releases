# Splat Studio — releases

Downloads for **Splat Studio**: a Windows desktop app that turns orbital video
of an object into a 3D Gaussian splat.

Point it at a few clips filmed around an object and it runs the whole chain —
frame extraction, COLMAP structure-from-motion, 2D Gaussian Splatting training,
object isolation, export — showing progress and stopping at the two points
where a human has to look at the result and decide.

**[⬇ Download the latest release](../../releases/latest)**

> ### Research and evaluation use only
>
> Splat Studio bundles [2D Gaussian Splatting](https://github.com/hbb1/2d-gaussian-splatting)
> and `diff-surfel-rasterization`, which are licensed under the **Inria + MPII
> Gaussian-Splatting License**: non-commercial, research and evaluation use,
> with no right to sublicense. That limitation propagates to this application
> as a whole. The full licence ships inside the installer and is shown during
> setup. Commercial use requires explicit consent from Inria
> (`stip-sophia.transfert@inria.fr`).

## Requirements

| | |
|---|---|
| OS | Windows 10 / 11, 64-bit |
| GPU | **NVIDIA, Pascal (GTX 10-series) or newer**, with a current driver |
| Disk | ~9 GB free |
| Network | needed once, for the runtime setup step |

The NVIDIA **driver** is the one prerequisite the installer cannot provide — it
is kernel-mode and has to come from NVIDIA. Everything else is either bundled or
fetched by the setup step.

There is no AMD, Intel or Apple support, and none is planned: the renderer is a
CUDA extension.

## Installing

1. Run the installer. It installs per-user to
   `%LOCALAPPDATA%\Programs\SplatStudio` — no administrator prompt.
2. Leave **“Download and set up the Python runtime now”** ticked on the last
   page. This fetches ~3 GB and takes 10–20 minutes. It happens once.
   You can also run it later from **Start Menu → Splat Studio → Set up Python
   runtime**.
3. Launch Splat Studio.

The installer itself is ~285 MB. It carries the code — COLMAP, ffmpeg, 2D
Gaussian Splatting, the pipeline, a Python interpreter, and the CUDA extensions
as prebuilt wheels, so **no CUDA toolkit and no Visual Studio are needed on your
machine**. The setup step fetches the Python packages, which are mostly PyTorch;
shipping a 5 GB copy of PyTorch inside an installer is not worth the download.

### If the setup step fails

It is safe to re-run — nothing is left half-written. The usual cause is no
internet connection, or a proxy blocking `pypi.org` or `download.pytorch.org`.
The window stays open on failure so you can read the reason.

## Verifying your download

Compare the SHA-256 of the file you downloaded against the checksum published in
the release notes:

```powershell
Get-FileHash .\SplatStudio-Setup-0.2.0-x64.exe -Algorithm SHA256
```

## What this repository is

Downloads only. The source lives in a private repository; this exists so release
links can be shared without handing out repository access. There is no issue
tracker here — please report problems wherever you got the link.
