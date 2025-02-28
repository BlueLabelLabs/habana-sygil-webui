# <center>Web-based UI for Stable Diffusion</center>

## Created by [Sygil.Dev](https://github.com/sygil-dev)

## Join us at Sygil.Dev's Discord Server [![Generic badge](https://flat.badgen.net/discord/members/ttM8Tm6wge?icon=discord)](https://discord.gg/ttM8Tm6wge)

## Installation instructions for:

- **[Windows](https://sygil-dev.github.io/sygil-webui/docs/Installation/windows-installation)**
- **[Linux](https://sygil-dev.github.io/sygil-webui/docs/Installation/linux-installation)**

### Want to ask a question or request a feature?

Come to our [Discord Server](https://discord.gg/gyXNe4NySY) or use [Discussions](https://github.com/sygil-dev/sygil-webui/discussions).

## Documentation

[Documentation is located here](https://sygil-dev.github.io/sygil-webui/)

## Want to contribute?

Check the [Contribution Guide](CONTRIBUTING.md)

[Sygil-Dev](https://github.com/Sygil-Dev) main devs:

* ![ZeroCool940711's avatar](https://avatars.githubusercontent.com/u/5977640?s=40&v=4)[ZeroCool940711](https://github.com/ZeroCool940711)
* ![Kasiya13's avatar](https://avatars.githubusercontent.com/u/26075839?s=40&v=4)[Kasiya13](https://github.com/Kasiya13)

### Project Features:

* Built-in image enhancers and upscalers, including GFPGAN and realESRGAN

* Generator Preview: See your image as its being made

* Run additional upscaling models on CPU to save VRAM

* Textual inversion: [Reaserch Paper](https://textual-inversion.github.io/)

* K-Diffusion Samplers: A great collection of samplers to use, including:

  - `k_euler`
  - `k_lms`
  - `k_euler_a`
  - `k_dpm_2`
  - `k_dpm_2_a`
  - `k_heun`
  - `PLMS`
  - `DDIM`

* Loopback: Automatically feed the last generated sample back into img2img

* Prompt Weighting & Negative Prompts: Gain more control over your creations

* Selectable GPU usage from Settings tab

* Word Seeds: Use words instead of seed numbers

* Automated Launcher: Activate conda and run Stable Diffusion with a single command

* Lighter on VRAM: 512x512 Text2Image & Image2Image tested working on 4GB (with *optimized* mode enabled in Settings)

* Prompt validation: If your prompt is too long, you will get a warning in the text output field

* Sequential seeds for batches: If you use a seed of 1000 to generate two batches of two images each, four generated images will have seeds: `1000, 1001, 1002, 1003`.

* Prompt matrix: Separate multiple prompts using the `|` character, and the system will produce an image for every combination of them.

* [Gradio] Advanced img2img editor with Mask and crop capabilities

* [Gradio] Mask painting 🖌️: Powerful tool for re-generating only specific parts of an image you want to change (currently Gradio only)

# SD WebUI

An easy way to work with Stable Diffusion right from your browser.

## Streamlit

![](images/streamlit/streamlit-t2i.png)

**Features:**

- Clean UI with an easy to use design, with support for widescreen displays
- *Dynamic live preview* of your generations
- Easily customizable defaults, right from the WebUI's Settings tab
- An integrated gallery to show the generations for a prompt
- *Optimized VRAM* usage for bigger generations or usage on lower end GPUs
- *Text to Video:* Generate video clips from text prompts right from the WebUI (WIP)
- Image to Text: Use [CLIP Interrogator](https://github.com/pharmapsychotic/clip-interrogator) to interrogate an image and get a prompt that you can use to generate a similar image using Stable Diffusion.
- *Concepts Library:* Run custom embeddings others have made via textual inversion.
- Textual Inversion training: Train your own embeddings on any photo you want and use it on your prompt.
- **Currently in development: [Stable Horde](https://stablehorde.net/) integration; ImgLab, batch inputs, & mask editor from Gradio

**Prompt Weights & Negative Prompts:**

To give a token (tag recognized by the AI) a specific or increased weight (emphasis), add `:0.##` to the prompt, where `0.##` is a decimal that will specify the weight of all tokens before the colon.
Ex: `cat:0.30, dog:0.70` or `guy riding a bicycle :0.7, incoming car :0.30`

Negative prompts can be added by using  `###` , after which any tokens will be seen as negative.
Ex: `cat playing with string ### yarn` will negate `yarn` from the generated image.

Negatives are a very powerful tool to get rid of contextually similar or related topics, but **be careful when adding them since the AI might see connections you can't**, and end up outputting gibberish

**Tip:* Try using the same seed with different prompt configurations or weight values see how the AI understands them, it can lead to prompts that are more well-tuned and less prone to error.

Please see the [Streamlit Documentation](docs/4.streamlit-interface.md) to learn more.

## Gradio [Legacy]

![](images/gradio/gradio-t2i.png)

**Features:**

- Older UI that is functional and feature complete.
- Has access to all upscaling models, including LSDR.
- Dynamic prompt entry automatically changes your generation settings based on `--params` in a prompt.
- Includes quick and easy ways to send generations to Image2Image or the Image Lab for upscaling.

**Note: the Gradio interface is no longer being actively developed by Sygil.Dev and is only receiving bug fixes.**

Please see the [Gradio Documentation](https://sygil-dev.github.io/sygil-webui/docs/Gradio/gradio-interface/) to learn more.

## Image Upscalers

---

### GFPGAN

![](images/GFPGAN.png)

Lets you improve faces in pictures using the GFPGAN model. There is a checkbox in every tab to use GFPGAN at 100%, and also a separate tab that just allows you to use GFPGAN on any picture, with a slider that controls how strong the effect is.

If you want to use GFPGAN to improve generated faces, you need to install it separately.
Download [GFPGANv1.4.pth](https://github.com/TencentARC/GFPGAN/releases/download/v1.3.4/GFPGANv1.4.pth) and put it
into the `/sygil-webui/models/gfpgan` directory.

### RealESRGAN

![](images/RealESRGAN.png)

Lets you double the resolution of generated images. There is a checkbox in every tab to use RealESRGAN, and you can choose between the regular upscaler and the anime version.
There is also a separate tab for using RealESRGAN on any picture.

Download [RealESRGAN_x4plus.pth](https://github.com/xinntao/Real-ESRGAN/releases/download/v0.1.0/RealESRGAN_x4plus.pth) and [RealESRGAN_x4plus_anime_6B.pth](https://github.com/xinntao/Real-ESRGAN/releases/download/v0.2.2.4/RealESRGAN_x4plus_anime_6B.pth).
Put them into the `sygil-webui/models/realesrgan` directory.

### LSDR

Download **LDSR** [project.yaml](https://heibox.uni-heidelberg.de/f/31a76b13ea27482981b4/?dl=1) and [model last.cpkt](https://heibox.uni-heidelberg.de/f/578df07c8fc04ffbadf3/?dl=1). Rename `last.ckpt` to `model.ckpt` and place both under `sygil-webui/models/ldsr/`

### GoBig, and GoLatent *(Currently on the Gradio version Only)*

More powerful upscalers that uses a separate Latent Diffusion model to more cleanly upscale images.

Please see the [Post-Processing Documentation](https://sygil-dev.github.io/sygil-webui/docs/post-processing) to learn more.

-----

### *Original Information From The Stable Diffusion Repo:*

# Stable Diffusion

*Stable Diffusion was made possible thanks to a collaboration with [Stability AI](https://stability.ai/) and [Runway](https://runwayml.com/) and builds upon our previous work:*

[**High-Resolution Image Synthesis with Latent Diffusion Models**](https://ommer-lab.com/research/latent-diffusion-models/)
[Robin Rombach](https://github.com/rromb)\*,
[Andreas Blattmann](https://github.com/ablattmann)\*,
[Dominik Lorenz](https://github.com/qp-qp)\,
[Patrick Esser](https://github.com/pesser),
[Björn Ommer](https://hci.iwr.uni-heidelberg.de/Staff/bommer)


## Diffusers Integration on Intel® Gaudi® HPU

A simple way to download and sample Stable Diffusion is by using the [diffusers library](https://github.com/huggingface/diffusers/tree/main#new--stable-diffusion-is-now-fully-compatible-with-diffusers):

```python
from torch import autocast
import time
from optimum.habana.diffusers import GaudiDDIMScheduler, GaudiStableDiffusionPipeline

model_name = "CompVis/stable-diffusion-v1-4"

scheduler = GaudiDDIMScheduler.from_pretrained(model_name, subfolder="scheduler")

pipe = GaudiStableDiffusionPipeline.from_pretrained(
    model_name,
    scheduler=scheduler,
    use_habana=True,
    use_hpu_graphs=True,
    gaudi_config="Habana/stable-diffusion",
)

from habana_frameworks.torch.utils.library_loader import load_habana_module
from optimum.habana.transformers.modeling_utils import adapt_transformers_to_gaudi
load_habana_module()

# Adapt transformers models to Gaudi for optimization
adapt_transformers_to_gaudi()

pipe = pipe.to("hpu")

prompt = "a photo of an astronaut riding a horse on mars"

with autocast("hpu"):
    t1 = time.perf_counter()
    upscaled_image = pipe(
        prompt=[prompt],
        num_images_per_prompt=2,
        batch_size=4,
        output_type="pil",
    ).images[0]

upscaled_image.save("astronaut_rides_horse.png")
print(f"Time taken: {time.perf_counter() - t1:.2f}s")
```

Note: This information has also been added to the Stable Diffusion core repository.

**CVPR '22 Oral**

which is available on [GitHub](https://github.com/CompVis/latent-diffusion). PDF at [arXiv](https://arxiv.org/abs/2112.10752). Please also visit our [Project page](https://ommer-lab.com/research/latent-diffusion-models/).

[Stable Diffusion](#stable-diffusion-v1) is a latent text-to-image diffusion
model.
Thanks to a generous compute donation from [Stability AI](https://stability.ai/) and support from [LAION](https://laion.ai/), we were able to train a Latent Diffusion Model on 512x512 images from a subset of the [LAION-5B](https://laion.ai/blog/laion-5b/) database.
Similar to Google's [Imagen](https://arxiv.org/abs/2205.11487),
this model uses a frozen CLIP ViT-L/14 text encoder to condition the model on text prompts.
With its 860M UNet and 123M text encoder, the model is relatively lightweight and runs on a GPU with at least 10GB VRAM.
See [this section](#stable-diffusion-v1) below and the [model card](https://huggingface.co/CompVis/stable-diffusion).

## Stable Diffusion v1

Stable Diffusion v1 refers to a specific configuration of the model
architecture that uses a downsampling-factor 8 autoencoder with an 860M UNet
and CLIP ViT-L/14 text encoder for the diffusion model. The model was pretrained on 256x256 images and
then finetuned on 512x512 images.

*Note: Stable Diffusion v1 is a general text-to-image diffusion model and therefore mirrors biases and (mis-)conceptions that are present
in its training data.
Details on the training procedure and data, as well as the intended use of the model can be found in the corresponding [model card](https://huggingface.co/CompVis/stable-diffusion).

## Stable Diffusion Integration with Intel® Gaudi® HPU

Stable Diffusion has been successfully integrated with Intel® Gaudi® HPUs, enabling high-performance text-to-image generation and image modifications on Habana’s specialized AI hardware. This enhancement leverages Habana’s optimized PyTorch environment to maximize efficiency and scalability for AI workloads.

## Stable Diffusion Integration with Intel® Gaudi® HPU

Stable Diffusion can be effectively run on Intel® Gaudi® HPUs, providing high-performance capabilities for deploying text-to-image generation systems in Dockerized environments. This approach is particularly valuable for frontend applications requiring real-time generative AI solutions. 

### Key Benefits of Intel® Gaudi® HPUs:

- **Optimized Performance:** Intel® Gaudi® HPUs are designed for deep learning workloads, delivering efficient and scalable solutions for generative AI tasks.
- **Docker Compatibility:** Pre-configured Docker containers make it easy to set up and deploy Stable Diffusion workflows.
- **Cost Efficiency:** Lower training and inference costs compared to traditional GPU-based systems.
- **Documentation and Support:** Comprehensive resources are available at [Intel® Gaudi® Documentation](https://docs.habana.ai/en/latest/index.html).

### Running Stable Diffusion on Intel® Gaudi® HPUs with Docker

#### Step 1: Prepare the Docker Environment

Intel® provides prebuilt Docker images optimized for Gaudi® HPUs. Follow these steps to set up your environment:

1. Pull the Base Image:
   ```bash
   docker pull vault.habana.ai/gaudi-docker/1.18.0/ubuntu22.04/habanalabs/pytorch-installer-2.3.1:latest
   ```

2. Build a Docker Image for Stable Diffusion:
   ```bash
   docker build -t sd_hpu:latest -f Dockerfile.hpu .
   ```

3. Run the Docker Container:
   ```bash
   docker run -it --runtime=habana sd_hpu:latest
   ```
   Use the `-v` option to mount local directories if needed.

#### Step 2: Configure Stable Diffusion

Inside the Docker container, configure and run Stable Diffusion pipelines. The Docker environment comes preloaded with Habana-specific optimizations, enabling seamless execution.

### Exploring Habana’s Tools and Documentation

Habana’s tools, such as SynapseAI and Gaudi-specific libraries, are tailored to enhance the performance of AI models. Key resources include:

- **Framework Integrations:** Optimized support for PyTorch and TensorFlow.
- **HPU Graph Support:** Efficient execution for both training and inference workflows.
- **Detailed Documentation:** Access the [Intel® Gaudi® Documentation](https://docs.habana.ai/en/latest/index.html) for technical insights, best practices, and troubleshooting.

### Why Choose Intel® Gaudi® HPUs

Intel® Gaudi® HPUs empower developers to achieve real-time, low-latency performance for frontend AI applications. By leveraging Dockerized environments and Habana’s software stack, developers can:

- Quickly deploy AI solutions with minimal setup.
- Optimize generative AI tasks for cost and efficiency.
- Access a robust ecosystem of tools and resources.

Incorporating Intel® Gaudi® HPUs into your AI workflows ensures that you stay ahead in delivering cutting-edge solutions for next-generation frontend applications.

### Additional Notes

- Ensure that the required models and checkpoints are available in their respective directories.
- Refer to the [Habana AI Developer Documentation](https://docs.habana.ai/en/latest/index.html) for further guidance on HPU-specific optimizations and troubleshooting.

With this integration, developers can now harness the power of Intel® Gaudi® HPUs for Stable Diffusion workflows, enabling cutting-edge generative AI tasks with optimized performance and scalability.

## Comments

- Our code base for the diffusion models builds heavily on [OpenAI's ADM codebase](https://github.com/openai/guided-diffusion)
  and [https://github.com/lucidrains/denoising-diffusion-pytorch](https://github.com/lucidrains/denoising-diffusion-pytorch).
  Thanks for open-sourcing!

- The implementation of the transformer encoder is from [x-transformers](https://github.com/lucidrains/x-transformers) by [lucidrains](https://github.com/lucidrains?tab=repositories).

## BibTeX

```
@misc{rombach2021highresolution,
      title={High-Resolution Image Synthesis with Latent Diffusion Models},
      author={Robin Rombach and Andreas Blattmann and Dominik Lorenz and Patrick Esser and Björn Ommer},
      year={2021},
      eprint={2112.10752},
      archivePrefix={arXiv},
      primaryClass={cs.CV}
}
```
