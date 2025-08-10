# Image-based Story Generation

**Program:** Master of Science in Artificial Intelligence  
**University:** University of Michigan–Dearborn  
**Author:** Likhitha Kolluru  

---

## Overview

This project integrates **computer vision** (YOLO for object detection) and **natural language processing** (LLaMA2 for story generation) to automatically create narratives based on objects detected in images.  

The approach aims to go beyond simple image captioning by generating **coherent, multi-sentence stories**, making the visual data richer and more meaningful.

**Potential Applications:**
- Creative writing tools for children
- Assistive technologies for the visually impaired
- Interactive multimedia and educational content

---

## Methodology

### 1. Dataset Preparation
- Source: **COCO Dataset** via `pycocotools`
- Selected **10 random categories**
- Samples per category:
  - 500 training
  - 50 validation
- COCO JSON annotations → converted to YOLO TXT format (bounding boxes + class labels)

### 2. Model Training (Object Detection)
- Model: **YOLOv5**
- Trained for **25 epochs** on prepared dataset
- Metrics tracked: Precision, Recall, mAP@50, mAP@50–95

### 3. Story Generation
- After object detection, detected labels are passed to **LLaMA2** (Large Language Model)
- LLaMA2 generates a **narrative** contextualized around the detected objects

---

## Results

### Object Detection Metrics (YOLOv5)
- Precision (B): 37.46%
- Recall (B): 25.87%
- mAP@50 (B): 22.81%
- mAP@50–95 (B): 10.80%

**Category Performance:**
| Category       | AP (%) |
|----------------|--------|
| Dog            | 17.58  |
| Surfboard      | 10.15  |
| Kite           | 2.06   |
| Fire Hydrant   | 18.03  |
| Boat           | 3.97   |
| Bowl           | 8.99   |
| Wine Glass     | 3.94   |
| Baseball Bat   | 3.28   |
| Giraffe        | 23.08  |
| Cat            | 16.87  |

**Processing Speed:**
- Preprocessing: **1.03 ms/image**
- Inference: **25.14 ms/image**
- Postprocessing: **0.77 ms/image**
- Loss: **0.0001**

---

### Example Narrative
**Detected Object:** <img src="https://drive.google.com/file/d/1jDhldW9WOSuwRRx_bsUP63GA_pSZQCOD/view?usp=drive_link" width="500">
 
**Generated Story:**
> ”Once upon a time, in a vast savannah,
 there lived a majestic giraffe named Gerald. Gerald was
 the tallest and the most handsome giraffe in the whole
 savannah, with a long neck and spotted coat. He loved to roam around the savannah, exploring every nook and
 cranny, and enjoying the beautiful views of the sunrise
 and sunset.
 One day, while Gerald was out for a stroll, he came across
 a group of young gazelles playing near a watering hole.
 They were laughing and chasing each other, and Gerald
 couldn’t help but be charmed by their energy and joy. He
 watched them for a while, feeling a sense of nostalgia
 wash over him.
 As he watched the gazelles, he remembered his own
 youth, when he used to play with his siblings and friends
 in the savannah. They would run and jump and chase
 each other, just like the gazelles. But as he grew older,
 Gerald realized that he had lost touch with his playful
 side.” 


---

## Discussion

**Strengths:**
- Successfully integrates YOLO object detection with LLaMA2 story generation
- Produces coherent, contextually relevant narratives
- Efficient enough for potential real-time applications

**Limitations:**
- **Small dataset** (4,951 images) limits generalization
- **Category imbalance** affects underrepresented objects
- Narratives sometimes lack depth and creativity
- No standardized quantitative metric for story quality
- Computational constraints limited training epochs & batch size

---

## Future Work
- Expand dataset size & balance category representation
- Use stronger hardware for deeper training
- Apply augmentation to improve detection for small/rare objects
- Add **contextual scene understanding** (e.g., spatial relationships, interactions)
- Develop **metrics for narrative quality** (semantic coherence, diversity)
- Explore domain-specific applications (education, assistive tech, entertainment)

---

## References
- Redmon et al., *YOLO: Unified, Real-Time Object Detection*, CVPR 2016  
- Vaswani et al., *Attention is All You Need*, NeurIPS 2017  
- Li et al., *OSCAR: Object-Semantics Aligned Pre-Training*, ECCV 2020  
- Krause et al., *Image Paragraph Generation*, CVPR 2017  
- Radford et al., *Language Models are Unsupervised Multitask Learners*, OpenAI 2019  
- Touvron et al., *LLaMA: Open and Efficient Foundation Language Models*, 2023  








Prerecorded Presentation Video: [https://youtu.be/f0JQbr22W_M](https://youtu.be/f0JQbr22W_M)

Prerecorded Demo video: [https://youtu.be/7o9ASXt8Bk8?feature=shared](https://youtu.be/7o9ASXt8Bk8?feature=shared)

Google drive link: [https://drive.google.com/drive/folders/15CQ6NBbTzCLqotc1eCLb3fTjn3anD6SV?usp=sharing](https://drive.google.com/drive/folders/15CQ6NBbTzCLqotc1eCLb3fTjn3anD6SV?usp=sharing)

report: [https://drive.google.com/drive/folders/1stVCIzWG7WaO-PgM9sQkdgBqn73Bv8UO?usp=sharing](https://drive.google.com/drive/folders/1stVCIzWG7WaO-PgM9sQkdgBqn73Bv8UO?usp=sharing)

Presentation pdf: [https://drive.google.com/drive/folders/1e9U6MdXTYQ13f2oXybJnZeW-UU9OO-dm?usp=sharing](https://drive.google.com/drive/folders/1e9U6MdXTYQ13f2oXybJnZeW-UU9OO-dm?usp=sharing)

dataset: [https://drive.google.com/drive/folders/1Uepch87fbUcOODUb-nSN_JG4xcLF3_He?usp=sharing](https://drive.google.com/drive/folders/1Uepch87fbUcOODUb-nSN_JG4xcLF3_He?usp=sharing)  (Has both runs folder (model training) and dataset folder)
