# Projet-TMR-Text-Motion-Retrieval
### Text-to-Motion Retrieval System: An AI-powered engine that aligns natural language descriptions with human motion sequences using a Dual-Encoder architecture (DistilBERT + Bi-GRU &amp; Self-Attention) and Contrastive Learning.

Overview
This project focuses on the development of a cross-modal retrieval engine designed to bridge the gap between natural language and physical human motion. By leveraging deep learning architectures, the system can interpret complex textual descriptions and identify the most corresponding 3D motion sequences within a large-scale database.

The core challenge lies in semantic alignment: ensuring that a sentence like "a person walks forward and then sits down" is mapped to the exact same mathematical space as the numerical coordinates representing that specific movement.

System Architecture
The system employs a Dual-Encoder framework (inspired by the CLIP architecture) to process and synchronize two fundamentally different types of data.

1. Textual Analysis Module (NLP)
Model: DistilBERT (Distilled Bidirectional Encoder Representations from Transformers).

Role: The encoder processes raw text strings to extract high-level semantic features. DistilBERT was chosen for its balance between computational efficiency and its ability to capture rich contextual meanings.

Output: A fixed-size latent vector representing the "intent" of the description.

2. Temporal Motion Module
Architecture: Bidirectional GRU (Gated Recurrent Units) combined with a Self-Attention mechanism.

Role: Unlike static data, motion is a time-series. The Bi-GRU layers process the sequence of joint coordinates in both forward and backward directions to capture the full context of the movement.

Attention Layer: A self-attention head is used to weigh the importance of specific time frames (e.g., the moment a person starts to sit), ensuring the final embedding is representative of the most critical parts of the motion.

3. Cross-Modal Alignment & Training
Latent Space Projection: Both text and motion vectors are projected into a shared high-dimensional embedding space.

Contrastive Learning: The model is trained using Contrastive Loss (InfoNCE style). The objective is to minimize the distance between matching text-motion pairs while maximizing the distance between mismatched pairs.

Similarity Metric: Cosine Similarity is used during inference to rank the motion candidates based on the user's input.

Technical Stack
Framework: PyTorch (Core Deep Learning library)

Language Modeling: Hugging Face Transformers

Sequence Processing: Bi-GRU, Self-Attention layers

Data Management: NumPy & Pandas for processing 3D coordinate datasets

Optimization: AdamW optimizer with custom learning rate scheduling

Key Accomplishments
Successfully implemented a Top-10 Retrieval pipeline, achieving high precision in matching complex gestures with text.

Developed a robust data pipeline to handle variable-length motion sequences through dynamic padding and masking.

Optimized model performance for GPU acceleration, significantly reducing inference time for real-time search capabilities.

Hazem Wannous and IKEN OMAR. TMR: Text-Motion Retrieval. https://kaggle.com/competitions/tmr-text-motion-retrieval, 2026. Kaggle.
