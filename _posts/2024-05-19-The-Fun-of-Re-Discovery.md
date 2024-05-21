---
layout: post
title: "llama-np.py (1): The Fun of Re-discovery"
date: 2024-05-19
excerpt: "Start"
---

<img src="/lumi-blog/assets/q_proj.png" width="100%" />
(part of the q_proj weight)

## About `llama-np.py` and this blog series

As a Steinway maker sometimes dreams of being Chopin, I started`lumi` - a hands-on hobby project to teach myself the fundamentals of deep learning and explore new ideas. For fun and total flexibility, I want to build a deep learning (DL) stack myself. `llama-np.py` is the first baby step in this journey. 

The goal of `llama-np.py` was to perform inference of non-trivial language models at usable speed on my home PC.  For example, it should be able to handle inference for Llama-2-7B. I figured that 7 seconds per generated word would be tolerable. (It is not as I learnt.)

`llama-np.py` is being developed in the [open](https://github.com/yuanlin2004/lumi/tree/main/llama-np). Along with the code repository, I'd like to share my experiences and learnings, hence this blog series. 

`llama-np.py` was originally written in `numpy` as it was the starting point for many DL frameworks, such as Theano, Chainer, MXNet, PyTorch and JAX. Initially, I did not include using GPU as a must-have since I thought it would be just a performance bonus. However, I couldn't resist, and now `llama-np.py` can run on GPU via `cupy`. 

[Currently](https://github.com/yuanlin2004/lumi/tree/84b3832169e9b7ef4f1feaf9680bfba8acaff964), `llama-np.py` can perform llama-3-8B inference in fp32 at approximately 1.2 tokens per second (tok/s) on CPU and 2.24 tok/s on GPU, measured on my gaming PC circa 2023 (AMD Ryzen 7700x CPU with over 32GB RAM and a RTX 4070 GPU). To put this speed in perspective, [`llama.cpp`](https://github.com/ggerganov/llama.cpp) can perform Llama-3-8B inference at 10 tok/s, with 8 bit quantization. While `llama-np.py` is not the fastest, it is a very usable and provides me with the foundation needed for further exploration. 

## The *Flow* Approach to Learn and Explore

Deep Learning is evolving at such a rapid pace that staying updated can easily consume several hours each day. The fear of missing out (FOMO) quickly turns into LLM fatigue.  What is read from paper may become irrelevant soon, and for me, they might be forgotten in no time too. I need to be hands on. 

> I hear and I forget. I see and I remember. I do and I understand.


<img style="float:right;" src="/lumi-blog/assets/flow-book.jpg" width=100 />
I decided to adopt what I call the *flow* approach, inspired by the book [Flow: The Psychology of Optimal Experience](https://www.amazon.com/Flow-Psychology-Experience-Perennial-Classics/dp/0061339202/ref=sr_1_3?crid=5XIY2GV41XIN&dib=eyJ2IjoiMSJ9._j0mDkxa26hiBFJ4Ve5Ommk6ozi_XUDEz4d-VccaspAoaYRO1LG-SF_cIUIWRVQbMF-67hQuuM26EQgwXRK8aP2X_U1wMgHj7NKQo4QAbvrDTd5PiyVOB-2VBz5RMICu9tqBRv266nmTZTJxw4_MfXhQsyJwLJBxJ2wRdLOXz0_ArF6NTwscZjWfzV6nLf56zZWsH4GHHT6BX2QnXwkySXwTC5q9f9moRmGiL7-fego.2JwyR2EhPL20L3tMeB_gkSKTivJsl0HJUWHftSFEQ4s&dib_tag=se&keywords=flow&qid=1716268345&sprefix=flow%2Caps%2C183&sr=8-3) by Mihaly Csikszentmihalyi. It creates immersive, focused activities for me. I read just enough to get started and explore on my own, guided by my curiosity and interests. This is not the best approach to any work project, but for me, the fun is in the exploration. And since I was quite behind, I figured that if I were really blocked I would just search or GPT it up. It is like solving a puzzle with a cheat sheet in my pocket. 

With this in mind, I embarked on my journey. It was just what I expected: frustratingly fun! 

Looking back, the development went roughly through four phases. 
1. Functional: Llama2 text completion
2. Speed: CPU performance tuning
3. Functional: Llama3 text completion, chat and sampler
4. Speed: CPU and GPU performance tuning 

I will cover the four phases in the upcoming posts. 