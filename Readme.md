# 🎨 AI Canvas Studio

A powerful web-based AI image generator and canvas editor built with **Fabric.js** and **FastAPI**. Create, edit, and enhance images with AI-powered tools and intuitive drag-and-drop editing.

![AI Canvas Studio Demo](https://via.placeholder.com/800x400/667eea/ffffff?text=AI+Canvas+Studio+Demo)

## ✨ Features

###  **AI Image Generation**
- **Text-to-Image**: Generate images from descriptive prompts
- **Style Transfer**: Apply artistic styles from reference images
- **Image Enhancement**: AI-powered upscaling and filtering
- **Smart Composition**: Intelligent layout suggestions

###  **Canvas Editing**
- **Multi-format Support**: Instagram, YouTube, Facebook, and custom sizes
- **Layer Management**: Advanced layer controls with visibility and locking
- **Text Styling**: Rich text editing with fonts, colors, and effects
- **Image Manipulation**: Resize, rotate, crop, and transform images
- **Real-time Preview**: Live preview of all changes

### **Export Options**
- **Multiple Formats**: PNG, JPG, SVG export
- **Full Resolution**: Export at exact canvas resolution
- **Batch Export**: Export multiple variations
- **Cloud Integration**: Save to cloud storage

##  Architecture

```mermaid
graph TB
    A[Frontend - HTML/JS/Fabric.js] --> B[FastAPI Backend]
    B --> C[AI Models]
    B --> D[Image Processing]
    B --> E[File Storage]
    
    C --> C1[Stable Diffusion]
    C --> C2[Style Transfer]
    C --> C3[Image Enhancement]
    
    D --> D1[PIL/OpenCV]
    D --> D2[Image Filters]
    D --> D3[Format Conversion]
    
    E --> E1[Local Storage]
    E --> E2[AWS S3]
    E --> E3[Google Cloud]
```

##  Tech Stack

### **Frontend**
- **HTML5 Canvas** - Core rendering engine
- **Fabric.js** - Advanced canvas manipulation
- **Vanilla JavaScript** - No framework dependencies
- **CSS3** - Modern responsive design

### **Backend**
- **FastAPI** - High-performance Python API
- **Pydantic** - Data validation and serialization
- **SQLAlchemy** - Database ORM
- **Redis** - Caching and session management

### **AI/ML**
- **Stable Diffusion** - Text-to-image generation
- **CLIP** - Image understanding and style transfer
- **OpenCV** - Computer vision operations
- **PIL/Pillow** - Image processing

### **Infrastructure**
- **Docker** - Containerization
- **PostgreSQL** - Primary database
- **Redis** - Cache and queue management
- **AWS S3** - File storage
- **GitHub Actions** - CI/CD pipeline

##  Quick Start

### Prerequisites
- **Python 3.9+**
- **Node.js 16+** (for development tools)
- **Docker & Docker Compose**
- **Git**

### 1. Clone Repository
```bash
git clone https://github.com/yourusername/ai-canvas-studio.git
cd ai-canvas-studio
```

### 2. Environment Setup
```bash
# Copy environment template
cp .env.example .env

# Edit environment variables
nano .env
```

### 3. Docker Setup (Recommended)
```bash
# Start all services
docker-compose up -d

# View logs
docker-compose logs -f
```

### 4. Manual Setup
```bash
# Backend setup
cd backend
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate
pip install -r requirements.txt

# Start FastAPI server
uvicorn main:app --reload --host 0.0.0.0 --port 8000

# Frontend setup (in new terminal)
cd frontend
python -m http.server 3000  # Or use any static server
```

### 5. Access Application
- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8000
- **API Docs**: http://localhost:8000/docs

## 📁 Project Structure

```
ai-canvas-studio/
├── 📁 frontend/
│   ├── index.html              # Main application
│   ├── css/
│   │   └── styles.css         # Styling
│   ├── js/
│   │   ├── canvas.js          # Canvas logic
│   │   ├── api.js             # API integration
│   │   └── utils.js           # Utilities
│   └── assets/
│       └── images/            # Static images
├── 📁 backend/
│   ├── app/
│   │   ├── main.py            # FastAPI application
│   │   ├── models/            # Database models
│   │   ├── routers/           # API routes
│   │   ├── services/          # Business logic
│   │   └── utils/             # Helper functions
│   ├── requirements.txt       # Python dependencies
│   └── Dockerfile            # Backend container
├── 📁 ai-models/
│   ├── stable_diffusion/      # Text-to-image models
│   ├── style_transfer/        # Style transfer models
│   └── enhancement/           # Image enhancement
├── 📁 docker/
│   ├── docker-compose.yml     # Multi-service setup
│   ├── nginx.conf            # Reverse proxy config
│   └── redis.conf            # Redis configuration
├── 📁 .github/workflows/
│   ├── ci.yml                # Continuous Integration
│   ├── deploy.yml            # Deployment pipeline
│   └── tests.yml             # Automated testing
├── .env.example              # Environment template
├── README.md                 # This file
└── LICENSE                   # MIT License
```

## 🔧 Configuration

### Environment Variables
```bash
# AI Models
OPENAI_API_KEY=your_openai_key
HUGGINGFACE_TOKEN=your_hf_token
STABILITY_API_KEY=your_stability_key

# Database
DATABASE_URL=postgresql://user:pass@localhost:5432/aicanvas
REDIS_URL=redis://localhost:6379/0

# Storage
AWS_ACCESS_KEY_ID=your_aws_key
AWS_SECRET_ACCESS_KEY=your_aws_secret
S3_BUCKET_NAME=ai-canvas-storage

# Security
SECRET_KEY=your_secret_key
ALLOWED_ORIGINS=http://localhost:3000,https://yourdomain.com
```

## 🎯 Canvas Sizes Supported

| Platform | Dimensions | Aspect Ratio |
|----------|------------|--------------|
| Instagram Post | 1080×1080 | 1:1 |
| Instagram Story | 1080×1920 | 9:16 |
| Facebook Post | 1200×630 | 1.91:1 |
| YouTube Thumbnail | 1920×1080 | 16:9 |
| Twitter Header | 1500×500 | 3:1 |
| LinkedIn Post | 1200×627 | 1.91:1 |
| Pinterest Pin | 735×1102 | 2:3 |
| Custom | Any Size | Custom |

## 🌐 API Endpoints

### **Image Generation**
```http
POST /api/v1/generate/text-to-image
Content-Type: application/json

{
  "prompt": "A beautiful sunset over mountains",
  "style": "photorealistic",
  "width": 1024,
  "height": 1024
}
```

### **Style Transfer**
```http
POST /api/v1/generate/style-transfer
Content-Type: multipart/form-data

image: (file)
style_image: (file)
strength: 0.8
```

### **Canvas Operations**
```http
POST /api/v1/canvas/export
Content-Type: application/json

{
  "canvas_data": "base64_canvas_data",
  "format": "png",
  "quality": 0.9
}
```

## 🧪 Testing

### Run Tests
```bash
# Backend tests
cd backend
pytest tests/ -v

# Frontend tests (if using Jest)
cd frontend
npm test

# Integration tests
docker-compose -f docker-compose.test.yml up --abort-on-container-exit
```

### Test Coverage
```bash
# Generate coverage report
pytest --cov=app tests/
coverage html
```

##  Deployment

### **Production Docker Setup**
```bash
# Build production images
docker-compose -f docker-compose.prod.yml build

# Deploy to production
docker-compose -f docker-compose.prod.yml up -d
```

### **AWS Deployment**
```bash
# Deploy using AWS CLI
aws ecs deploy --cluster ai-canvas --service ai-canvas-service

# Or use GitHub Actions for automatic deployment
git push origin main  # Triggers deployment pipeline
```

### **Manual Deployment**
```bash
# Build frontend
cd frontend
npm run build

# Deploy backend
cd backend
pip install -r requirements.txt
gunicorn main:app --workers 4 --bind 0.0.0.0:8000
```

## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### **Development Workflow**
1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### **Code Standards**
- **Python**: Follow PEP 8, use `black` formatter
- **JavaScript**: Use ESLint with standard config
- **Documentation**: Update README for new features
- **Testing**: Add tests for new functionality

##  Performance

### **Benchmarks**
- **Image Generation**: ~5-15 seconds (depending on model)
- **Canvas Operations**: <100ms real-time
- **Export Operations**: <2 seconds for standard sizes
- **API Response Time**: <200ms average

### **Optimization Tips**
- Use **Redis caching** for repeated operations
- **Optimize images** before uploading
- **Batch operations** when possible
- **Use CDN** for static assets

##  Security

- **API Rate Limiting**: 100 requests/minute per IP
- **Input Validation**: All inputs sanitized and validated
- **CORS Protection**: Configured for production domains
- **File Upload Security**: Size limits and type validation
- **Authentication**: JWT-based user authentication

## 🐛 Troubleshooting

### **Common Issues**

**Canvas not loading?**
```bash
# Check if Fabric.js is loaded
console.log(typeof fabric);  # Should return 'object'
```

**AI generation failing?**
```bash
# Check API keys
curl -H "Authorization: Bearer $OPENAI_API_KEY" https://api.openai.com/v1/models
```

**Docker issues?**
```bash
# Reset Docker environment
docker-compose down
docker system prune -a
docker-compose up --build
```

##  License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

##  Acknowledgments

- **Fabric.js** - Amazing canvas library
- **FastAPI** - High-performance Python framework
- **Stability AI** - Stable Diffusion models
- **OpenAI** - CLIP and GPT models
- **Hugging Face** - Model hosting and APIs

---

⭐ **Star this repo** if you find it helpful!

**Made with ❤️ by [Your Name](https://github.com/mayyzz)**