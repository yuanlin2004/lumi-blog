---
layout: post
title: "llama-np.py (1): The Fun of Re-discovery"
date: 2024-05-19
excerpt: "Start"
---

## About `llama-np.py` and this blog series

As a Steinway maker sometimes dreams of being Chopin, I started`lumi` - a hands-on project to teach myself the fundamentals of deep learning and explore new ideas. For fun and total flexibility, I want to build a deep learning (DL) stack myself. `llama-np.py` is the first baby step. 

The goal of `llama-np.py` was to perform inference of non-trivial language models at usable speed on my home PC.  For example, it should be able to inference Llama-2-7B. I figured that 7 seconds for each word generated was probably tolerable. 

`llama-np.py` is being developed in the [open](https://github.com/yuanlin2004/lumi/tree/main/llama-np). Together with the code repo, I'd like share my experience and learnings, hence this blog series. 

`llama-np.py` was originally written in `numpy`as it was also the starting look-and-feel of many DL frameworks, e.g. Theano, Chainer, MXNet, PyTorch and JAX, etc.  I did not include using GPU as a must-have in the beginning, as it would be just a performance bonus so I thought. But I could not resist it. Now `llama-np.py` can run on GPU via `cupy`. 

Right [now](https://github.com/yuanlin2004/lumi/tree/84b3832169e9b7ef4f1feaf9680bfba8acaff964), `llama-np.py` can do llama-3-8B inference in fp32 at approximately 1.2 tokens per second (tok/s) on CPU and 2.24 tok/s on GPU. It is on my gaming PC  circa 2023 (AMD Ryzen 7700x CPU with over 32GB RAM and an RTX 4070 GPU). To put the speed in perspective, `ollama (llama.cpp)` can do Llama-3-8B at, with 8 bit quantization. `llama-np.py` is by no-means speedy, but it is a very usable and give me the foundation needed for further exploration. 

## The *Flow* Approach to Learn and Explore

Deep Learning is moving at such a rapid pace that just to keep updated with what's going everyday can easily take a few hours a day. The FOMO turns into LLM fatigue quickly.  Whatever read from paper may become irrelevant soon. For me, they may be forgotten in no time too. I need to put my hands on. 

> I hear and I forget. I see and I remember. I do and I understand.

I decided to take what I call the *flow* approach, inspired by the book [Flow: The Psychology of Optimal Experience](https://www.amazon.com/Flow-Psychology-Experience-Perennial-Classics/dp/0061339202/ref=sr_1_3?crid=5XIY2GV41XIN&dib=eyJ2IjoiMSJ9._j0mDkxa26hiBFJ4Ve5Ommk6ozi_XUDEz4d-VccaspAoaYRO1LG-SF_cIUIWRVQbMF-67hQuuM26EQgwXRK8aP2X_U1wMgHj7NKQo4QAbvrDTd5PiyVOB-2VBz5RMICu9tqBRv266nmTZTJxw4_MfXhQsyJwLJBxJ2wRdLOXz0_ArF6NTwscZjWfzV6nLf56zZWsH4GHHT6BX2QnXwkySXwTC5q9f9moRmGiL7-fego.2JwyR2EhPL20L3tMeB_gkSKTivJsl0HJUWHftSFEQ4s&dib_tag=se&keywords=flow&qid=1716268345&sprefix=flow%2Caps%2C183&sr=8-3) by Mihaly Csikszentmihalyi. It creates the immersive, focused activities for me. I would read  just enough to get started and explore on my own, led by my curiosity and interests. This is not the best approach to any work project. But for me, the fun is in the exploration. And since I was quite behind, I figured that if I were really blocked I would just search/GPT it up. It is like solving a puzzle with a cheat sheet in my pocket. With this, I set on my journey. It was just what I expected, frustratingly fun! 

Looking back, the development went roughly through 4 phases. 
1. Functional: Llama2 text completion
2. Speed: CPU perf tuning
3. Functional: Llama3 text completion, chat and sampler
4. Speed: CPU and GPU perf tuning 

I will cover the 4 phases in the coming posts. 