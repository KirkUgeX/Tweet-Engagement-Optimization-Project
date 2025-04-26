# 🧐 Tweet Engagement Optimization Project

## 🚀 Overview  
We built an NLP system that predicts and boosts tweet engagement (likes, retweets, reach) by analyzing the text and generating improved tweet versions using a fine-tuned language model.

## 🎯 Objectives
- Predict engagement based **only on tweet text**  
- Provide suggestions to rewrite tweets for better performance  
- Generate more engaging versions of tweets using a text generation model

## 📊 Dataset
We used the **“Tweets and User Engagement”** dataset from Kaggle, which includes:
- `text`: tweet content  
- `likes`, `retweetCount`, `reach`: engagement metrics  
- `sentiment`, `clout`: user sentiment & influence  
- `weekday`, `hour`: time of publication  

> ❗ We **excluded sentiment and clout**, focusing only on **textual features** to study the direct impact of wording on engagement.

## 🧼 Data Processing
- Removed fake, empty, and very short tweets  
- Cleaned text: removed links, unnecessary emojis, special characters  
- Created a **custom dataset** of manually improved tweets paired with suggestions for fine-tuning the generation model  
- Added popular **emojis and hashtags** into the tokenizer to enhance generation quality  
- Limited max sequence length to **128 tokens** to preserve structure and key elements

## 🧠 Models Used  

### 🔹 Engagement Prediction
- **BERT + LightGBM** pipeline  
  - BERT was used to extract tweet embeddings  
  - LightGBM trained on top of embeddings to predict engagement  
  - Performance:  
    - R² = `0.134`  
    - MAE = `0.311`  
    - Accuracy within ±1 = `95.65%`

### 🔹 Tweet Generation
- **Flan-T5 (fine-tuned)**  
  - Fine-tuned on our manually curated dataset  
  - Generates improved tweets with better structure, engaging wording, CTA, emojis 😎, and hashtags #AI #NLP  
  - Tokenizer extended with custom emoji tokens 🛠️

## ✅ Results
Our system can:
- Predict how engaging a tweet will be based on its text  
- Rewrite tweets to increase user interaction  
- Work independently from user stats, sentiment, or time factors — pure text-based analysis

## 📌 Example
**Original:**  
> Just posted a blog update.  
**Generated:**  
> 🚀 Just dropped a fresh blog post! Check it out & let me know what you think 💬👇 #TechUpdate #Blog
