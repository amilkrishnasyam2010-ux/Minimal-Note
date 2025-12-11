# Welcome to Your Miaoda Project
Miaoda Application Link URL
    URL:https://medo.dev/projects/app-83t3rqxocu81

# Minimal Notes

A comprehensive educational resource management platform built with React, TypeScript, and Tailwind CSS. Access study notes, question banks, and vocabulary materials across five subjects with a clean, modern Superlist-inspired interface.

## 🎯 Features

- **User Authentication**: Secure login and signup system with localStorage
- **Multiple Resource Types**: 
  - 📚 Notes - Comprehensive study materials
  - ❓ Question Bank - Practice questions
  - ✨ One Word - Vocabulary resources
- **Five Subjects**: Maths, Physics, Chemistry, Biology, Social Science
- **Access Code System**: Controlled resource access with some free content
- **Download Tracking**: Monitor your learning progress
- **Responsive Design**: Works seamlessly on desktop and mobile devices
- **Modern UI**: Superlist-inspired design with shadcn/ui components and Tailwind CSS
- **Frontend Only**: No backend required - runs entirely in the browser

## 🚀 Quick Start

### Prerequisites

- Node.js ≥ 20
- npm ≥ 10 or pnpm ≥ 8

### Installation

1. Clone the repository:
   ```bash
   git clone <repository-url>
   cd minimal-notes
   ```

2. Install dependencies:
   ```bash
   pnpm install
   # or
   npm install
   ```

3. Start the development server:
   ```bash
   pnpm run dev
   # or
   npm run dev
   ```

4. Open your browser and navigate to `http://localhost:5173`

## 📁 Project Structure

```
├── public/
│   ├── pdfs/              # PDF files directory
│   └── favicon.png        # Application icon
├── src/
│   ├── components/
│   │   ├── auth/          # Authentication components
│   │   ├── common/        # Common components (Header, Footer)
│   │   ├── resource/      # Resource-related components
│   │   └── ui/            # shadcn/ui components
│   ├── lib/
│   │   ├── accessCode.ts  # Access code generation/validation
│   │   ├── auth.ts        # Authentication utilities
│   │   ├── storage.ts     # localStorage management
│   │   └── utils.ts       # General utilities
│   ├── pages/
│   │   ├── Index.tsx      # Landing page
│   │   ├── Dashboard.tsx  # User dashboard
│   │   ├── Notes.tsx      # Notes page
│   │   ├── Questions.tsx  # Question bank page
│   │   └── OneWord.tsx    # Vocabulary page
│   ├── types/
│   │   └── index.ts       # TypeScript type definitions
│   ├── App.tsx            # Main application component
│   ├── routes.tsx         # Route configuration
│   └── index.css          # Global styles
├── ACCESS_CODES.md        # Access code reference
├── DEPLOYMENT.md          # Deployment guide
├── USER_GUIDE.md          # User documentation
└── README.md              # This file
```

## 🎨 Design System

The application uses a professional blue color scheme optimized for educational content:

- **Primary Color**: Blue (#2563eb) - Trust and professionalism
- **Background**: White/Light gray - Clean and readable
- **Accents**: Subtle blues and grays - Visual hierarchy

All colors are defined as semantic tokens in `src/index.css` and can be easily customized.

## 📚 Adding PDF Files

1. Navigate to `public/pdfs/`
2. Add your PDF files following the naming convention:
   - Notes: `{Subject}_{Chapter}.pdf` (e.g., `Maths_1.pdf`)
   - Question Bank: `{Subject}_{Chapter}_QB.pdf` (e.g., `Physics_2_QB.pdf`)
   - One Word: `{Subject}_{Chapter}_OW.pdf` (e.g., `Chemistry_3_OW.pdf`)

### Available Subjects and Chapters

- **Maths**: Chapters 1-7
- **Physics**: Chapters 1-7
- **Chemistry**: Chapters 1-7
- **Biology**: Chapters 1-6
- **Social Science**: Chapters 1-9

## 🔐 Access Code System

Access codes control resource access. The format is: `MN` + 5 characters

### Free Resources (No Access Code Required)

- Maths Chapter 6 - Question Bank
- Maths Chapter 7 - Question Bank
- History Chapter 4 - Question Bank
- Physics Chapter 5 - Question Bank

### Testing Access Codes

During development, the expected access code for each resource is logged to the browser console. Open the console (F12) to see the codes when selecting a chapter.

For a complete reference, see [ACCESS_CODES.md](./ACCESS_CODES.md).

## 🛠️ Tech Stack

- **Frontend Framework**: React 18 with TypeScript
- **Build Tool**: Vite
- **Styling**: Tailwind CSS
- **UI Components**: shadcn/ui
- **Routing**: React Router v6
- **Icons**: Lucide React
- **State Management**: React Context + Hooks
- **Data Storage**: localStorage (client-side)

## 📖 Documentation

- [User Guide](./USER_GUIDE.md) - Complete guide for end users
- [Deployment Guide](./DEPLOYMENT.md) - Instructions for deploying to GitHub Pages
- [Access Codes Reference](./ACCESS_CODES.md) - Complete access code documentation
- [PDF Files Guide](./public/pdfs/README.md) - PDF naming conventions and setup

## 🚢 Deployment

### GitHub Pages

1. Update `vite.config.ts` with your repository name:
   ```typescript
   base: '/your-repo-name/'
   ```

2. Build and deploy:
   ```bash
   pnpm run build
   pnpm run deploy
   ```

For detailed deployment instructions, see [DEPLOYMENT.md](./DEPLOYMENT.md).

## 🧪 Development

### Available Scripts

- `pnpm run dev` - Start development server
- `pnpm run build` - Build for production
- `pnpm run preview` - Preview production build
- `pnpm run lint` - Run linter

### Code Quality

The project uses:
- **Biome** for linting and formatting
- **TypeScript** for type safety
- **ESLint** for code quality

Run `pnpm run lint` to check for issues.

## 🔒 Security Notes

**Important**: The current implementation uses localStorage for demonstration purposes. For production use:

1. Implement proper backend authentication
2. Use secure password hashing (bcrypt, argon2)
3. Store access codes server-side
4. Implement rate limiting
5. Add CSRF protection
6. Use HTTPS only

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- [shadcn/ui](https://ui.shadcn.com/) - Beautiful UI components
- [Tailwind CSS](https://tailwindcss.com/) - Utility-first CSS framework
- [Lucide Icons](https://lucide.dev/) - Beautiful icon set
- [Vite](https://vitejs.dev/) - Fast build tool

## 📧 Support

For issues, questions, or suggestions:
- Check the [User Guide](./USER_GUIDE.md)
- Review the [Deployment Guide](./DEPLOYMENT.md)
- Open an issue on GitHub

---

**Version**: 1.0.0  
**Last Updated**: 2025-12-09

Made with ❤️ for education
