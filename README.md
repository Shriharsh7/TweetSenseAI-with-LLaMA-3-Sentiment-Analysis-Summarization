
# TweetSenseAI: Sentiment & Summary Analysis with LLaMA-3

A Python-based tool that fetches tweets using the X API and analyzes them with LLaMA-3-8B for sentiment and summarization, built to run on Google Colab with a GPU. The project provides insights into the emotional tone and key points of tweets, making it valuable for social media analysis, marketing, or research.

## Live Demo
You can access the project notebook here: [TweetSenseAI Notebook](https://github.com/Shriharsh7/TweetSenseAI-with-LLaMA-3-Sentiment-Analysis-Summarization/blob/main/TweetSenseAI.ipynb)

## Project Overview
This project was developed to analyze tweets using advanced natural language processing techniques with the following requirements:
- **Input**: Fetch tweet text using the X API v2 based on a tweet URL.
- **Functionality**: Perform sentiment analysis and generate concise summaries using LLaMA-3-8B.  
- **Output**: Provide sentiment (e.g., positive, negative, neutral, happy, sad, angry, excited) and a one-sentence summary for each tweet.
- **Deliverables**: A functional notebook on Google Colab, source code on GitHub, and clear setup instructions.
- **Environment**: Optimized to run on Google Colab’s free Tesla T4 GPU.

The tool leverages LLaMA-3-8B for both sentiment detection and summarization, running efficiently on Colab with GPU acceleration. It’s designed to handle tweet analysis securely and provide nuanced emotional insights beyond basic sentiment categories.

## Implementation Details
The tool is built using Python and integrates several libraries for API interaction, model inference, and GPU optimization. Here’s a breakdown of the implementation:

### Tech Stack
- **API Interaction**: `requests` for fetching tweets via the X API v2.
- **Model Inference**: `transformers` and `torch` for loading and running LLaMA-3-8B.
- **Quantization**: `bitsandbytes` for 8-bit quantization to fit LLaMA-3-8B on a Tesla T4 GPU.
- **Token Management**: `google.colab.userdata` for secure token retrieval from Colab Secrets.
- **Environment**: Google Colab with a Tesla T4 GPU (free tier).

### Workflow
1. **Tweet Retrieval**:
   - Users input a tweet URL.
   - The tool extracts the username and post ID, fetching the tweet text via the X API v2.
2. **Sentiment Analysis**:
   - LLaMA-3-8B analyzes the tweet to detect sentiments from an expanded list (positive, negative, neutral, happy, sad, angry, excited).
3. **Summarization**:
   - LLaMA-3-8B generates a one-sentence summary capturing the tweet’s essence.
4. **Output**:
   - Displays the username, post ID, tweet text, sentiment, and summary.

### Key Features
- **Tweet Retrieval**: Fetches tweet text by URL using the X API v2.
- **Expanded Sentiments**: Detects a wide range of emotions (positive, negative, neutral, happy, sad, angry, excited) using LLaMA-3-8B.
- **Summarization**: Produces concise one-sentence summaries of tweets.
- **GPU Efficiency**: Runs on Colab’s Tesla T4 GPU with 8-bit quantization to optimize memory usage.
- **Secure Token Management**: Stores API tokens (Hugging Face and X) in Colab Secrets.

## What We Tried and Discarded
During development, several approaches were explored to enhance functionality and performance, but some were discarded due to complexity, inconsistency, or resource constraints:

1. **Basic Sentiment Categories**:
   - **What We Tried**: Started with positive, negative, and neutral sentiments.
   - **Why Discarded**: Too limiting for diverse tweets; expanded to seven categories after testing LLaMA’s nuance detection.
   - **Lesson Learned**: Granular sentiments offer richer insights into tweet emotions.

2. **Hardcoded Tokens**:
   - **What We Tried**: Initially hardcoded API tokens in the script.
   - **Why Discarded**: Posed a security risk; switched to Colab Secrets.
   - **Lesson Learned**: Secure token handling is critical for safety.

3. **Multiple Model Loads**:
   - **What We Tried**: Loaded the model and tokenizer for each analysis.
   - **Why Discarded**: Increased runtime overhead; switched to a single load with global variables.
   - **Lesson Learned**: Optimize resource usage in GPU-constrained environments.

## Engineering Decisions
Key engineering choices were made to ensure functionality, efficiency, and security within Colab’s constraints:

1. **Model Selection**:
   - Chose LLaMA-3-8B-Instruct for its strong performance in NLP tasks over smaller models like Flan-T5.
   - **Rationale**: Ensures high-quality sentiment analysis and summarization.

2. **Quantization**:
   - Applied 8-bit quantization via `BitsAndBytesConfig` to fit LLaMA-3-8B on a Tesla T4 GPU.
   - **Rationale**: Balances performance and accessibility on free hardware.

3. **Sentiment Expansion**:
   - Expanded to seven sentiment categories beyond basic ones.
   - **Rationale**: Provides deeper emotional insights.

4. **Secure Token Handling**:
   - Stored tokens in Colab Secrets, fetched with `userdata.get()`.
   - **Rationale**: Prevents exposure of sensitive data.

5. **Single Model Load**:
   - Used global variables to load LLaMA-3-8B once.
   - **Rationale**: Reduces runtime overhead in Colab.

## Testing Observations
- **Sentiment Accuracy**: LLaMA-3-8B excels at detecting nuanced emotions with clear cues.
- **Summary Quality**: Summaries are concise and capture key points effectively.
- **GPU Efficiency**: 8-bit quantization enables smooth operation on a Tesla T4 GPU.
- **Token Security**: Colab Secrets ensure secure and reliable token access.

## Future Improvements
With additional time and resources, the tool could be enhanced in several ways:

1. **More Sentiment Categories**:
   - Add sentiments like "sarcastic" or "playful" with prompt engineering.
   - **Rationale**: Further enrich emotional analysis.

2. **Multi-Tweet Analysis**:
   - Extend to analyze multiple tweets in batch for users or hashtags.
   - **Rationale**: Provide broader insights.

3. **Interactive Interface**:
   - Deploy as a web app (e.g., Hugging Face Spaces) with a smaller model.
   - **Rationale**: Improve accessibility, though GPU hosting would be needed.

4. **Error Handling**:
   - Enhance handling for X API rate limits and private/deleted tweets.
   - **Rationale**: Increase robustness.

5. **Model Upgrade**:
   - Test newer models like Claude Sonnet or Grok fun mode for improved performance.
   - **Rationale**: Leverage LLM advancements.

## Setup Instructions
### Running in Colab
1. Open the notebook in Colab:  
   [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/Shriharsh7/TweetSenseAI-with-LLaMA-3-Sentiment-Analysis-Summarization/blob/main/TweetSenseAI.ipynb)
2. Switch to a GPU runtime (`Runtime > Change runtime type > GPU`).
3. Install dependencies:
   ```bash
   !pip install transformers torch bitsandbytes requests
4. Add your HF_TOKEN (Hugging Face) and BEARER_TOKEN (X API) to Colab Secrets (Secrets tab in the sidebar).
5. Run all cells to analyze a tweet.

## Sample Output 
**Username:** BillGates   
**Post ID:** 1902597037935497324    
**Tweet Text:** I had a very productive meeting with @jpnadda where we discussed India’s impressive progress in public health. India’s commitment to eliminating infectious diseases, advancing maternal and child healthcare, and leveraging digital health platforms and AI, is creating healthier… [https://t.co/DPV5q1XamX](https://t.co/DPV5q1XamX) [https://t.co/ITp6Oynlaq](https://t.co/ITp6Oynlaq)   
### LLaMA Model Analysis
- **GPU:** Tesla T4
- **Sentiment:** positive
- **Summary:** The author had a productive meeting with @jpnadda to discuss India's progress in public health, specifically their efforts to eliminate infectious diseases and improve maternal and child healthcare.

## Acknowledgments
- Built with LLaMA-3-8B-Instruct by Meta AI.
- Uses the X API v2 for tweet retrieval.
- Thanks to Grok for helping with model quantization

## Conclusion

TweetSenseAI showcases the power of large language models in social media analysis. By integrating the X API with LLaMA-3-8B, it delivers nuanced sentiment analysis and concise summaries, optimized for Google Colab’s free GPU tier. The development process involved balancing model performance, memory constraints, and security, with several approaches tested and refined. Future enhancements could include multi-tweet analysis and a web interface, further expanding its utility. This project highlights my skills in NLP, API integration, and AI optimization under resource constraints.
