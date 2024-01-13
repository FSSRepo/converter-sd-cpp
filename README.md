# Converter Stable Diffusion cpp
A simple converter of models for [stable-diffusion-cpp](https://github.com/leejet/stable-diffusion.cpp).

# Compile

First, You need to get the code, using the following commands:

```bash
git clone https://github.com/FSSRepo/converter-sd-cpp.git
cd converter-sd-cpp
```

Inside the folder of the local repository, execute this:

```bash
mkdir build
cmake -S . -B build
cmake --build . --config Release
```

# Usage

```bash
usage: convert [MODEL_PATH] --type [OUT_TYPE] [arguments]
Model supported for conversion: .safetensors models or .ckpt checkpoints models

arguments:
  -h, --help                         show this help message and exit
  -o, --out [FILENAME]               path or name to converted model
  -v, --verbose                      print processing info - dev info
  -l, --lora                         force read the model as a LoRA
  --vae [FILENAME]                   merge a custom VAE
  -t, --type [OUT_TYPE]              output format (f32, f16, q4_0, q4_1, q5_0, q5_1, q8_0)
```

Example:

```bash
build/bin/convert sd-v1-4.ckpt --type q8_0 -v
```