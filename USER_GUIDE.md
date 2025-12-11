# Minimal Notes - User Guide

## Overview

Minimal Notes is a comprehensive educational resource management platform that provides access to study notes, question banks, and vocabulary materials across five subjects: Maths, Physics, Chemistry, Geography, and History.

## Getting Started

### 1. Account Creation

1. Visit the homepage
2. Click the **Sign Up** button
3. Enter your desired username (minimum 3 characters)
4. Create a password (minimum 6 characters)
5. Confirm your password
6. Click **Sign Up** to create your account

### 2. Logging In

1. Click the **Login** button on the homepage
2. Enter your username and password
3. Click **Login** to access your dashboard

## Features

### Dashboard

After logging in, you'll see your personalized dashboard with:
- Welcome message with your username
- Three resource type cards: Notes, Question Bank, and One Word
- Download history showing all resources you've accessed

### Resource Types

#### 1. Notes
Comprehensive study notes for all subjects and chapters.

#### 2. Question Bank
Practice questions organized by subject and chapter. Some chapters are available for free!

#### 3. One Word
Vocabulary resources to expand your knowledge.

### Accessing Resources

1. **Select Resource Type**: From the dashboard, click on Notes, Question Bank, or One Word
2. **Choose Subject**: Select from Maths, Physics, Chemistry, Geography, or History
3. **Select Chapter**: Choose the chapter you want to access
4. **Enter Access Code** (if required): Some resources require an access code
5. **View/Download**: Preview the PDF in a new tab or download it to your device

### Free Resources

The following resources are available without an access code:
- Maths Chapter 6 - Question Bank
- Maths Chapter 7 - Question Bank
- History Chapter 4 - Question Bank
- Physics Chapter 5 - Question Bank

### Access Codes

Access codes are required for most resources. When you select a chapter that requires an access code:
1. A dialog will appear asking for the code
2. Enter the access code (format: MN + 5 characters)
3. Click **Verify** to access the resource

**Note**: The expected access code for each resource is logged to the browser console for testing purposes.

### Download History

Your dashboard keeps track of all resources you've downloaded. This helps you:
- Keep track of what you've studied
- Quickly identify resources you've accessed
- Monitor your learning progress

## Account Management

### Changing Your Password

1. Click on your user icon in the top-right corner
2. Select **Change Password** from the dropdown menu
3. Enter your current password
4. Enter your new password (minimum 6 characters)
5. Confirm your new password
6. Click **Change Password**

### Logging Out

1. Click on your user icon in the top-right corner
2. Select **Logout** from the dropdown menu

## Navigation

- **Dashboard Button**: Visible on all pages when logged in (except the dashboard itself)
- **Back Button**: Available on resource pages to navigate back to previous selections
- **Logo**: Click the Minimal Notes logo to return to the homepage

## Available Subjects and Chapters

### Maths
- Chapters: 1, 2, 3, 4, 5, 6, 7, 8

### Physics
- Chapters: 1, 2, 3, 4, 5, 6

### Chemistry
- Chapters: 1, 2, 3, 4, 5

### Geography
- Chapters: 1, 2, 3, 4

### History
- Chapters: 1, 2, 3, 4, 5

## Tips for Best Experience

1. **Use a Modern Browser**: For best performance, use the latest version of Chrome, Firefox, Safari, or Edge
2. **Enable Pop-ups**: Allow pop-ups for PDF preview functionality
3. **Check Console**: If you need to test access codes, open the browser console (F12) to see the expected codes
4. **Download for Offline**: Download resources to access them offline
5. **Track Your Progress**: Use the download history to monitor your study progress

## Troubleshooting

### Can't Login?
- Verify your username and password are correct
- Ensure you've created an account first
- Check that your password meets the minimum length requirement (6 characters)

### Access Code Not Working?
- Ensure you're entering the code in uppercase
- Check the browser console for the expected access code
- Verify you're entering the code for the correct resource

### PDF Not Loading?
- Check your internet connection
- Ensure pop-ups are enabled in your browser
- Verify the PDF file exists in the `/public/pdfs/` directory
- Try refreshing the page

### Download History Not Updating?
- Ensure you're logged in
- Try logging out and back in
- Clear your browser cache if the issue persists

## Data Storage

All user data is stored locally in your browser using localStorage. This means:
- Your data is private and stays on your device
- No server-side storage or tracking
- Clearing browser data will remove your account and history
- Data is not synced across devices

## Security

- Passwords are stored in localStorage (for demonstration purposes)
- In a production environment, implement proper password hashing
- Keep your password secure and don't share it with others
- Log out when using shared computers

## Adding PDF Files

To add PDF files to the application:

1. Navigate to the `/public/pdfs/` directory
2. Add your PDF files following the naming convention:
   - Notes: `{Subject}_{Chapter}.pdf` (e.g., `Maths_1.pdf`)
   - Question Bank: `{Subject}_{Chapter}_QB.pdf` (e.g., `Physics_2_QB.pdf`)
   - One Word: `{Subject}_{Chapter}_OW.pdf` (e.g., `Chemistry_3_OW.pdf`)
3. The application will automatically detect and serve the files

## Support

For issues or questions:
- Check this user guide first
- Review the troubleshooting section
- Check the browser console for error messages
- Ensure all PDF files are properly named and located

## Future Enhancements

Potential features for future versions:
- Backend database integration
- User profile customization
- Progress tracking and analytics
- Bookmarking favorite resources
- Search functionality
- Mobile app version
- Social features (study groups, sharing)

---

**Version**: 1.0  
**Last Updated**: 2025-12-09

Enjoy your learning journey with Minimal Notes! 📚
