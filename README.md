# Kanji Diffusion

This repository contains a Jupyter notebook for fine-tuning the Stable Diffusion v1.4 model to generate new Kanji-like characters for words that don't have established Kanji representations. The notebook was originally run on Google Colab with GPU acceleration.

## Overview

The Kanji Diffusion project uses deep learning to create artificial Kanji characters that visually represent English words or concepts. The model is trained on existing Kanji from KanjiVG and their English meanings from KANJIDIC2, then used to generate new characters that follow similar visual patterns.

## Repository Content

This repository already includes all the necessary files:
- `kanji_diffusion.ipynb` - The main Jupyter notebook
- `train_text_to_image_lora.py` - The LoRA training script from Hugging Face
- `kanjidic2.xml` - The KANJIDIC2 dataset with kanji meanings
- `kanjivg-20220427.xml` - The KanjiVG dataset with SVG data

## Usage

1. Open the `kanji_diffusion.ipynb` notebook in Google Colab, Jupyter Lab, or another notebook environment. Google Colab with a GPU runtime is recommended for the best experience.
2. Follow the step-by-step instructions in the notebook:
   - Install dependencies
   - Log in to Hugging Face
   - Mount Google Drive (if using Colab)
   - Prepare training data from KanjiVG SVGs and KANJIDIC2
   - Fine-tune Stable Diffusion v1.4 model with LoRA
   - Generate new Kanji characters
   
If you don't want to run the entire training pipeline, you can skip to the last section and use the pre-trained model available on Hugging Face.

## Model Training

The model is trained using Low-Rank Adaptation (LoRA) on the Stable Diffusion v1.4 model. This process can take approximately 2 hours on a T4 GPU.

## Pre-trained Resources

The project has already generated these resources which are available on Hugging Face:

- Dataset: [Akirashindo39/KANJIDIC2](https://huggingface.co/datasets/Akirashindo39/KANJIDIC2)
- Trained Model: [Akirashindo39/kanji-diffusion-v1-4-kanjidic2](https://huggingface.co/Akirashindo39/kanji-diffusion-v1-4-kanjidic2)

You can use the pre-trained model directly without having to run the entire training process.

## Example Results

After training (or when using the pre-trained model), you can generate Kanji-like characters for any English word by running:

```python
new_kanji_meaning = "internet"  # Enter your desired meaning
prompt = f"a Kanji meaning {new_kanji_meaning}"
image = pipe(prompt).images[0]
image.save(f"{new_kanji_meaning}-kanji-v1-4.png")
```

### Sample Generated Kanji

![Sample Kanji for "internet"](internet-kanji-v1-4.png)

*This is a sample Kanji generated for the word "internet" using the fine-tuned model. These Kanji images were generated on Google Colab free version for proof of concept purposes. A bigger training run with more epochs and on more powerful hardware would result in much better images.*

## License

This project is available under the MIT License. See the LICENSE file for more details.

## Acknowledgments

- [KanjiVG](https://github.com/KanjiVG/kanjivg) for the Kanji SVG data
- [KANJIDIC2](https://www.edrdg.org/wiki/index.php/KANJIDIC_Project) for the Kanji definitions
- [Hugging Face Diffusers](https://github.com/huggingface/diffusers) for the Stable Diffusion implementation
- [CompVis](https://github.com/CompVis/stable-diffusion) for the original Stable Diffusion model