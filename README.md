# Text Reader

A modern, mobile-friendly web application for reading text documents with interactive word definitions powered by AI.

## Features

- 📖 **Text Reading**: Read text files with a clean, readable interface
- 🤖 **AI Definitions**: Click any word to get instant English definitions using Mistral AI
- 📄 **PDF Support**: Import and read PDF files with preserved formatting
- 📱 **Mobile-Friendly**: Responsive design optimized for mobile devices
- 📑 **Pagination**: Automatic pagination for long documents (80 lines per page)
- 💾 **Import/Export**: Import your own text/PDF files or export the current content
- ⚙️ **Customizable Prompts**: Customize the AI prompt used for word definitions
- 💾 **Auto-Save**: Remembers your current page position on refresh
- 🎨 **Modern UI**: Built with GitHub's Primer CSS design system

## How to Use

### Getting Started

1. **Start the local server**:
   ```bash
   python3 -m http.server 8000
   ```

2. **Open in browser**:
   - On your computer: `http://localhost:8000/index.html`
   - On your phone (same network): `http://[YOUR_IP]:8000/index.html`
     - Find your IP with: `ifconfig | grep "inet " | grep -v 127.0.0.1`

### Basic Usage

- **Read Text**: The app displays text content with clickable words
- **Get Definitions**: Click any word to see its English definition in a popup
- **Navigate Pages**: Use "Previous" and "Next" buttons at the bottom for long documents
- **Settings Menu**: Click the ⚙️ gear icon (top-right) to access:
  - **Import Text**: Upload `.txt` or `.pdf` files
  - **Export Text**: Download the current content as a text file
  - **Reset to Default**: Restore the default "Hello World" text
  - **AI Prompt Settings**: Customize the prompt used for word definitions

### Customizing AI Prompts

1. Open Settings → **AI Prompt Settings**
2. Edit the prompt in the textarea
3. Use `{word}` as a placeholder for the word being defined
4. Click **Save** to apply your custom prompt
5. Click **Reset to Default** to restore the original prompt

**Default Prompt**: `Give me a brief English definition of the word: {word}`

## Supported File Formats

- **Text Files** (`.txt`): Plain text files
- **PDF Files** (`.pdf`): PDF documents with formatting preservation

## Technical Details

- **Frontend**: Pure HTML, CSS, and JavaScript
- **AI Integration**: Mistral AI API for word definitions
- **PDF Processing**: PDF.js library for PDF text extraction
- **Storage**: LocalStorage for saving preferences and imported content
- **Design System**: GitHub Primer CSS

## Requirements

- Python 3 (for local server)
- Modern web browser with JavaScript enabled
- Internet connection (for AI definitions)

## Notes

- The app uses localStorage to remember your reading position and imported content
- PDF formatting is preserved by analyzing text positioning and spacing
- The settings button auto-hides when scrolling down for a cleaner reading experience
- All definitions are fetched from Mistral AI in real-time

## License

Free to use and modify.
