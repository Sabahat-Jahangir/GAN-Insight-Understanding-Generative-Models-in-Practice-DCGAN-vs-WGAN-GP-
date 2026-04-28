### Overview

Anime GAN Showdown is an interactive deep learning application that explores how Generative Adversarial Networks actually behave in practice. Instead of just training models and plotting losses, this project puts two GAN variants—DCGAN and WGAN-GP—side by side and lets you see the difference yourself.

The application is built using Streamlit and allows real-time image generation, comparison, and analysis of training behavior. The focus is not just on generating anime faces, but on understanding why one model performs better than the other.

---

### Contributor

* Ishrat Fatima

---

### Purpose

GANs sound impressive until they collapse and start generating the same face over and over again. This project tackles that exact problem.

The goal is to:

* Build a baseline GAN (DCGAN)
* Improve it using WGAN-GP
* Visually and analytically compare both models
* Demonstrate how better loss functions lead to more stable training and diverse outputs

---

## Key Features

### Generation Module

* Generate anime faces using DCGAN
* Generate anime faces using WGAN-GP
* Control number of samples (1–16)
* Seed-based reproducibility

---

### Comparison Module

* Side-by-side comparison of both models
* Real-time generation for visual inspection
* Clear difference in diversity and quality

---

### Deep Dive Section

* Architecture breakdown of both models
* Explanation of loss functions
* Insight into training behavior

---

### Training Insights

* Generator and Discriminator/Critic loss curves
* Training progression visualization
* Observations on stability and convergence

---

### Model Differences

* Structured comparison between DCGAN and WGAN-GP
* Highlights issues like mode collapse and instability
* Explains why WGAN-GP performs better

---

## Project Flow

### 1. Data Preparation

* Dataset: Anime Faces (64×64) / Pokemon Sprites
* Images resized to 64×64
* Normalized to range [-1, 1]
* Loaded using PyTorch DataLoader

---

### 2. Model 1 – DCGAN (Baseline)

#### Generator

* Takes 100D noise vector
* Uses transposed convolutions
* Applies BatchNorm + ReLU
* Outputs image using Tanh activation

#### Discriminator

* Convolutional layers
* LeakyReLU activation
* Sigmoid output for classification

#### Training

* Loss: Binary Cross Entropy
* Behavior: Works, but unstable
* Common issue: Mode collapse

---

### 3. Model 2 – WGAN-GP (Improved)

#### Key Changes

* Discriminator replaced with Critic (no sigmoid)
* Loss changed to Wasserstein Distance
* Gradient Penalty added (λ = 10)
* Critic updated multiple times per generator step

#### Training

* More stable convergence
* Better diversity in generated images
* Reduced mode collapse

---

### 4. Training Strategy

* DCGAN trained first as baseline
* WGAN-GP trained afterward for improvement
* Mixed precision used for efficiency
* Checkpoints saved periodically
* Loss curves tracked for analysis

---

### 5. Visualization

* Generated samples from both models
* Direct comparison output
* Visual proof of training quality

---

## Results & Observations

* DCGAN generates decent images but struggles with stability
* WGAN-GP produces more consistent and diverse outputs
* Mode collapse is significantly reduced in WGAN-GP
* Training curves show smoother convergence for WGAN-GP

In simple terms:
DCGAN learns fast but forgets quickly. WGAN-GP learns slower but actually learns.

---

## Tech Stack

* Python
* PyTorch
* Streamlit
* NumPy, Matplotlib, Plotly
* PIL

---

## How to Run Locally

1. Clone the repository

```bash
git clone <your-repo-link>
cd DCGAN-vs-WGAN-GP
```

2. Install dependencies

```bash
pip install -r requirements.txt
```

3. Run the app

```bash
streamlit run anime_gan_app.py
```

4. Open in browser

```
http://localhost:8501
```

---

## Deployment (Streamlit Cloud)

1. Push project to GitHub
2. Go to [https://streamlit.io/cloud](https://streamlit.io/cloud)
3. Connect your GitHub account
4. Select repository
5. Set main file:

```
anime_gan_app.py
```

6. Click Deploy

Your app will be live in a few minutes.

---

## Real-World Relevance

This project is not just about anime faces. The techniques apply to:

* Image generation systems
* Data augmentation
* Creative AI tools
* Game asset generation
* Synthetic dataset creation

Organizations working in AI, gaming, or media generation can use similar approaches to build scalable generative systems.

---

## Challenges Faced

* Training instability in DCGAN
* Handling mode collapse
* Balancing generator and discriminator training
* Managing GPU memory constraints
* Ensuring fair comparison between models

---

## Future Improvements

* Add FID and Inception Score evaluation
* Introduce StyleGAN for advanced comparison
* Improve UI with more interactive controls
* Add real-time training visualization
* Support custom dataset uploads

---

## Conclusion

Anime GAN Showdown demonstrates the difference between “it works” and “it works properly.” By comparing DCGAN with WGAN-GP in a hands-on way, the project highlights why improvements in loss functions and training strategies matter.

Instead of just generating images, it helps understand what is happening behind the scenes—and where things usually go wrong.
