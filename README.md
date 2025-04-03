# 🧠 Deepfake Detection with Vision Transformer (ViT)

This project uses a fine-tuned Vision Transformer (ViT) model to detect deepfake images. It classifies images as either **real** or **fake** using Hugging Face Transformers.

## 🚀 Features

- Vision Transformer (`google/vit-base-patch16-224-in21k`)
- Fine-tuned on real vs fake image dataset
- Inference support on sample images
- All-in-one training + evaluation + prediction script

## 🗂️ Project Structure

```
.
├── vit-deepfake-finetune/
│   └── best_model/           # Fine-tuned model saved here
├── inference.py              # Script to train and test
├── README.md                 # You're here
```

## 📦 Installation

```bash
pip install torch torchvision transformers datasets evaluate pillow
```

## 🏋️‍♂️ Training the Model

Just run the script:

```bash
python inference.py
```

What it does:
- Loads images from your dataset
- Trains a ViT model (3 epochs by default)
- Saves the best model to `./vit-deepfake-finetune/best_model`
- Evaluates model accuracy
- Runs sample predictions

## 🔍 Inference Example

At the end of the script, it loads 3 real and 3 fake test images and prints predictions:

```
image1.jpg: predicted = real, actual = real
image2.jpg: predicted = fake, actual = fake
...
Accuracy on test images: 6/6
```

To change test paths or number of images:

```python
real_test_images = load_test_images("/path/to/Real", max_images=3, label=0)
fake_test_images = load_test_images("/path/to/Fake", max_images=3, label=1)
```

## 🖼️ Dataset Structure

Make sure your folders are set up like this:

```
Dataset/
└── Validation/
    ├── Real/
    └── Fake/

Test/
├── Real/
└── Fake/
```

Each folder should contain `.jpg` or `.png` images.

## 📊 Evaluation Output

After training, the script prints accuracy:

```
Evaluation Accuracy: 0.92
```

## ⚙️ Customization

- Change training settings inside `TrainingArguments`:
  ```python
  num_train_epochs=3
  per_device_train_batch_size=2
  ```

- Modify dataset paths, number of images, etc. as needed

## 🙏 Acknowledgements

- [Hugging Face Transformers](https://huggingface.co/transformers/)
- [ViT Base Model](https://huggingface.co/google/vit-base-patch16-224-in21k)
- PyTorch, Datasets, Evaluate, Pillow

## 💡 Future Ideas

- Add real-time image prediction via CLI or web app
- Extend to deepfake video frame analysis
- Improve with data augmentation
