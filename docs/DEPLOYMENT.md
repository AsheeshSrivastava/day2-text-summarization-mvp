# 🚀 Deployment Guide

> **Deploy Your Text Summarization App** to Production
> Free and paid hosting options for permanent URLs

---

## 📋 Deployment Options Comparison

| Platform | Cost | Setup Time | GPU | Pros | Cons |
|----------|------|------------|-----|------|------|
| **HuggingFace Spaces** | Free | 10 min | Yes (paid) | Easy, permanent URL | 16GB RAM limit |
| **Google Colab** | Free | 2 min | Yes | No setup | 72-hour limit |
| **Streamlit Cloud** | Free | 15 min | No | GitHub integration | CPU only |
| **Railway** | $5/mo | 20 min | No | Docker support | Paid only |
| **Render** | Free tier | 30 min | No | Auto-deploy | Slow cold start |
| **AWS/GCP** | Pay-as-go | 60 min | Yes | Scalable | Complex setup |

**Recommended for Bootcamp**: **HuggingFace Spaces** (free, permanent, easy)

---

## 🤗 HuggingFace Spaces (Recommended)

### Why HuggingFace Spaces?
- ✅ **Free**: Permanent hosting at no cost
- ✅ **Easy**: One-command deployment
- ✅ **Fast**: Built-in Gradio support
- ✅ **Shareable**: Professional URL: `huggingface.co/spaces/username/app`
- ✅ **GPU**: Available (paid tier, $0.60/hour)

### Prerequisites
- HuggingFace account (free)
- Git installed
- Project on your local machine

---

### Method 1: **Gradio Deploy** (Easiest) ⭐

**Step 1: Install Gradio CLI**
```bash
pip install gradio
```

**Step 2: Login to HuggingFace**
```bash
huggingface-cli login
# Paste your token from: https://huggingface.co/settings/tokens
```

**Step 3: Deploy**
```bash
cd day2-text-summarization-mvp

# Convert notebook to app.py (see below)
# Then deploy:
gradio deploy
```

You'll be prompted for:
- **Space name**: `text-summarization-mvp`
- **Hardware**: Select "CPU (free)" or "GPU T4 ($0.60/hr)"

**Result**: Permanent URL at `https://huggingface.co/spaces/YOUR_USERNAME/text-summarization-mvp`

---

### Method 2: **Manual Git Deployment**

**Step 1: Create Space**
1. Go to [HuggingFace Spaces](https://huggingface.co/spaces)
2. Click **"Create new Space"**
3. Name: `text-summarization-mvp`
4. License: MIT
5. Select **Gradio** SDK
6. Click **"Create Space"**

**Step 2: Clone Your Space**
```bash
git clone https://huggingface.co/spaces/YOUR_USERNAME/text-summarization-mvp
cd text-summarization-mvp
```

**Step 3: Add Files**
```bash
# Copy your app files
cp ../day2-text-summarization-mvp/app.py .
cp ../day2-text-summarization-mvp/requirements.txt .

# Create README.md with metadata
cat > README.md << EOF
---
title: Text Summarization MVP
emoji: 📝
colorFrom: blue
colorTo: green
sdk: gradio
sdk_version: 5.0.0
app_file: app.py
pinned: false
---

# Text Summarization MVP
AI-powered text summarization with multi-format export
EOF
```

**Step 4: Commit and Push**
```bash
git add .
git commit -m "Initial deployment"
git push
```

**Step 5: Wait for Build**
- Go to your Space URL
- Wait 5-10 minutes for build
- App will be live!

---

### Converting Notebook to app.py

**Create `app.py`** from your notebook:

```python
# app.py
import os
import sys
import time
from datetime import datetime
import hashlib
import json

import gradio as gr
import torch
from transformers import AutoTokenizer, AutoModelForSeq2SeqLM
from gtts import gTTS
from reportlab.lib.pagesizes import letter
from reportlab.platypus import SimpleDocTemplate, Paragraph

# [Copy all class definitions from notebook]
class Config:
    # ... (copy from notebook)

class ModelManager:
    # ... (copy from notebook)

class CacheManager:
    # ... (copy from notebook)

class TextProcessor:
    # ... (copy from notebook)

class ExportManager:
    # ... (copy from notebook)

class SummarizationEngine:
    # ... (copy from notebook)

# Initialize components
model_manager = ModelManager()
cache_manager = CacheManager()
text_processor = TextProcessor()
export_manager = ExportManager()
engine = SummarizationEngine()

# [Copy interface code from notebook]
with gr.Blocks(title="Text Summarization", theme=gr.themes.Soft()) as interface:
    # ... (copy from notebook)

# Launch
if __name__ == "__main__":
    interface.launch()
```

**Simplified app.py** (extract from notebook cells 1-25)

---

### HuggingFace Spaces Configuration

**Edit `README.md`** in your Space:

```yaml
---
title: Text Summarization MVP
emoji: 📝
colorFrom: blue
colorTo: purple
sdk: gradio
sdk_version: 5.0.0
app_file: app.py
pinned: false
license: mit
duplicated_from: YOUR_USERNAME/text-summarization-mvp
models:
  - facebook/bart-large-cnn
  - t5-small
  - t5-base
  - google/pegasus-xsum
---
```

---

## ☁️ Google Colab (Quick Demo)

### Pros & Cons
- ✅ **No setup**: Upload and run
- ✅ **Free GPU**: T4 GPU available
- ⏰ **72-hour limit**: Session expires
- 🔗 **7-day link**: Public URL expires

### Deployment Steps

1. Upload `text_summarization_mvp_enhanced.ipynb` to Colab
2. Run all cells
3. Share the public URL (valid 7 days)

**Use Case**: Quick demos, bootcamp submissions with screenshots

---

## 🎨 Streamlit Cloud

### Why Streamlit?
- Free hosting
- GitHub integration (auto-deploy on push)
- Custom domain support

### Prerequisites
- Convert Gradio app to Streamlit
- GitHub repository

### Deployment Steps

**1. Convert to Streamlit**
```python
# streamlit_app.py
import streamlit as st

st.title("📝 Text Summarization")

text = st.text_area("Enter text:", height=200)
model = st.selectbox("Model:", ["t5-small", "BART"])

if st.button("Summarize"):
    summary = engine.summarize(text, model)
    st.write(summary)
```

**2. Create `requirements.txt`**
```
streamlit
transformers
torch
```

**3. Deploy**
1. Push to GitHub
2. Go to [Streamlit Cloud](https://streamlit.io/cloud)
3. Connect GitHub
4. Select repository
5. Deploy

**Result**: URL like `https://your-app.streamlit.app`

---

## 🚂 Railway (Docker Deployment)

### Why Railway?
- Simple Docker deployment
- Custom domains
- Auto-scaling

### Prerequisites
- Railway account
- Docker knowledge (optional)

### Deployment Steps

**1. Create `Dockerfile`**
```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 7860

CMD ["python", "app.py"]
```

**2. Deploy to Railway**
```bash
# Install Railway CLI
npm install -g @railway/cli

# Login
railway login

# Deploy
railway init
railway up
```

**Cost**: ~$5/month

---

## 🎯 Render (Free Tier Available)

### Deployment Steps

1. Push code to GitHub
2. Go to [Render Dashboard](https://dashboard.render.com/)
3. New → Web Service
4. Connect GitHub repository
5. Configure:
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `python app.py`
6. Deploy

**Free Tier Limitations**:
- Spins down after 15 min inactivity
- Cold start takes ~30 seconds

---

## ☁️ AWS/GCP (Production Scale)

### AWS (EC2 + Elastic Beanstalk)

**1. Package Application**
```bash
zip -r app.zip app.py requirements.txt
```

**2. Deploy to Elastic Beanstalk**
```bash
eb init -p python-3.9 text-summarization
eb create production-env
eb deploy
```

**Cost**: ~$10-50/month depending on instance

---

### GCP (Cloud Run)

**1. Create `Dockerfile`**
```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["python", "app.py"]
```

**2. Deploy**
```bash
gcloud builds submit --tag gcr.io/PROJECT_ID/text-summarization
gcloud run deploy --image gcr.io/PROJECT_ID/text-summarization
```

**Cost**: Pay per request (~$0.40/million requests)

---

## 🔐 Environment Variables in Production

### HuggingFace Spaces
```bash
# In Space Settings → Variables
HF_TOKEN=hf_your_token
```

### Railway/Render
```bash
# In dashboard, add environment variable:
HF_TOKEN=hf_your_token
CACHE_DIR=/app/cache
```

### Docker
```dockerfile
# In Dockerfile
ENV HF_TOKEN=$HF_TOKEN
```

---

## 📊 Monitoring & Analytics

### HuggingFace Spaces
- Built-in analytics (space settings)
- Request logs
- Resource usage

### Custom Logging
```python
import logging

logging.basicConfig(level=logging.INFO)
logger = logging.getLogger(__name__)

def summarize(text, model):
    logger.info(f"Request: model={model}, text_length={len(text)}")
    # ... process
    logger.info(f"Success: summary_length={len(summary)}")
```

---

## 🚀 Performance Tips

### 1. Model Optimization
```python
# Use smaller models for free tier
if os.environ.get('FREE_TIER'):
    DEFAULT_MODEL = "t5-small"
else:
    DEFAULT_MODEL = "facebook/bart-large-cnn"
```

### 2. Caching
```python
# Persistent cache across restarts
CACHE_DIR = "/persistent/cache"  # Mount persistent volume
```

### 3. Request Queuing
```python
# Gradio built-in queue
interface.queue(concurrency_count=3)
interface.launch()
```

---

## ✅ Deployment Checklist

Before going live:

- [ ] Test locally with `python app.py`
- [ ] Verify all dependencies in `requirements.txt`
- [ ] Set environment variables
- [ ] Test on different browsers
- [ ] Check mobile responsiveness
- [ ] Set up error logging
- [ ] Add analytics (optional)
- [ ] Create demo video/screenshots
- [ ] Update README with live URL
- [ ] Test all export formats

---

## 🐛 Common Deployment Issues

### 1. "No module named 'X'"
**Fix**: Add missing package to `requirements.txt`

### 2. "Out of memory"
**Fix**: Use smaller model or upgrade plan

### 3. "Port already in use"
**Fix**: Use `os.environ.get('PORT', 7860)`

### 4. "Model download timeout"
**Fix**: Pre-download models in Dockerfile

---

## 📞 Support

- **HuggingFace**: [Community Forum](https://discuss.huggingface.co/)
- **Streamlit**: [Forum](https://discuss.streamlit.io/)
- **Railway**: [Discord](https://discord.gg/railway)
- **Render**: [Docs](https://render.com/docs)

---

**Ready to Deploy?** Start with HuggingFace Spaces for easiest experience!

**Need Help?** Check [SETUP.md](../SETUP.md) or [README.md](../README.md)
