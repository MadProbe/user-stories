My first AI work I've ever done is made using these tools:
- https://github.com/AUTOMATIC1111/stable-diffusion-webui (That's the best thing I've ever found and it does its job very well)
- https://civitai.com/models/9139/checkpointyesmix?modelVersionId=11086 (base model, "checkpoint")
- https://civitai.com/models/115839/tokisaki-kurumi-date-a-live?modelVersionId=125371 (LoRA model of Tokisaki Kurumi)
- https://civitai.com/models/7808/easynegative (EasyNegative TI model to get images better as I seen in example images)
- I have run sdw with `--reinstall-xformers` and then modified `user-webui.bat` so:

```bat
@echo off

set PYTHON="C:\Program Files\Python310\python.exe"
set GIT=
set VENV_DIR=
# I have 1050TI on my machine (4GB VRAM), so these options help to squeeze in that limit and not running much into Shared Memory heaps (= amount of physical RAM installed AFAIK), you can remove this if you have a better GPU with like 16+GB VRAM
set COMMANDLINE_ARGS=--lowvram --opt-split-attention
# Also don't crash with obscure OOM errors (why it just couldn't allocate more space when there's plenty more RAM left to suck up? - IDFK)
set PYTORCH_CUDA_ALLOC_CONF=max_split_size_mb:128

# Launch with xformers for best performance
call webui.bat --xformers %*
```

SDWUI Extentions:
sd-model-preview-xd 	https://github.com/CurtisDS/sd-model-preview-xd
sd-webui-additional-networks 	https://github.com/kohya-ss/sd-webui-additional-networks.git
stable-diffusion-webui-embedding-merge 	https://github.com/klimaleksus/stable-diffusion-webui-embedding-merge.git

Also run `user-webui.bat` with `--reinstall-xformers` at a first time.
That's all!
