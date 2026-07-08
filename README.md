# OpenKurdish-ASR-A-Conformer-Transformer-Speech-Recognition-System-for-Sorani-and-Badini-Dialects
Kurdish language feom speech to text 
Abstract
​Despite recent breakthroughs in Natural Language Processing (NLP) and Automatic Speech Recognition (ASR), Kurdish remains a critically under-resourced language. Existing multilingual models often suffer from high Word Error Rates (WER) when processing regional dialects and fail to handle frequent code-switching. This project proposes the development of an open-source, state-of-the-art ASR model specifically optimized for كوردي باديني (Badini) and كوردي سوراني (Sorani). Leveraging a FastConformer encoder and an autoregressive Transformer decoder—a methodology proven highly effective for complex, multi-dialect languages—this project aims to deliver a high-throughput, production-ready speech-to-text foundation model for the Kurdistan Region and the broader research community.
​1. Introduction & Motivation
​The digital inclusion of the Kurdish language requires robust foundational AI models. Currently, transcription for Badini and Sorani dialects lacks the precision required for automated media monitoring, clinical dictation, and digital accessibility.
​Furthermore, speakers of these dialects frequently code-switch between Kurdish, Arabic, and English. By engineering a targeted dataset and utilizing a Conformer-Transformer architecture, this project will bridge the gap between high-resource and low-resource ASR, providing an open-source infrastructure for developers and researchers.
​2. Project Objectives
​Corpus Development: Curate and open-source a highly diverse, dialect-tagged Kurdish audio-text dataset (1,000+ hours) encompassing varying acoustic environments and code-switching scenarios.
​Architecture Implementation: Train a robust ASR model combining the local acoustic feature extraction of FastConformers with the global contextual processing of Transformers.
​High-Throughput Optimization: Ensure the final model weights are compatible with vLLM and the Hugging Face transformers ecosystem for seamless Linux-based deployment and API integration.
​Open Access: Release the model, dataset, and training pipelines under a permissive Apache 2.0 license.
​3. Methodology
​3.1. Data Engineering Pipeline
​The foundation of this model relies on rigorous data curation rather than purely relying on parameter scale.
​Scraping & Aggregation: Sourcing high-quality audio from regional broadcast media, parliamentary sessions, and public domain podcasts.
​Tokenization & Dialect Tagging: Implementing strict control tokens (<|badini|>, <|sorani|>) to prime the model for specific phonetics, vocabulary, and orthography.
​Script Standardization: Normalizing Sorani (Arabic script) and managing Badini’s dual-script nature (Arabic and Hawar/Latin) through automated transliteration and text-cleaning pipelines in Python.
​Noise Augmentation: Injecting synthetic silence, background chatter, and static during the data preparation phase to prevent the "eager transcription" hallucinations common in modern ASR models.
​3.2. Model Architecture
​The system will mirror the architectural efficiency of recent high-performance dialectal models, operating within a PyTorch-based training environment.
​Encoder (Acoustic Modeling): A FastConformer block. It will downsample input audio sequences to 16kHz and extract log-Mel spectrograms, efficiently capturing both local phonetic boundaries and wider prosodic contexts.
​Decoder (Text Generation): A lightweight autoregressive Transformer. It will utilize cross-attention mechanisms to map the rich acoustic embeddings from the encoder into accurate Kurdish text tokens.
​3.3. Training Strategy
​Training a multi-billion parameter model from scratch is computationally prohibitive. We will employ a Transfer Learning paradigm:
​Base Model Selection: Initialize weights from a leading multilingual Conformer-based ASR (e.g., highly resourced open-source checkpoints).
​Layer Freezing: Freeze the foundational acoustic extraction layers of the encoder.
​Targeted Fine-Tuning: Continuously pre-train the upper encoder layers and the entire Transformer decoder exclusively on the curated Kurdish corpus.
​4. Evaluation Metrics
​The model's performance will be benchmarked against existing commercial and open-source baselines using a withheld "Golden Dataset" of 20 hours of manually verified, studio-quality speech.
​Primary Metric: Word Error Rate (WER) and Character Error Rate (CER), stratified by dialect (Badini vs. Sorani).
​Efficiency Metric: Real-Time Factor multiple (RTFx) to measure throughput capabilities for concurrent inference workloads.
​5. Development Roadmap
