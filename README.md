# Video AI Summarizer Agent 📽️

An intelligent Streamlit application that analyzes video content using **Google Gemini 2.0 Flash** and **phidata** agents. Upload any video and get AI-powered insights, summaries, and answers to your questions.

## Project Overview

### What It Does
- 🎬 Upload video files (MP4, MOV, AVI)
- 🤖 Analyze video content using Google Gemini 2.0 Flash multimodal model
- 🔍 Ask custom questions about video content
- 🌐 Supplement analysis with web research (DuckDuckGo)
- 📝 Get detailed, actionable insights

### Key Features
- ✅ **Multimodal AI** - Gemini 2.0 Flash understands both video and text
- ✅ **Web-Enhanced Analysis** - Combines video insights with web search
- ✅ **User-Friendly UI** - Streamlit web interface
- ✅ **Real-time Processing** - See results as they're generated
- ✅ **Video Preview** - Built-in video player
- ✅ **Flexible Queries** - Ask anything about the video

---

## Use Cases

- 📺 **Video Summarization** - Get quick summaries of long videos
- 🎓 **Educational Content** - Extract key learnings from lectures
- 📊 **Business Analysis** - Analyze presentations and meetings
- 🎨 **Creative Review** - Get feedback on video projects
- 📰 **News Analysis** - Understand news reports and updates
- 🎥 **Content Verification** - Fact-check video claims with web research

---

## Prerequisites

- **Python 3.8+**
- **Google Gemini API Key** (free tier available)
  - Get it: https://aistudio.google.com/apikey
- **Internet connection** (for Google API and video processing)
- **Streamlit** and dependencies

---

## Setup Instructions

### Step 1: Install Dependencies

From the project directory:

```cmd
pip install -r requirements.txt
```

Or install manually:

```cmd
pip install streamlit phidata google-generativeai python-dotenv duckduckgo-search
```

### Step 2: Get Google Gemini API Key

1. Go to **https://aistudio.google.com/apikey**
2. Click "Create API Key"
3. Copy the API key

### Step 3: Set Up Environment Variables

Create a `.env` file in the `Video_Suammarizer/` folder:

```
GOOGLE_API_KEY=your_google_api_key_here
```

### Step 4: Run the Application

```cmd
cd Video_Suammarizer
streamlit run app.py
```

Your browser will open to: **http://localhost:8501**

---

## How to Use

### Basic Workflow

1. **Upload a Video**
   - Click "Upload a video file"
   - Select a video file (MP4, MOV, or AVI)
   - Supported formats: MP4, MOV, AVI

2. **Preview the Video**
   - The video player shows your uploaded file
   - You can play, pause, and seek through the video

3. **Ask a Question**
   - Type your question in the text area
   - Examples:
     - "Summarize this video in 3 bullet points"
     - "What are the main topics discussed?"
     - "Extract all the key statistics mentioned"
     - "Fact-check the claims made in this video"
     - "What's the sentiment and tone of this video?"

4. **Click "Analyze Video"**
   - The AI processes your video
   - It may take 10-60 seconds depending on video length

5. **View Results**
   - Read the detailed analysis
   - Results include insights from the video + web research

### Example Queries

**For Educational Videos:**
- "Extract the main learning objectives"
- "List all formulas and definitions mentioned"
- "Create a study guide from this video"

**For Business Videos:**
- "Summarize the key business metrics"
- "What decisions or announcements were made?"
- "Extract action items and deadlines"

**For News/Documentary:**
- "What are the main claims and supporting evidence?"
- "List the key people and organizations mentioned"
- "Fact-check the statistics presented"

**For Creative Content:**
- "Analyze the cinematography and visual style"
- "Describe the narrative structure"
- "What emotions does this video evoke?"

---

## How It Works (Technical Overview)

### Architecture Flow

```
Video File (uploaded)
    ↓
Google Cloud Storage (temporary)
    ↓
Gemini 2.0 Flash Model (multimodal analysis)
    ↓
DuckDuckGo Web Search (supplementary research)
    ↓
phidata Agent (orchestration)
    ↓
Markdown Response (Streamlit UI)
```

### Key Components

1. **Streamlit UI**
   - File uploader for video files
   - Video preview player
   - Text area for user queries
   - Results display

2. **Google Gemini 2.0 Flash**
   - State-of-the-art multimodal model
   - Understands video, audio, and text
   - Fast processing (optimized for real-time analysis)

3. **phidata Agent**
   - Orchestrates the AI workflow
   - Manages tools (DuckDuckGo, Gemini)
   - Generates structured prompts

4. **DuckDuckGo Search**
   - Supplements video analysis with web research
   - Helps verify claims and find additional context
   - No API key needed

---

## Project Structure

```
Video_Suammarizer/
├── app.py                 # Main Streamlit application
├── requirements.txt       # Python dependencies
├── .env                   # Environment variables (create locally)
└── README.md             # This file
```

### File Details

**app.py** - Main Application
- Streamlit page configuration
- Video uploader component
- AI agent initialization
- Video processing and analysis
- Results display

**requirements.txt** - Dependencies
- streamlit (UI framework)
- phidata (AI agent framework)
- google-generativeai (Gemini API)
- duckduckgo-search (web search)
- python-dotenv (environment variables)

---

## Features in Detail

### Video Upload
- Accepts: MP4, MOV, AVI formats
- File size: Limited by browser and Google API
- Preview: Built-in player to watch before analysis

### AI Analysis
- **Model**: Google Gemini 2.0 Flash Exp
- **Capabilities**: Understands video content, transcribes audio, analyzes visuals
- **Speed**: Optimized for quick analysis
- **Accuracy**: State-of-the-art multimodal understanding

### Web Research Integration
- Supplements video insights with web data
- Fact-checks claims automatically
- Finds additional context and related information

### User Query System
- Free-form text input
- Flexible question types
- Custom analysis requests

---

## Troubleshooting

### Issue: `ModuleNotFoundError: No module named 'streamlit'`
**Solution:** Install requirements:
```cmd
pip install -r requirements.txt
```

### Issue: `GOOGLE_API_KEY not set`
**Solution:** 
1. Create `.env` file in `Video_Suammarizer/` folder
2. Add: `GOOGLE_API_KEY=your_key_here`
3. Get key from: https://aistudio.google.com/apikey

### Issue: "Error: The resource is not ready"
**Solution:** This means Google is still processing the video. The app retries automatically, but you may need to wait longer for large videos.

### Issue: Video upload fails
**Solution:**
- Check file format (must be MP4, MOV, or AVI)
- Ensure file size is reasonable (< 100MB recommended)
- Check internet connection
- Try a shorter video first

### Issue: "An error occurred during the analysis"
**Solution:**
- Verify your Google API key is valid
- Check you have credits in your Google Cloud account
- Ensure video is not corrupted
- Try with a different video
- Check terminal for detailed error messages

### Issue: Streamlit app won't start
**Solution:**
```cmd
# Reinstall Streamlit
pip install --upgrade streamlit

# Try running with explicit host/port
streamlit run app.py --server.port 8501
```

---

## Customization

### Change the Gemini Model

Edit `app.py`, line ~35:

```python
model=Gemini(id="gemini-2.0-flash-exp"),  # Change to another model
```

Available models:
- `gemini-2.0-flash-exp` (recommended, fastest)
- `gemini-1.5-pro` (more capable, slower)
- `gemini-1.5-flash` (balanced)

### Add More Tools

Add additional tools to the agent in `app.py`:

```python
tools=[
    DuckDuckGo(),
    # Add more tools here
]
```

### Change Supported Video Formats

Edit line ~49 in `app.py`:

```python
video_file = st.file_uploader(
    "Upload a video file", 
    type=['mp4', 'mov', 'avi', 'mkv', 'webm'],  # Add formats
)
```

### Customize Analysis Prompt

Edit the `analysis_prompt` in `app.py` (around line ~71):

```python
analysis_prompt = (
    f"""
    Your custom instructions here...
    {user_query}
    """
)
```

---

## Limitations & Considerations

- **Video Processing Time**: Larger videos take longer (10-60 seconds typical)
- **API Limits**: Google Gemini has rate limits on free tier
- **File Size**: Extremely large files may timeout
- **Privacy**: Videos are temporarily uploaded to Google's servers
- **Audio**: Works best with clear audio (transcription happens automatically)
- **Accuracy**: AI analysis may have errors - always verify important information

---

## Performance Tips

1. **Shorter Videos** - Upload clips instead of full videos (< 10 minutes ideal)
2. **Clear Audio** - Videos with clear audio produce better transcriptions
3. **Good Lighting** - Well-lit videos are easier to analyze visually
4. **Specific Queries** - Ask detailed questions for better results
5. **Web Context** - Enable DuckDuckGo search for fact-checking

---

## API Costs

- **Google Gemini 2.0 Flash**: Free tier available
  - Visit: https://aistudio.google.com/apikey
  - Monitor usage: https://console.cloud.google.com/

---

## Next Steps / Enhancements

- [ ] Support for YouTube video URLs (not just file upload)
- [ ] Batch processing (analyze multiple videos)
- [ ] Export results to PDF
- [ ] Save analysis history
- [ ] Custom AI instructions/prompts
- [ ] Support for different languages
- [ ] Audio extraction and transcription only
- [ ] Sentiment analysis dashboard
- [ ] Video chapters/timestamps in analysis
- [ ] Integration with cloud storage (Google Drive, etc.)

---

## Security & Privacy

- **API Keys**: Keep your `.env` file private, add to `.gitignore`
- **Video Data**: Videos are temporarily processed by Google
- **No Storage**: Analyzed videos are not permanently stored by this app
- **Local Processing**: Video file handling is done locally, not saved

---

## Command Reference

```cmd
# Install dependencies
pip install -r requirements.txt

# Run the application
streamlit run app.py

# Run with custom port
streamlit run app.py --server.port 8502

# Run in development mode
streamlit run app.py --logger.level=debug
```

---

## Dependencies Summary

| Package | Purpose |
|---------|---------|
| streamlit | Web UI framework |
| phidata | AI agent framework |
| google-generativeai | Google Gemini API client |
| duckduckgo-search | Web search tool |
| python-dotenv | Environment variable management |

---

## Support & Resources

- **Google Gemini Docs**: https://ai.google.dev/docs
- **Streamlit Docs**: https://docs.streamlit.io
- **phidata Docs**: https://docs.phidata.com
- **Google AI Studio**: https://aistudio.google.com

---

## License & Notes

- This project uses Google's free Gemini API tier
- Respect Google's terms of service and usage limits
- Keep API keys secure and never commit them to version control
- Be mindful of video content privacy

---

## Quick Start Summary

```cmd
# 1. Install
pip install -r requirements.txt

# 2. Set up .env with GOOGLE_API_KEY

# 3. Run
streamlit run app.py

# 4. Open browser to http://localhost:8501

# 5. Upload video and ask questions!
```

---

**Last Updated:** November 12, 2025  
**Status:** ✅ Ready to Use  
**Model:** Google Gemini 2.0 Flash Exp  
**Framework:** Streamlit + phidata
