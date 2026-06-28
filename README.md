# 🚀 AI-Powered Portfolio - Raviteja B

A modern, modular portfolio website with integrated AI chatbot functionality. It now includes a GitHub Pages-friendly static homepage so the portfolio can be hosted for free on a username.github.io domain.

## ✨ Features

- **🤖 AI-Powered Chatbot**: Interactive assistant using Gemini and Groq APIs
- **📱 Responsive Design**: Works seamlessly on desktop and mobile
- **🎨 Modern UI**: Terminal-inspired design with smooth animations
- **⚡ Fast & Lightweight**: Optimized for performance
- **🔧 Modular Architecture**: Clean, maintainable codebase
- **📄 Resume Download**: Direct PDF download functionality

## 🏗️ Project Structure

```
PORTFOLIO/
├── app/                          # Main application package
│   ├── __init__.py              # Flask app factory
│   ├── api/                     # API routes
│   │   ├── __init__.py
│   │   ├── main_routes.py       # Main page & resume routes
│   │   └── routes.py            # Chat API routes
│   ├── config/                  # Configuration management
│   │   ├── __init__.py
│   │   └── settings.py          # App settings & environment config
│   ├── static/                  # Static assets
│   │   ├── css/
│   │   │   └── portfolio.css    # Main stylesheet
│   │   └── js/
│   │       └── portfolio.js     # Frontend JavaScript
│   ├── templates/               # HTML templates
│   │   └── portfolio.html       # Main portfolio template
│   └── utils/                   # Utility modules
│       ├── __init__.py
│       ├── ai_clients.py        # AI API management
│       └── resume_context.py    # Resume data & fallbacks
├── assets/                      # Static assets
│   └── Raviteja_B_AI_GenAI_Resume.pdf   # Resume file
├── venv/                        # Virtual environment
├── .env                         # Environment variables
├── requirements.txt             # Python dependencies
├── run.py                      # Main entry point
└── README.md                   # This file
```

## 🚀 Quick Start

### GitHub Pages deployment

1. Push this repository to GitHub.
2. Ensure the default branch is named `main`.
3. Open Settings → Pages in GitHub and select the `GitHub Actions` deployment source.
4. The site will be published at `https://your-username.github.io`.

The repository includes a static entry point at [index.html](index.html) and a Pages workflow in [.github/workflows/deploy-pages.yml](.github/workflows/deploy-pages.yml).

### Prerequisites

- Python 3.8+
- Virtual environment (recommended)

### Installation

1. **Clone & Navigate**
   ```bash
   cd PORTFOLIO
   ```

2. **Activate Virtual Environment**
   ```bash
   source venv/bin/activate  # Linux/Mac
   # or
   venv\Scripts\activate     # Windows
   ```

3. **Install Dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Configure Environment Variables**
   
   Create/update `.env` file:
   ```env
   GEMINI_API_KEY=your_gemini_api_key_here
   GROQ_API_KEY=your_groq_api_key_here
   FLASK_DEBUG=True
   FLASK_HOST=0.0.0.0
   FLASK_PORT=5000
   SECRET_KEY=your_secure_secret_key
   ```

   Notes:
   - `GEMINI_API_KEY` and `GROQ_API_KEY` are only used by the Flask backend for AI chat.
   - The GitHub Pages static deployment does not use these keys, because Pages cannot run Python server code.
   - If you want the AI assistant live, deploy the Flask app to a dynamic host (Railway, Render, Heroku, etc.) and set the same keys there.

5. **Update your resume file**
   - Replace `assets/Raviteja_B_AI_GenAI_Resume.pdf` with your new resume using the same filename.
   - If you want another path or filename, update the download link in `index.html` and `app/api/main_routes.py`.

6. **Run the Application**
   ```bash
   python run.py
   ```

6. **Access Portfolio**
   
   Open your browser and navigate to: `http://localhost:5000`

## 🔧 Configuration

### API Keys

The application supports multiple AI providers:

- **Gemini API**: Get your key from [Google AI Studio](https://makersuite.google.com/app/apikey)
- **Groq API**: Get your key from [Groq Console](https://console.groq.com/keys)

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `GEMINI_API_KEY` | Google Gemini API key | None |
| `GROQ_API_KEY` | Groq API key | None |
| `FLASK_DEBUG` | Enable debug mode | True |
| `FLASK_HOST` | Server host | 0.0.0.0 |
| `FLASK_PORT` | Server port | 5000 |

## 🏛️ Architecture

### Design Principles

- **Separation of Concerns**: Each module has a single responsibility
- **Dependency Injection**: Loose coupling between components
- **Configuration Management**: Centralized settings
- **Error Handling**: Graceful fallbacks and error recovery
- **Scalability**: Easy to extend and modify

### Key Components

1. **Flask App Factory** (`app/__init__.py`)
   - Creates and configures Flask application
   - Registers blueprints and extensions

2. **API Routes** (`app/api/`)
   - `main_routes.py`: Portfolio page and resume download
   - `routes.py`: Chat API endpoints

3. **AI Client Manager** (`app/utils/ai_clients.py`)
   - Manages multiple AI providers
   - Handles API failures and fallbacks
   - Model selection and optimization

4. **Configuration** (`app/config/settings.py`)
   - Environment-based configuration
   - Development/Production settings

## 🤖 AI Features

### Supported Models

- **Gemini 2.5 Flash** (Primary)
- **Gemini 2.5 Pro** (Fallback)
- **Groq Llama 3** (Secondary)

### Fallback System

1. Try Gemini API with multiple models
2. Fall back to Groq API
3. Use static responses as last resort

### Smart Responses

The AI assistant provides contextual responses about:
- Work experience and career progression
- Technical skills and expertise
- Projects and achievements
- Education and certifications

## 📱 Frontend Features

### Responsive Design

- **Desktop**: Full-featured terminal interface
- **Tablet**: Optimized layout and interactions
- **Mobile**: Touch-friendly compact design

### Interactive Elements

- **Floating Chat Button**: Always accessible AI assistant
- **Smooth Animations**: Professional transitions and effects
- **Terminal Theme**: Modern developer-inspired design
- **Resume Download**: One-click PDF download

## 🔒 Security

- Environment variable protection
- Input sanitization
- CORS configuration
- Error message sanitization

## 🚀 Deployment

### Local Development

```bash
python run.py
```

### Production Deployment

1. Set environment variables
2. Use production WSGI server (e.g., Gunicorn)
3. Configure reverse proxy (e.g., Nginx)
4. Set up SSL certificates

Example with Gunicorn:
```bash
gunicorn -w 4 -b 0.0.0.0:8000 "app:create_app()"
```

## 🛠️ Development

### Adding New Features

1. **API Routes**: Add to `app/api/routes.py`
2. **Frontend**: Update `app/templates/` and `app/static/`
3. **Configuration**: Modify `app/config/settings.py`
4. **Utilities**: Add to `app/utils/`

### Code Style

- Follow PEP 8 guidelines
- Use type hints where appropriate
- Document functions and classes
- Write descriptive commit messages

## 📊 Performance

- **Fast Loading**: Optimized CSS and JavaScript
- **Efficient AI**: Smart model selection and caching
- **Responsive**: Smooth interactions on all devices
- **Lightweight**: Minimal dependencies

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is for portfolio purposes. All rights reserved.

## 📞 Contact

- **Email**: ravitejab2209@gmail.com
- **LinkedIn**: [linkedin.com/in/ravitejab2209](https://linkedin.com/in/ravitejab2209)
- **GitHub**: [github.com/ravitejab2209](https://github.com/ravitejab2209)

---

**Built with ❤️ by Raviteja B** # portfolio
