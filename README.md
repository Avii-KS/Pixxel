# 🎨 PIXXEL - Professional Image Editing Platform

A modern, AI-powered image editing platform built with Next.js 15, featuring real-time collaboration, advanced AI tools, and a professional-grade editing experience.

## 🚀 Live Demo

[View Live Demo]([https://pixxel-rust.vercel.app/])

## ✨ Key Features

### 🎯 Core Editing Capabilities

- **Real-time Canvas Editing** - Powered by Fabric.js for smooth, responsive image manipulation
- **AI-Powered Tools** - Advanced image enhancement using ImageKit's AI transformations
- **Background Removal** - One-click AI background removal with multiple options
- **Image Extension** - AI-powered image extension in all directions
- **Smart Retouching** - Professional-grade image enhancement with multiple presets
- **Color & Adjustment Tools** - Comprehensive color correction and image adjustment

### 🤖 AI Features

- **AI Retouch** - Automatic image quality improvement
- **AI Upscale** - Increase resolution up to 16MP
- **AI Background Removal** - Remove backgrounds with precision
- **AI Image Extension** - Extend images intelligently using AI generation
- **Smart Enhancement** - Combined AI retouch, contrast, and sharpening

### 🎨 Professional Tools

- **Crop & Resize** - Precise cropping and resizing tools
- **Text Overlay** - Add and style text on images
- **Layer Management** - Professional layer-based editing
- **Export Options** - Multiple format and quality export options
- **Project Management** - Organize and manage multiple projects

### 🔐 User Management

- **Authentication** - Secure user authentication with Clerk
- **Project Organization** - Folder-based project organization
- **Usage Tracking** - Monitor usage and plan limits
- **Collaboration** - Real-time project sharing and collaboration

## 🏗️ Architecture Overview

### Frontend Architecture

```
app/
├── (auth)/                 # Authentication routes
│   ├── sign-in/
│   └── sign-up/
├── (main)/                 # Main application routes
│   ├── dashboard/          # Project management
│   └── editor/            # Image editor
│       └── [projectId]/   # Dynamic project routes
├── api/                   # API routes
└── globals.css           # Global styles
```

### Backend Architecture

```
convex/
├── schema.js             # Database schema
├── projects.js           # Project management functions
├── users.js              # User management functions
└── _generated/           # Auto-generated types
```

### Component Structure

```
components/
├── ui/                   # Reusable UI components
├── features.jsx          # Landing page features
├── header.jsx            # Navigation header
└── theme-provider.jsx    # Theme management
```

## 🛠️ Tech Stack

### Frontend

- **Next.js 15** - React framework with App Router
- **React 19** - Latest React with concurrent features
- **Fabric.js 6.7** - Canvas manipulation library
- **Tailwind CSS 4** - Utility-first CSS framework
- **Radix UI** - Accessible component primitives
- **Lucide React** - Beautiful icon library

### Backend & Database

- **Convex** - Real-time database and backend
- **Clerk** - Authentication and user management
- **ImageKit** - AI-powered image processing

### Development Tools

- **ESLint** - Code linting and formatting
- **PostCSS** - CSS processing
- **Turbopack** - Fast development bundler

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- npm or yarn
- Convex account
- Clerk account
- ImageKit account

### Installation

1. **Clone the repository**

```bash
git clone https://github.com/yourusername/ai-image-editor.git
cd ai-image-editor
```

2. **Install dependencies**

```bash
npm install
```

3. **Environment Setup**

```bash
cp .env.example .env.local
```

Configure your environment variables:

```env
# Clerk Authentication
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_key
CLERK_SECRET_KEY=your_clerk_secret

# Convex Database
NEXT_PUBLIC_CONVEX_URL=your_convex_url

# ImageKit Configuration
NEXT_PUBLIC_IMAGEKIT_URL_ENDPOINT=your_imagekit_endpoint
NEXT_PUBLIC_IMAGEKIT_PUBLIC_KEY=your_imagekit_public_key
IMAGEKIT_PRIVATE_KEY=your_imagekit_private_key

# Optional: Unsplash API
NEXT_PUBLIC_UNSPLASH_ACCESS_KEY=your_unsplash_key
```

4. **Start development server**

```bash
npm run dev
```

5. **Open your browser**
   Navigate to [http://localhost:3000](http://localhost:3000)

## 📁 Project Structure

```
ai-image-editor/
├── app/                    # Next.js App Router
│   ├── (auth)/            # Authentication pages
│   ├── (main)/            # Main application
│   │   ├── dashboard/     # Project dashboard
│   │   └── editor/        # Image editor
│   ├── api/               # API routes
│   └── globals.css        # Global styles
├── components/             # Reusable components
│   ├── ui/                # UI components
│   └── features.jsx       # Feature components
├── convex/                # Backend functions
│   ├── schema.js          # Database schema
│   ├── projects.js        # Project functions
│   └── users.js           # User functions
├── hooks/                 # Custom React hooks
├── lib/                   # Utility functions
└── public/                # Static assets
```

## 🎯 Key Features Implementation

### 1. Real-time Canvas Editing

The editor uses Fabric.js for canvas manipulation, providing:

- Smooth object manipulation
- Layer management
- Real-time updates
- Export capabilities

```javascript
// Canvas initialization
const canvas = new fabric.Canvas("canvas", {
  width: 800,
  height: 600,
  backgroundColor: "#ffffff",
});
```

### 2. AI-Powered Image Processing

Integration with ImageKit's AI transformations:

```javascript
// AI Background Removal
const bgRemovedUrl = `${imageUrl}?tr=e-bgremove`;

// AI Retouch
const retouchedUrl = `${imageUrl}?tr=e-retouch,e-contrast,e-sharpen`;

// AI Image Extension
const extendedUrl = `${imageUrl}?tr=bg-genfill,w-1200,h-800,cm-pad_resize,fo-center`;
```

### 3. Project Management

Convex database schema for project organization:

```javascript
// Project schema
projects: defineTable({
  title: v.string(),
  userId: v.id("users"),
  canvasState: v.any(),
  originalImageUrl: v.optional(v.string()),
  currentImageUrl: v.optional(v.string()),
  createdAt: v.number(),
  updatedAt: v.number(),
});
```

### 4. Authentication & Authorization

Clerk integration for secure user management:

```javascript
// Protected routes
import { auth } from "@clerk/nextjs";

export default function Dashboard() {
  const { userId } = auth();
  // User-specific data and permissions
}
```

## 🔧 Advanced Features

### AI Image Enhancement

- **Multiple Presets**: AI retouch, upscale, enhance & sharpen, premium quality
- **Real-time Processing**: Live preview of AI transformations
- **Batch Processing**: Apply multiple AI effects simultaneously

### Background Management

- **AI Removal**: One-click background removal
- **Color Backgrounds**: Custom color backgrounds
- **Image Backgrounds**: Unsplash integration for background images
- **Transparent Export**: PNG export with transparency

### Image Extension

- **Multi-directional**: Extend in any direction (top, bottom, left, right)
- **AI Generation**: Intelligent content generation for extensions
- **Custom Sizing**: Adjustable extension amounts
- **Focus Control**: Maintain subject focus during extension

## 📊 Performance Optimizations

### Frontend Optimizations

- **Code Splitting**: Dynamic imports for better loading
- **Image Optimization**: Next.js Image component with optimization
- **Lazy Loading**: Components loaded on demand
- **Memoization**: React.memo and useMemo for performance

### Backend Optimizations

- **Real-time Updates**: Convex subscriptions for live data
- **Caching**: Intelligent caching strategies
- **Database Indexing**: Optimized queries with proper indexing
- **CDN Integration**: ImageKit CDN for fast image delivery

## 🔒 Security Features

- **Authentication**: Secure user authentication with Clerk
- **Authorization**: Role-based access control
- **Data Validation**: Input validation and sanitization
- **CORS Protection**: Proper CORS configuration
- **Rate Limiting**: API rate limiting for abuse prevention

## 🧪 Testing Strategy

### Unit Testing

- Component testing with React Testing Library
- Hook testing with custom test utilities
- Utility function testing

### Integration Testing

- API endpoint testing
- Database operation testing
- Authentication flow testing

### E2E Testing

- User workflow testing
- Cross-browser compatibility
- Performance testing

## 🚀 Deployment

### Production Build

```bash
npm run build
npm start
```

### Environment Variables

Ensure all production environment variables are configured:

- Database connection strings
- API keys and secrets
- CDN configurations
- Monitoring and analytics

### Monitoring

- Error tracking with Sentry
- Performance monitoring
- User analytics
- Server health monitoring

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Fabric.js** - Canvas manipulation library
- **ImageKit** - AI-powered image processing
- **Clerk** - Authentication and user management
- **Convex** - Real-time database and backend
- **Radix UI** - Accessible component primitives

## 📞 Contact

- **Portfolio**: [Your Portfolio](https://your-portfolio.com)
- **LinkedIn**: [Your LinkedIn](https://linkedin.com/in/yourprofile)
- **Email**: your.email@example.com

---

**Built with ❤️ using Next.js, React, and modern web technologies**

_This project demonstrates advanced frontend development skills, AI integration, real-time collaboration, and professional-grade application architecture._
