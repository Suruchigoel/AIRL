# Final Project Report

## Q1 — Vision Transformer on CIFAR-10
- **Paper**: *An Image is Worth 16x16 Words: Transformers for Image Recognition at Scale* (Dosovitskiy et al., ICLR 2021)  
- **Implementation**: Vision Transformer (ViT) in PyTorch, trained on CIFAR-10.  
- **Best Test Accuracy**: **97.15%**  

### Configuration
- Patch size: 16  
- Embedding dim: 512  
- Depth: 8 layers  
- Optimizer: AdamW (lr=3e-4)  
- Scheduler: Cosine Annealing LR  
- Epochs: 10  
- Batch size: 128  

### Results
| Model | Test Accuracy |
|-------|---------------|
| ViT   | 97.15%        |

---

## Q2 — Text-Driven Image Segmentation with SAM 2
- **Pipeline**:  
  1. Load image  
  2. Accept text prompt (e.g., `"a cat"`)  
  3. Convert text → region seeds (using CLIPSeg / GroundingDINO)  
  4. Feed seeds → SAM 2  
  5. Display final segmentation mask overlay  

- **Limitations**:
  - Accuracy depends on quality of text-to-seed model.  
  - May fail on very small or overlapping objects.  
  - Requires GPU runtime on Colab (slower on CPU).  

---

## How to Run in Colab
1. Open **q1.ipynb** in Google Colab.  
   - Runtime → Change runtime type → GPU  
   - Run all cells to train & evaluate the Vision Transformer on CIFAR-10.  

2. Open **q2.ipynb** in Google Colab.  
   - Run all cells to install dependencies, load an image, enter a text prompt, and visualize segmentation.  

---

## Bonus (Optional Analysis)
- **Patch size trade-off**: Smaller patches capture fine-grained features but increase computation. Patch size 16 was a good balance for CIFAR-10.  
- **Depth/width**: Increasing depth beyond 8 did not yield big improvements (likely due to dataset size).  
- **Augmentation**: Random cropping & flipping improved robustness.  
