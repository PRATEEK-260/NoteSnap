<<<<<<< HEAD
# 📝 NoteSnap

<div align="center">

![NoteSnap Logo](https://img.shields.io/badge/📝-NoteSnap-blue?style=for-the-badge)

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![Streamlit](https://img.shields.io/badge/Streamlit-FF4B4B?style=flat&logo=streamlit&logoColor=white)](https://streamlit.io/)
[![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)](https://www.docker.com/)
[![Transformers](https://img.shields.io/badge/🤗%20Transformers-FFD21E?style=flat)](https://huggingface.co/transformers/)

[![GitHub stars](https://img.shields.io/github/stars/PRATEEK-260/NoteSnap?style=social)](https://github.com/PRATEEK-260/NoteSnap/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/PRATEEK-260/NoteSnap?style=social)](https://github.com/PRATEEK-260/NoteSnap/network/members)
[![GitHub issues](https://img.shields.io/github/issues/PRATEEK-260/NoteSnap)](https://github.com/PRATEEK-260/NoteSnap/issues)

</div>

A powerful web application that transforms lengthy documents and notes into concise, bullet-point summaries using state-of-the-art AI models.

---

## 📋 Table of Contents

- [✨ Features](#-features)
- [🚀 Quick Start](#-quick-start)
  - [Option 1: Docker (Recommended)](#option-1-docker-recommended)
  - [Option 2: Local Installation](#option-2-local-installation)
- [📖 Usage Guide](#-usage-guide)
- [🖼️ Screenshots](#️-screenshots)
- [🛠️ Technical Details](#️-technical-details)
- [🐳 Docker Deployment](#-docker-deployment)
- [🔧 Configuration](#-configuration)
- [🚨 Troubleshooting](#-troubleshooting)
- [🤝 Contributing](#-contributing)
- [📄 License](#-license)
- [🙏 Acknowledgments](#-acknowledgments)
- [📞 Support](#-support)

---

## ✨ Features

- **PDF Processing**: Upload PDF files and extract text content automatically
- **Direct Text Input**: Paste text content directly for immediate summarization
- **AI-Powered Summarization**: Uses Hugging Face Transformers (BART, T5) for high-quality summaries
- **Bullet-Point Format**: Clean, readable bullet-point summaries
- **Multiple AI Models**: Choose from different pre-trained models
- **Customizable Length**: Adjust summary length (Short, Medium, Long)
- **Progress Tracking**: Real-time progress indicators during processing
- **Download Summaries**: Save generated summaries as text files
- **Statistics**: View compression ratios and word counts
- **Error Handling**: Comprehensive error handling and user feedback

## 🚀 Quick Start

### 🌐 Try Online (Fastest)
**[🚀 Live Demo on Hugging Face Spaces](https://huggingface.co/spaces/PRATEEK-260/NoteSnap)**
- No installation required
- Instant access in your browser
- Full functionality available

### Option 1: Docker (Recommended)

#### Prerequisites
- Docker and Docker Compose installed
- Internet connection (for downloading AI models)

#### Using Docker Compose (Easiest)
```bash
# Clone the repository
git clone https://github.com/PRATEEK-260/NoteSnap.git
cd NoteSnap

# Start the application
docker-compose up -d

# Access the application at http://localhost:8501
```

#### Using Docker Scripts
```bash
# Build the Docker image
./docker-build.sh

# Run the container
./docker-run.sh

# For development with live code reloading
./docker-dev.sh
```

#### Manual Docker Commands
```bash
# Build the image
docker build -t notesnap .

# Run the container
docker run -p 8501:8501 notesnap
```

### Option 2: Local Installation

#### Prerequisites
- Python 3.8 or higher
- pip (Python package installer)
- Internet connection (for downloading AI models)

#### Installation Steps
1. **Clone the repository**
   ```bash
   git clone https://github.com/PRATEEK-260/NoteSnap.git
   cd NoteSnap
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Run the application**
   ```bash
   streamlit run app.py
   ```

4. **Open your browser**
   - The application will automatically open at `http://localhost:8501`
   - If it doesn't open automatically, navigate to the URL manually

## 📖 Usage Guide

### PDF Summarization

1. **Upload PDF**: Click on the "📄 PDF Upload" tab
2. **Select File**: Choose a PDF file (max 10MB)
3. **Process**: Click "📖 Extract & Summarize PDF"
4. **Review**: View the extracted text preview
5. **Get Summary**: The AI will generate a bullet-point summary
6. **Download**: Save the summary using the download button

### Text Summarization

1. **Input Text**: Click on the "📝 Text Input" tab
2. **Paste Content**: Enter or paste your text (minimum 100 characters)
3. **Summarize**: Click "🚀 Summarize Text"
4. **Review**: View the generated summary
5. **Download**: Save the summary as needed

### Settings

- **AI Model**: Choose from BART (recommended), T5, or DistilBART
- **Summary Length**: Select Short, Medium, or Long summaries
- **Statistics**: View word counts and compression ratios

## 🛠️ Technical Details

### Architecture

```
NoteSnap/
├── app.py                 # Main Streamlit application
├── modules/
│   ├── __init__.py
│   ├── pdf_processor.py   # PDF text extraction
│   ├── text_summarizer.py # AI summarization
│   └── utils.py          # Utility functions
├── requirements.txt       # Python dependencies
└── README.md             # This file
```

### AI Models

- **BART (facebook/bart-large-cnn)**: Best quality, recommended for most use cases
- **T5 Small**: Faster processing, good for shorter texts
- **DistilBART**: Balanced performance and speed

### Dependencies

- **Streamlit**: Web application framework
- **Transformers**: Hugging Face AI models
- **PyTorch**: Deep learning framework
- **PyPDF2**: PDF text extraction
- **Additional utilities**: See `requirements.txt`

## 🔧 Configuration

### Model Selection

You can change the default model by modifying the `TextSummarizer` initialization in `app.py`:

```python
text_summarizer = TextSummarizer(model_name="your-preferred-model")
```

### Summary Length

Adjust default summary lengths in `modules/text_summarizer.py`:

```python
self.min_summary_length = 50  # Minimum words
self.max_summary_length = 300  # Maximum words
```

### File Size Limits

Modify PDF file size limits in `modules/pdf_processor.py`:

```python
self.max_file_size = 10 * 1024 * 1024  # 10MB
```

## 🚨 Troubleshooting

### Common Issues

1. **Model Loading Errors**
   - Ensure stable internet connection
   - Check available disk space (models can be 1-2GB)
   - Try switching to a smaller model (T5 Small or DistilBART)

2. **PDF Processing Issues**
   - Ensure PDF is not encrypted
   - Check if PDF contains readable text (not just images)
   - Try with a smaller PDF file

3. **Memory Errors**
   - Reduce text length
   - Close other applications
   - Try using CPU instead of GPU

4. **Slow Performance**
   - Use GPU if available
   - Choose smaller models for faster processing
   - Process shorter text chunks

### Error Messages

- **"Text is too short"**: Minimum 100 characters required
- **"No readable text found"**: PDF may contain only images
- **"Model loading error"**: Check internet connection
- **"Out of memory"**: Reduce text length or restart application

## 🎯 Best Practices

### For Best Results

1. **Text Quality**: Use well-formatted, coherent text
2. **Length**: Optimal text length is 500-5000 words
3. **Content**: Works best with structured content (articles, reports, notes)
4. **Model Choice**: Use BART for academic/formal content, T5 for general text

### Performance Tips

1. **GPU Usage**: Enable CUDA for faster processing
2. **Batch Processing**: Process multiple documents separately
3. **Model Caching**: Models are cached after first load
4. **Text Preprocessing**: Clean text improves summary quality

## 🖼️ Screenshots

<div align="center">

### Main Interface
![Main Interface](Screenshots/Main%20interface.png)
*Clean and intuitive interface with PDF upload and text input options*

### PDF Processing
![PDF Processing](Screenshots/pdf%20processing.png)
*Real-time PDF processing with progress indicators*

### Summary Results
![Summary Results](Screenshots/Summery%20Result.png)
*Bullet-point summaries with statistics and download options*

### Settings Panel
![Settings Panel](Screenshots/settings%20panel.png)
*Customizable AI model selection and summary length options*

</div>

## 🎥 Demo

🚀 **[Live Demo](https://huggingface.co/spaces/PRATEEK-260/NoteSnap)** - Try it now on Hugging Face Spaces!

## 📄 License

This project is open source and available under the MIT License.

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues, feature requests, or pull requests.

## 🐳 Docker Deployment

### Production Deployment

For production deployment, use the standard Docker Compose configuration:

```bash
# Start in production mode
docker-compose up -d

# View logs
docker-compose logs -f

# Stop the application
docker-compose down

# Update the application
docker-compose pull
docker-compose up -d
```

### Development Mode

For development with live code reloading:

```bash
# Start development environment
docker-compose -f docker-compose.dev.yml up

# Or use the convenience script
./docker-dev.sh
```

### Docker Configuration

#### Environment Variables
- `STREAMLIT_SERVER_PORT`: Port for the application (default: 8501)
- `TRANSFORMERS_CACHE`: Cache directory for AI models
- `MAX_FILE_SIZE_MB`: Maximum PDF file size (default: 10MB)

#### Volumes
- `model_cache`: Persistent storage for downloaded AI models
- `logs`: Application logs
- `uploads`: Temporary file storage (optional)

#### Resource Limits
- Memory: 4GB limit, 2GB reserved
- CPU: 2 cores limit, 1 core reserved

### Docker Troubleshooting

1. **Container won't start**: Check logs with `docker-compose logs`
2. **Out of memory**: Increase Docker memory limits
3. **Model download fails**: Ensure internet connectivity
4. **Permission issues**: Check file ownership and Docker user settings

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

### 🌟 Ways to Contribute

- ⭐ **Star this repository** if you find it useful
- 🐛 **Report bugs** by opening an [issue](https://github.com/PRATEEK-260/NoteSnap/issues)
- 💡 **Suggest features** or improvements
- 📖 **Improve documentation**
- 🔧 **Submit pull requests** with bug fixes or new features

### 🚀 Getting Started

1. **Fork the repository**
   ```bash
   # Click the "Fork" button on GitHub, then:
   git clone https://github.com/YOUR-USERNAME/NoteSnap.git
   cd NoteSnap
   ```

2. **Create a feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```

3. **Make your changes**
   - Follow the existing code style
   - Add tests for new features
   - Update documentation as needed

4. **Test your changes**
   ```bash
   # Run basic tests
   python test_basic.py

   # Test Docker build
   ./docker-test.sh
   ```

5. **Submit a pull request**
   ```bash
   git add .
   git commit -m "Add amazing feature"
   git push origin feature/amazing-feature
   ```

### 📋 Development Guidelines

- **Code Style**: Follow PEP 8 for Python code
- **Documentation**: Update README.md for new features
- **Testing**: Add tests for new functionality
- **Docker**: Ensure Docker compatibility
- **Dependencies**: Keep requirements.txt updated

### 🐛 Reporting Issues

When reporting issues, please include:

- **Environment details** (OS, Python version, Docker version)
- **Steps to reproduce** the issue
- **Expected vs actual behavior**
- **Error messages** or logs
- **Screenshots** if applicable

[**Report an Issue →**](https://github.com/PRATEEK-260/NoteSnap/issues/new)

### 💬 Discussions

Join our community discussions:

- [**GitHub Discussions**](https://github.com/PRATEEK-260/NoteSnap/discussions) - General questions and ideas
- [**Issues**](https://github.com/PRATEEK-260/NoteSnap/issues) - Bug reports and feature requests

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

### 🛠️ Built With

- [**Streamlit**](https://streamlit.io/) - Web application framework
- [**Hugging Face Transformers**](https://huggingface.co/transformers/) - AI/ML models
- [**PyTorch**](https://pytorch.org/) - Deep learning framework
- [**PyPDF2**](https://pypdf2.readthedocs.io/) - PDF processing
- [**Docker**](https://www.docker.com/) - Containerization

### 🎯 Inspiration

- Inspired by the need for efficient document summarization
- Built to help students, researchers, and professionals save time
- Leverages state-of-the-art AI models for high-quality summaries

### 🤖 AI Models

Special thanks to the teams behind these amazing models:
- [**BART**](https://huggingface.co/facebook/bart-large-cnn) by Facebook AI
- [**T5**](https://huggingface.co/t5-small) by Google Research
- [**DistilBART**](https://huggingface.co/sshleifer/distilbart-cnn-12-6) by Sam Shleifer

## 📞 Support

If you encounter any issues or have questions:

### 🔍 Self-Help Resources

1. 📖 Check the [troubleshooting section](#-troubleshooting) above
2. 🐛 Review error messages for specific guidance
3. 📦 Ensure all dependencies are properly installed
4. 🔄 Try with different models or settings
5. 🐳 For Docker issues, check container logs: `docker-compose logs`

### 💬 Get Help

- 🐛 **Bug Reports**: [Open an Issue](https://github.com/PRATEEK-260/NoteSnap/issues/new)
- 💡 **Feature Requests**: [Start a Discussion](https://github.com/PRATEEK-260/NoteSnap/discussions)

---

<div align="center">

**Made with ❤️ by [PRATEEK-260](https://github.com/PRATEEK-260)**

**Happy Summarizing! 📝✨**

[![GitHub](https://img.shields.io/badge/GitHub-PRATEEK--260-181717?style=flat&logo=github)](https://github.com/PRATEEK-260)

</div>
=======
# NoteSnap
>>>>>>> 9b4f2dab9437daaefabf059cd647a5761c93c197
