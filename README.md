# AnyStyle Lite — MLinPL 2026

This is a reduced fork of [AnyStyle](https://github.com/joaxkal/AnyStyle) for the MLinPL 2026 tutorial **“Build Your Own 3D Scene: An Introduction to Gaussian Splatting.”** It keeps image/video-frame stylization inference with the *simple-injection* checkpoint, Gaussian rendering and PLY export. Training, evaluation, post-optimization, extra LongCLIP variants and large example assets have been removed. `assets/example-starry_night.jpg` remains for the optional image-style exercise.

Use this fork as `modules/AnyStyle` in the [workshop repository](https://github.com/MikolajZielinski/MLinPL-2026). The notebook invokes `inference_style.py` directly from this directory and adds it to `sys.path`; **do not install the original AnyStyle `pyproject.toml`**, which pins a different Torch stack. The parent workshop's `environment.yml` and setup instructions define the compatible Python 3.10 / PyTorch 2.1.2 / CUDA 11.8 runtime.

Required model files live in the parent workshop's `models/` directory, **not in this Git repository**:

- `anystyle_simple.ckpt` — the released `simple` checkpoint. The `aggregator` checkpoint is not used by this notebook.
- `longclip-B-32.pt` — LongCLIP-B-32 weights for the text/image style embedding.

The checkpoint's training configuration is preserved at `config/pretrained_simple.yaml`. Set `model_config`, `ckpt` and `longclip_ckpt` in the inference YAML (the workshop notebook does this automatically), then run `python inference_style.py --config /path/to/inference.yaml` from this repository root. The old `run_dir/.hydra` layout remains supported for upstream compatibility but is not needed in the tutorial. The simple checkpoint is designed for the `simple_injection_clip` architecture; do not pair it with the `aggregator` config.

The original project and full training/evaluation instructions remain [upstream](https://github.com/joaxkal/AnyStyle). Bundled LongCLIP retains its [original license](src/longclip/LICENSE).
