# Food-Classifier-101
# 🍕 Food-101 Classifier

A deep learning image classifier that identifies **101 food categories** from photos, built with PyTorch and EfficientNet-B2.

[![HuggingFace Space](https://img.shields.io/badge/🤗%20HuggingFace-Space-yellow)](https://huggingface.co/spaces/Zalaid/food-classifier)
[![Python](https://img.shields.io/badge/Python-3.10+-blue)](https://python.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.0+-red)](https://pytorch.org)

---

## 🚀 Live Demo

Try it here → [huggingface.co/spaces/Zalaid/food-classifier](https://huggingface.co/spaces/Zalaid/food-classifier)

---

## 📌 Project Overview

This project trains a food image classifier on the [Food-101 dataset](https://data.vision.ee.ethz.ch/cvl/datasets_extra/food-101/) using transfer learning with EfficientNet-B2. Training was done in multiple stages to progressively fine tune the model for better accuracy.

---

## 🧠 Model Architecture

- **Base model:** EfficientNet-B2 (pretrained on ImageNet)
- **Custom classifier head:**

---

## 📊 Dataset

| Property | Value |
|---|---|
| Dataset | Food-101 |
| Training images | 75,750 |
| Test images | 25,250 |
| Classes | 101 |
| Image size | 260×260 |

---

## 🏋️ Training Strategy

Training was done in 3 stages to avoid overfitting and maximize accuracy:

### Stage 1 — Classifier Only (Epochs 1–10)
- Froze all EfficientNet layers
- Trained only the custom classifier head
- Learning rate: `1e-4`
- Result: **~75% accuracy**

### Stage 2 — Unfreeze Last Block (Epochs 11–15)
- Unfroze `blocks[6]`, `conv_head`, `bn2`
- Different learning rates per layer group
- Result: **~80% accuracy**

### Stage 3 — Unfreeze Deeper (Epochs 16–25)
- Also unfroze `blocks[5]`
- Higher learning rate for fine tuning
- Cosine annealing scheduler
- Result: **~82% accuracy**

---

## 📈 Training Results

| Epoch | Train Acc | Test Acc |
|---|---|---|
| 1 | 37.68% | 61.95% |
| 5 | 69.25% | 73.05% |
| 10 | 77.89% | 74.90% |
| 15 | 83.02% | 75.68% |
| 19 | 88.02% | 81.66% |
| 25 | ~85% | ~82% |

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| PyTorch | Model training |
| timm | EfficientNet-B2 pretrained weights |
| torchvision | Data loading + transforms |
| Gradio | Web interface |
| HuggingFace Spaces | Deployment |
| Google Colab | Training (T4 GPU) |

---

---

## 🍽️ Supported Food Categories

| | | | | |
|---|---|---|---|---|
| Apple Pie | Baby Back Ribs | Baklava | Beef Carpaccio | Beef Tartare |
| Beet Salad | Beignets | Bibimbap | Bread Pudding | Breakfast Burrito |
| Bruschetta | Caesar Salad | Cannoli | Caprese Salad | Carrot Cake |
| Ceviche | Cheesecake | Cheese Plate | Chicken Curry | Chicken Quesadilla |
| Chicken Wings | Chocolate Cake | Chocolate Mousse | Churros | Clam Chowder |
| Club Sandwich | Crab Cakes | Creme Brulee | Croque Madame | Cup Cakes |
| Deviled Eggs | Donuts | Dumplings | Edamame | Eggs Benedict |
| Escargots | Falafel | Filet Mignon | Fish And Chips | Foie Gras |
| French Fries | French Onion Soup | French Toast | Fried Calamari | Fried Rice |
| Frozen Yogurt | Garlic Bread | Gnocchi | Greek Salad | Grilled Cheese Sandwich |
| Grilled Salmon | Guacamole | Gyoza | Hamburger | Hot And Sour Soup |
| Hot Dog | Huevos Rancheros | Hummus | Ice Cream | Lasagna |
| Lobster Bisque | Lobster Roll Sandwich | Mac And Cheese | Macarons | Miso Soup |
| Mussels | Nachos | Omelette | Onion Rings | Oysters |
| Pad Thai | Paella | Pancakes | Panna Cotta | Peking Duck |
| Pho | Pizza | Pork Chop | Poutine | Prime Rib |
| Pulled Pork Sandwich | Ramen | Ravioli | Red Velvet Cake | Risotto |
| Samosa | Sashimi | Scallops | Seaweed Salad | Shrimp And Grits |
| Spaghetti Bolognese | Spaghetti Carbonara | Spring Rolls | Steak | Strawberry Shortcake |
| Sushi | Tacos | Takoyaki | Tiramisu | Tuna Tartare | Waffles |

---

