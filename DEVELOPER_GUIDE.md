# Developer Guide - Minimal Notes

This guide provides technical information for developers working on the Minimal Notes project.

## Architecture Overview

### Technology Stack

- **Frontend**: React 18 with TypeScript
- **Build Tool**: Vite 5
- **Styling**: Tailwind CSS 3
- **UI Library**: shadcn/ui
- **Routing**: React Router v6
- **Icons**: Lucide React
- **State Management**: React Hooks + localStorage

### Design Patterns

1. **Component Composition**: Reusable components built with shadcn/ui
2. **Custom Hooks**: Centralized logic for common operations
3. **Type Safety**: Full TypeScript coverage
4. **Atomic Design**: Components organized by complexity
5. **Client-Side Storage**: localStorage for all data persistence

## Project Structure

```
src/
├── components/
│   ├── auth/              # Authentication-related components
│   │   ├── LoginDialog.tsx
│   │   ├── SignupDialog.tsx
│   │   └── ChangePasswordDialog.tsx
│   ├── common/            # Shared components
│   │   ├── Header.tsx
│   │   └── Footer.tsx
│   ├── resource/          # Resource management components
│   │   ├── AccessCodeDialog.tsx
│   │   └── PdfViewer.tsx
│   └── ui/                # shadcn/ui components (do not modify)
├── lib/
│   ├── accessCode.ts      # Access code generation/validation
│   ├── auth.ts            # Authentication logic
│   ├── storage.ts         # localStorage wrapper
│   └── utils.ts           # Utility functions
├── pages/
│   ├── Index.tsx          # Landing page
│   ├── Dashboard.tsx      # User dashboard
│   ├── ResourcePage.tsx   # Shared resource page logic
│   ├── Notes.tsx          # Notes page
│   ├── Questions.tsx      # Questions page
│   └── OneWord.tsx        # OneWord page
├── types/
│   └── index.ts           # TypeScript type definitions
├── App.tsx                # Main app component
├── routes.tsx             # Route configuration
└── index.css              # Global styles & design tokens
```

## Key Concepts

### 1. Authentication System

**Location**: `src/lib/auth.ts`

The authentication system uses localStorage to store user credentials:

```typescript
// User data structure
interface User {
  username: string;
  password: string;
  downloads: string[];
}

// Stored in localStorage as:
// - 'minimal_notes_users': Record<username, User>
// - 'minimal_notes_current_user': string (current username)
```

**Key Functions**:
- `auth.signup(username, password)` - Create new user
- `auth.login(username, password)` - Authenticate user
- `auth.logout()` - Clear current session
- `auth.getCurrentUser()` - Get logged-in username
- `auth.changePassword(current, new)` - Update password

### 2. Access Code System

**Location**: `src/lib/accessCode.ts`

Access codes control resource access using base64 encoding:

```typescript
// Generation formula
const accessCode = 'MN' + btoa(fileKey).substring(0, 5).replace(/=/g, '');

// Example:
// fileKey: 'Maths_1' → accessCode: 'MNTWFOa'
```

**Free Resources**:
```typescript
const FREE_RESOURCES = [
  'Maths_6_QB',
  'Maths_7_QB', 
  'History_4_QB',
  'Physics_5_QB'
];
```

### 3. Resource Management

**File Naming Convention**:
- Notes: `{Subject}_{Chapter}.pdf`
- Question Bank: `{Subject}_{Chapter}_QB.pdf`
- One Word: `{Subject}_{Chapter}_OW.pdf`

**Subjects Configuration**:
```typescript
const subjects = [
  { id: 'Maths', name: 'Maths', chapters: [1,2,3,4,5,6,7,8] },
  { id: 'Physics', name: 'Physics', chapters: [1,2,3,4,5,6] },
  { id: 'Chemistry', name: 'Chemistry', chapters: [1,2,3,4,5] },
  { id: 'Geography', name: 'Geography', chapters: [1,2,3,4] },
  { id: 'History', name: 'History', chapters: [1,2,3,4,5] }
];
```

### 4. Storage Layer

**Location**: `src/lib/storage.ts`

Wrapper around localStorage with type-safe operations:

```typescript
// Key operations
storage.getUser(username)           // Get user data
storage.saveUser(username, user)    // Save user data
storage.getCurrentUser()            // Get current session
storage.addDownload(username, key)  // Track download
storage.updatePassword(username, pw) // Change password
```

## Component Guidelines

### Creating New Components

1. **Use TypeScript**: Always define prop interfaces
2. **Follow shadcn/ui patterns**: Import from `@/components/ui`
3. **Use semantic tokens**: Reference design system colors
4. **Add error handling**: Use toast notifications
5. **Make it responsive**: Test on mobile and desktop

### Example Component Structure

```typescript
import React from 'react';
import { Button } from '@/components/ui/button';
import { useToast } from '@/hooks/use-toast';

interface MyComponentProps {
  title: string;
  onAction: () => void;
}

export function MyComponent({ title, onAction }: MyComponentProps) {
  const { toast } = useToast();

  const handleClick = () => {
    try {
      onAction();
      toast({
        title: 'Success',
        description: 'Action completed'
      });
    } catch (error) {
      toast({
        title: 'Error',
        description: 'Something went wrong',
        variant: 'destructive'
      });
    }
  };

  return (
    <div className="p-4">
      <h2 className="text-xl font-bold mb-4">{title}</h2>
      <Button onClick={handleClick}>
        Perform Action
      </Button>
    </div>
  );
}
```

## Design System

### Color Tokens

All colors are defined in `src/index.css` as CSS variables:

```css
:root {
  --primary: 217 91% 60%;        /* Main blue */
  --primary-foreground: 0 0% 100%; /* White text on primary */
  --secondary: 214 32% 91%;       /* Light gray */
  --muted: 214 32% 91%;           /* Muted backgrounds */
  --accent: 217 91% 95%;          /* Light blue accent */
  --destructive: 0 84% 60%;       /* Error red */
  /* ... more tokens */
}
```

### Using Colors

**✅ Correct**:
```tsx
<div className="bg-primary text-primary-foreground">
<Button variant="destructive">Delete</Button>
```

**❌ Incorrect**:
```tsx
<div className="bg-blue-500 text-white">  // Don't use Tailwind colors directly
<div style={{backgroundColor: '#2563eb'}}> // Don't use inline styles
```

### Typography

Use Tailwind's typography utilities:
```tsx
<h1 className="text-4xl font-bold">Title</h1>
<p className="text-muted-foreground">Description</p>
```

### Spacing

Follow consistent spacing patterns:
```tsx
<div className="p-4">        // Padding
<div className="mb-8">       // Margin bottom
<div className="gap-4">      // Gap in flex/grid
```

## State Management

### Local Component State

Use `useState` for component-specific state:
```typescript
const [isOpen, setIsOpen] = useState(false);
const [data, setData] = useState<User[]>([]);
```

### Global State (localStorage)

Use the storage utility for persistent data:
```typescript
import { storage } from '@/lib/storage';

// Get data
const user = storage.getUser(username);

// Save data
storage.saveUser(username, userData);
```

### Form State

Use controlled components:
```typescript
const [value, setValue] = useState('');

<Input
  value={value}
  onChange={(e) => setValue(e.target.value)}
/>
```

## Routing

### Adding New Routes

1. Create the page component in `src/pages/`
2. Add route to `src/routes.tsx`:

```typescript
import NewPage from './pages/NewPage';

const routes: RouteConfig[] = [
  // ... existing routes
  {
    name: 'New Page',
    path: '/new-page',
    element: <NewPage />,
    visible: false  // Hide from navigation
  }
];
```

### Protected Routes

Check authentication in the component:
```typescript
export default function ProtectedPage() {
  const navigate = useNavigate();
  
  useEffect(() => {
    if (!auth.isAuthenticated()) {
      navigate('/');
    }
  }, [navigate]);
  
  // ... rest of component
}
```

## Error Handling

### Toast Notifications

Use the toast hook for user feedback:
```typescript
import { useToast } from '@/hooks/use-toast';

const { toast } = useToast();

// Success
toast({
  title: 'Success',
  description: 'Operation completed'
});

// Error
toast({
  title: 'Error',
  description: 'Something went wrong',
  variant: 'destructive'
});
```

### Try-Catch Blocks

Wrap risky operations:
```typescript
try {
  const result = performOperation();
  // Handle success
} catch (error) {
  console.error('Operation failed:', error);
  toast({
    title: 'Error',
    description: error.message,
    variant: 'destructive'
  });
}
```

## Testing

### Manual Testing Checklist

- [ ] User can sign up with valid credentials
- [ ] User can log in with correct credentials
- [ ] Invalid login shows error message
- [ ] User can change password
- [ ] User can log out
- [ ] Dashboard shows correct username
- [ ] All subjects are displayed
- [ ] All chapters are displayed
- [ ] Free resources don't require access code
- [ ] Paid resources require valid access code
- [ ] Invalid access code shows error
- [ ] PDF preview opens in new tab
- [ ] PDF download works correctly
- [ ] Download history updates
- [ ] Navigation works correctly
- [ ] Responsive design works on mobile
- [ ] All buttons are functional
- [ ] No console errors

### Browser Console Testing

Open console (F12) to see:
- Expected access codes for each resource
- Any error messages
- Network requests

## Performance Optimization

### Code Splitting

Routes are automatically code-split by Vite.

### Lazy Loading

Images and PDFs are loaded on-demand.

### Bundle Size

Check bundle size:
```bash
pnpm run build
# Check dist/ folder size
```

## Common Tasks

### Adding a New Subject

1. Update `src/lib/accessCode.ts`:
```typescript
export const subjects = [
  // ... existing subjects
  { id: 'Biology', name: 'Biology', chapters: [1,2,3,4] }
];
```

2. Add PDF files to `public/pdfs/`:
```
Biology_1.pdf
Biology_1_QB.pdf
Biology_1_OW.pdf
```

### Changing Access Code Algorithm

1. Update `src/lib/accessCode.ts`:
```typescript
export const accessCode = {
  generate(fileKey: string): string {
    // New algorithm here
    return 'MN' + yourNewAlgorithm(fileKey);
  }
};
```

2. Update documentation in `ACCESS_CODES.md`

### Adding New Resource Type

1. Update types in `src/types/index.ts`
2. Add to `resourceTypes` in `src/lib/accessCode.ts`
3. Create new page component
4. Add route to `src/routes.tsx`
5. Add navigation button to Dashboard

## Debugging

### Common Issues

**Issue**: Blank page after build
- Check browser console for errors
- Verify `base` in `vite.config.ts`
- Check route configuration

**Issue**: Access codes not working
- Check console for expected code
- Verify file key format
- Check `FREE_RESOURCES` array

**Issue**: PDF not loading
- Verify file exists in `public/pdfs/`
- Check file name matches convention
- Check browser console for 404 errors

### Debug Mode

Enable verbose logging:
```typescript
// In src/lib/accessCode.ts
console.log('File key:', fileKey);
console.log('Expected code:', expectedCode);
console.log('Input code:', inputCode);
```

## Code Style

### Naming Conventions

- **Components**: PascalCase (`UserProfile.tsx`)
- **Functions**: camelCase (`getUserData()`)
- **Constants**: UPPER_SNAKE_CASE (`FREE_RESOURCES`)
- **Types**: PascalCase (`interface User {}`)

### File Organization

- One component per file
- Co-locate related files
- Use index files for exports
- Keep files under 300 lines

### Import Order

1. React imports
2. Third-party libraries
3. UI components
4. Local components
5. Utilities and types
6. Styles

```typescript
import React, { useState } from 'react';
import { useNavigate } from 'react-router-dom';
import { Button } from '@/components/ui/button';
import { Header } from '@/components/common/Header';
import { auth } from '@/lib/auth';
import type { User } from '@/types';
```

## Git Workflow

### Commit Messages

Follow conventional commits:
```
feat: Add new subject selector
fix: Resolve access code validation bug
docs: Update deployment guide
style: Format code with Biome
refactor: Simplify authentication logic
test: Add user flow tests
```

### Branch Naming

- `feature/feature-name` - New features
- `fix/bug-description` - Bug fixes
- `docs/update-readme` - Documentation
- `refactor/component-name` - Refactoring

## Deployment

### Pre-Deployment Checklist

- [ ] Run `pnpm run lint` - No errors
- [ ] Test all user flows
- [ ] Update version in `package.json`
- [ ] Update `CHANGELOG.md`
- [ ] Build successfully (`pnpm run build`)
- [ ] Test production build (`pnpm run preview`)
- [ ] Update documentation

### Build Command

```bash
pnpm run build
```

Output: `dist/` directory

### Environment Variables

For production, create `.env.production`:
```
VITE_APP_NAME=Minimal Notes
VITE_API_URL=https://api.example.com
```

## Resources

### Documentation

- [React Docs](https://react.dev/)
- [TypeScript Docs](https://www.typescriptlang.org/docs/)
- [Tailwind CSS](https://tailwindcss.com/docs)
- [shadcn/ui](https://ui.shadcn.com/)
- [Vite Guide](https://vitejs.dev/guide/)

### Tools

- [React DevTools](https://react.dev/learn/react-developer-tools)
- [TypeScript Playground](https://www.typescriptlang.org/play)
- [Tailwind Play](https://play.tailwindcss.com/)

## Support

For development questions:
1. Check this guide
2. Review component source code
3. Check shadcn/ui documentation
4. Open an issue on GitHub

---

**Last Updated**: 2025-12-09  
**Maintainer**: Development Team
