# CinePixel - AI Media Generation Platform

![CinePixel Logo](https://img.shields.io/badge/CinePixel-AI%20Media%20Generation-blueviolet?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMjQiIGhlaWdodD0iMjQiIHZpZXdCb3g9IjAgMCAxMDAgMTAwIiBmaWxsPSJub25lIiB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciPjxjaXJjbGUgY3g9IjUwIiBjeT0iNTAiIHI9IjQ1IiBzdHJva2U9IiM2MzY2ZjEiIHN0cm9rZS13aWR0aD0iMyIvPjxyZWN0IHg9IjM1IiB5PSIzNSIgd2lkdGg9IjMwIiBoZWlnaHQ9IjMwIiByeD0iNiIgZmlsbD0iIzYzNjZmMSIvPjxwb2x5Z29uIHBvaW50cz0iNDUsNDIgNDUsNTggNTgsNTAiIGZpbGw9IndoaXRlIi8+PC9zdmc+)

CinePixel is a modern, full-stack AI media generation platform that transforms your imagination into stunning visuals. Create breathtaking AI-powered images and videos with an intuitive, beautifully designed interface.

## ✨ Features

- **🎨 AI Image Generation**: Create stunning images from text prompts using advanced AI models
- **🎬 AI Video Generation**: Generate captivating videos from text descriptions or images
- **🖼️ Gallery Management**: Organize and view all your creations in a beautiful gallery
- **⬬ Download & Share**: Download your generated content in high quality
- **🔐 Secure Authentication**: Email/password authentication with JWT tokens
- **💳 Credit System**: Fair usage system with 100 free credits for new users
- **📱 Responsive Design**: Works perfectly on desktop, tablet, and mobile devices

## 🚀 Tech Stack

### Frontend
- **React 18** with TypeScript
- **Wouter** for client-side routing
- **Tailwind CSS** with custom CinePixel gradients
- **Shadcn/ui** component library
- **TanStack Query** for server state management
- **Vite** for fast development and building

### Backend
- **Node.js** with Express.js
- **TypeScript** with ES modules
- **JWT** authentication
- **Drizzle ORM** with PostgreSQL
- **Replicate API** for AI generation

### Database & Storage
- **PostgreSQL** (Supabase recommended)
- **Drizzle ORM** for type-safe database operations
- **Supabase Storage** for media files

## 🎨 Design System

CinePixel features a cohesive design system built around creativity and innovation:

- **Custom Logo**: Animated SVG combining film reel, play button, and pixel elements
- **Color Palette**: Beautiful gradients from indigo → purple → pink
- **Glass Morphism**: Modern backdrop blur effects and translucent elements
- **Smooth Animations**: Hover effects, loading states, and micro-interactions

## 🛠️ Installation & Setup

### Prerequisites

- Node.js 18+ installed
- A Supabase account for database and storage
- A Replicate account for AI generation

### 1. Clone & Install

```bash
# Clone the repository
git clone <your-repo-url>
cd cinepixel

# Install dependencies
npm install
```

### 2. Environment Configuration

You'll need to set up these environment variables in Replit Secrets or `.env`:

#### Required Secrets:

1. **DATABASE_URL** - Your Supabase database connection string
   ```
   # Get this from your Supabase project dashboard:
   # 1. Go to https://supabase.com/dashboard/projects
   # 2. Create/select your project
   # 3. Click "Connect" button
   # 4. Copy "Connection string" -> "Transaction pooler"
   # 5. Replace [YOUR-PASSWORD] with your actual password
   postgresql://postgres:[YOUR-PASSWORD]@db.xxx.supabase.co:5432/postgres?pgbouncer=true
   ```

2. **REPLICATE_API_TOKEN** - Your Replicate API token
   ```
   # Get this from Replicate:
   # 1. Sign up at https://replicate.com
   # 2. Go to account settings
   # 3. Generate an API token (starts with "r8_")
   r8_xxxxxxxxxxxxxxxxxxxxxxxxxx
   ```

3. **JWT_SECRET** - Secret key for JWT tokens
   ```
   # Generate a secure random string (32+ characters)
   your-super-secure-jwt-secret-key-here
   ```

### 3. Database Setup

```bash
# Push the database schema to your Supabase database
npm run db:push
```

### 4. Development

```bash
# Start the development server
npm run dev
```

The app will be available at `http://localhost:5000`

### 5. Production Build

```bash
# Build for production
npm run build

# Start production server
npm start
```

## 🎯 Usage Guide

### Getting Started

1. **Sign Up**: Create your CinePixel account with email and password
2. **Get Credits**: New users receive 100 free credits to start creating
3. **Generate Content**: Use the dashboard to create images (5 credits) or videos (15 credits)
4. **View Gallery**: Browse all your creations in the beautiful gallery
5. **Download**: Save your favorite generations to your device

### AI Models Used

- **Images**: Flux Schnell (black-forest-labs/flux-schnell)
- **Videos**: Video-01 (minimax/video-01)

Both models are accessed through Replicate's API for consistent, high-quality results.

## 📁 Project Structure

```
cinepixel/
├── client/                 # Frontend React application
│   ├── src/
│   │   ├── components/     # Reusable UI components
│   │   │   ├── cinepixel-logo.tsx
│   │   │   ├── navigation-sidebar.tsx
│   │   │   ├── image-generation-card.tsx
│   │   │   ├── video-generation-card.tsx
│   │   │   └── media-gallery.tsx
│   │   ├── pages/          # Page components
│   │   │   ├── login.tsx
│   │   │   ├── dashboard.tsx
│   │   │   └── gallery.tsx
│   │   ├── lib/            # Utility libraries
│   │   │   ├── auth.ts
│   │   │   ├── queryClient.ts
│   │   │   └── utils.ts
│   │   ├── hooks/          # Custom React hooks
│   │   └── index.css       # Custom Tailwind styles
├── server/                 # Backend Express application
│   ├── index.ts           # Main server file
│   ├── routes.ts          # API routes
│   ├── storage.ts         # Data layer abstraction
│   └── vite.ts            # Vite middleware setup
├── shared/                 # Shared TypeScript schemas
│   └── schema.ts          # Database schemas and types
└── README.md              # This file
```

## 🔧 API Endpoints

### Authentication
- `POST /api/auth/register` - Create new user account
- `POST /api/auth/login` - User login
- `GET /api/auth/me` - Get current user info

### AI Generation
- `POST /api/generate/image` - Generate AI image (5 credits)
- `POST /api/generate/video` - Generate AI video (15 credits)

### Gallery
- `GET /api/generations` - Get user's generations
- `GET /api/generations/:id` - Get specific generation

## 🎨 Customization

The CinePixel design system is highly customizable:

### Colors
Update the gradient colors in `client/src/index.css`:
```css
.cinepixel-gradient {
  background: linear-gradient(135deg, #6366f1 0%, #8b5cf6 50%, #ec4899 100%);
}
```

### Logo
Modify the logo in `client/src/components/cinepixel-logo.tsx` to change:
- Colors and gradients
- Animation timing
- Size variations
- Brand name

### UI Components
All components use Tailwind CSS classes and can be easily customized by updating the class names.

## 🚀 Deployment

### Replit Deployment (Recommended)

1. Make sure all secrets are configured in Replit
2. Click the "Deploy" button in your Replit workspace
3. Your app will be automatically deployed to a `.replit.app` domain

### Other Platforms

The app can be deployed to any Node.js hosting platform:
- Vercel
- Netlify
- Railway
- Heroku
- DigitalOcean App Platform

## 📝 Development Notes

### Database
- Uses in-memory storage by default for development
- Switch to PostgreSQL for production by updating the storage implementation
- Database migrations are handled by Drizzle Kit

### AI Integration
- Replicate API handles all AI generation
- Async generation with status polling
- Error handling and credit refunds on failures

### Security
- JWT tokens for authentication
- Password hashing with bcrypt
- Input validation with Zod schemas
- Protected API routes

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 💡 Support

For support or questions:
- Create an issue in the repository
- Check the documentation
- Review the code comments for implementation details

---

**Built with ❤️ using modern web technologies**

Transform your imagination into reality with CinePixel! 🎬✨