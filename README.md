# CreatorOS: AI-Powered Content Automation Platform

**Tagline:** Create. Automate. Grow.

CreatorOS is a comprehensive AI-powered content automation platform designed for content creators to discover trends, generate scripts, create thumbnails, produce videos, optimize SEO, schedule uploads, publish content, and analyze channel growth—all in one unified platform.

## 🚀 Features

### Content Generation
- **Trend Discovery**: Real-time trend analysis across multiple platforms
- **Script Generation**: AI-powered scripts for long-form videos, shorts, and reels in multiple languages
- **Thumbnail Creation**: Automated thumbnail generation with text overlays and templates
- **Video Production**: End-to-end video creation with captions and scene generation
- **Voice Synthesis**: Multi-voice text-to-speech capabilities

### Optimization & Publishing
- **SEO Optimization**: Intelligent title, description, and keyword suggestions
- **Hashtag Generation**: AI-powered hashtag suggestions for maximum reach
- **Schedule Management**: Automated content scheduling and publishing
- **YouTube Integration**: Direct YouTube upload and analytics integration

### Analytics & Growth
- **Channel Analytics**: Comprehensive performance metrics and insights
- **Growth Recommendations**: AI-powered suggestions for channel optimization
- **Performance Tracking**: Real-time tracking of views, CTR, retention, and subscribers

## 📋 Prerequisites

- Docker & Docker Compose
- Python 3.12+ (for local development)
- Node.js 18+ (for frontend development)
- PostgreSQL 15+ (included in Docker setup)
- Redis (included in Docker setup)

## 🛠️ Tech Stack

### Backend
- **Framework**: Django 5.0 + Django REST Framework
- **Database**: PostgreSQL
- **Task Queue**: Celery + Redis
- **Authentication**: JWT (SimpleJWT)
- **Video Processing**: FFmpeg
- **API Documentation**: DRF Spectacular

### Frontend
- **Framework**: Next.js 15 with TypeScript
- **Styling**: Tailwind CSS + ShadCN UI
- **State Management**: Zustand
- **Data Fetching**: TanStack React Query
- **Charts**: Recharts
- **Animations**: Framer Motion

### Infrastructure
- **Containerization**: Docker & Docker Compose
- **Web Server**: Nginx (reverse proxy & static serving)
- **CI/CD**: GitHub Actions
- **Storage**: Local filesystem (production-ready for S3 migration)

## 🚀 Quick Start

### Option 1: Docker Compose (Recommended)

```bash
# Clone the repository
git clone https://github.com/bindnoob70-sudo/creatoros.git
cd creatoros

# Copy environment variables
cp .env.example .env

# Build and start all services
docker-compose up -d

# Run migrations
docker-compose exec backend python manage.py migrate

# Create superuser
docker-compose exec backend python manage.py createsuperuser

# Access the application
# Frontend: http://localhost:3000
# Backend API: http://localhost:8000/api/v1/
# Admin Panel: http://localhost:8000/admin/
```

### Option 2: Local Development

```bash
# Backend Setup
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements/development.txt

python manage.py migrate
python manage.py createsuperuser
python manage.py runserver

# In another terminal - Frontend Setup
cd frontend
npm install
npm run dev

# In another terminal - Celery Worker
cd backend
celery -A config worker -l info
```

## 📁 Project Structure

```
creatoros/
├── backend/                      # Django application
│   ├── apps/                     # Django apps
│   │   ├── accounts/             # User management
│   │   ├── authentication/       # Auth endpoints
│   │   ├── channels/             # YouTube channel management
│   │   ├── projects/             # Project management
│   │   ├── scripts/              # Script generation
│   │   ├── videos/               # Video management
│   │   ├── thumbnails/           # Thumbnail generation
│   │   ├── seo/                  # SEO optimization
│   │   ├── hashtags/             # Hashtag generation
│   │   ├── analytics/            # Analytics engine
│   │   ├── uploads/              # Upload scheduling
│   │   ├── notifications/        # Notification system
│   │   └── settings/             # User settings
│   ├── config/                   # Django configuration
│   ├── requirements/             # Python dependencies
│   ├── media/                    # User-uploaded files
│   ├── static/                   # Static files
│   ├── logs/                     # Application logs
│   └── manage.py
│
├── frontend/                     # Next.js application
│   ├── app/                      # App router pages
│   ├── components/               # Reusable components
│   ├── hooks/                    # Custom React hooks
│   ├── services/                 # API services
│   ├── store/                    # Zustand stores
│   ├── types/                    # TypeScript types
│   ├── lib/                      # Utilities
│   ├── styles/                   # Global styles
│   └── public/                   # Static assets
│
├── ai-engine/                    # AI services
│   ├── trend_engine/             # Trend analysis
│   ├── script_generator/         # Script generation
│   ├── seo_generator/            # SEO generation
│   ├── hashtag_generator/        # Hashtag generation
│   ├── thumbnail_generator/      # Thumbnail generation
│   ├── voice_engine/             # Text-to-speech
│   ├── video_generator/          # Video creation
│   ├── analytics_engine/         # Analytics
│   └── growth_agent/             # Growth recommendations
│
├── infrastructure/               # IaC and configs
├── docker/                       # Docker configurations
├── nginx/                        # Nginx configuration
├── .github/                      # GitHub Actions
├── scripts/                      # Utility scripts
├── tests/                        # Test files
├── docker-compose.yml            # Docker Compose config
└── .env.example                  # Environment template
```

## 🔐 Environment Variables

See `.env.example` for all available configuration options.

Key variables:
```
DJANGO_SECRET_KEY
DEBUG=False
ALLOWED_HOSTS
DATABASE_URL
REDIS_URL
YOUTUBE_CLIENT_ID
YOUTUBE_CLIENT_SECRET
```

## 🔌 API Endpoints

### Authentication
- `POST /api/v1/auth/register/` - User registration
- `POST /api/v1/auth/login/` - User login
- `POST /api/v1/auth/refresh/` - Refresh token
- `POST /api/v1/auth/logout/` - User logout
- `POST /api/v1/auth/password-reset/` - Password reset

### Content Management
- `GET/POST /api/v1/projects/` - Project management
- `GET/POST /api/v1/scripts/` - Script generation and listing
- `GET/POST /api/v1/videos/` - Video management
- `GET/POST /api/v1/thumbnails/` - Thumbnail generation
- `GET/POST /api/v1/seo/` - SEO optimization

### Analytics
- `GET /api/v1/analytics/overview/` - Channel overview
- `GET /api/v1/analytics/performance/` - Performance metrics
- `GET /api/v1/analytics/growth/` - Growth recommendations

### YouTube Integration
- `POST /api/v1/channels/auth/` - YouTube OAuth
- `POST /api/v1/uploads/schedule/` - Schedule uploads
- `GET /api/v1/channels/analytics/` - YouTube analytics

## 🧪 Testing

```bash
# Backend tests
cd backend
pytest
pytest --cov

# Frontend tests
cd frontend
npm test
npm run test:coverage
```

## 📚 Documentation

- [Installation Guide](./docs/INSTALLATION.md)
- [Development Guide](./docs/DEVELOPMENT.md)
- [API Documentation](./docs/API.md)
- [Deployment Guide](./docs/DEPLOYMENT.md)
- [Architecture](./docs/ARCHITECTURE.md)

## 🔄 CI/CD Pipeline

GitHub Actions automatically:
- Lints code (Black, Flake8, ESLint)
- Runs tests
- Builds Docker images
- Generates API documentation

## 🐳 Docker Services

```yaml
Services:
  - frontend: Next.js application (port 3000)
  - backend: Django application (port 8000)
  - postgres: PostgreSQL database (port 5432)
  - redis: Redis cache (port 6379)
  - celery: Background task worker
  - nginx: Reverse proxy (port 80/443)
```

## 📊 Database Models

- **User**: Core user model with profile
- **Channel**: YouTube channel management
- **Project**: Content project management
- **Video**: Video metadata and status
- **Script**: Generated scripts
- **Thumbnail**: Generated thumbnails
- **SEO**: SEO metadata and suggestions
- **Hashtag**: Hashtag suggestions
- **Analytics**: Performance metrics
- **UploadSchedule**: Scheduled uploads
- **Notification**: User notifications
- **ActivityLog**: Audit trail

## 🔒 Security Features

- JWT-based authentication
- CSRF protection
- Rate limiting on endpoints
- Input validation and sanitization
- Secure password hashing (Argon2)
- Environment variable configuration
- Secure headers (HSTS, X-Frame-Options, etc.)
- CORS properly configured
- SQL injection prevention (ORM)

## 🚀 Deployment

See [Deployment Guide](./docs/DEPLOYMENT.md) for:
- Production environment setup
- Database migrations
- Static file collection
- SSL/TLS configuration
- Monitoring and logging
- Backup strategies

## 🤝 Contributing

1. Create a feature branch
2. Make your changes
3. Write/update tests
4. Submit a pull request

## 📄 License

MIT License - See LICENSE file for details

## 🆘 Support

For issues and questions:
- GitHub Issues: [Create an issue](https://github.com/bindnoob70-sudo/creatoros/issues)
- Documentation: [Docs folder](./docs)

## 🎯 Roadmap

- [ ] Multi-language support
- [ ] Advanced AI model integration
- [ ] TikTok integration
- [ ] Instagram Reels integration
- [ ] Collaboration features
- [ ] Team management
- [ ] Advanced analytics dashboard
- [ ] API webhook support
- [ ] Mobile app (React Native)
- [ ] Enterprise features

---

**CreatorOS** - Empowering creators to focus on creativity while we handle automation.
