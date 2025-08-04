# Ahmed Othman's Personal Blog

This repository contains the source code and content for [Ahmed Othman](https://blog.aothman.de) personal blog, built with [Hugo](https://gohugo.io/) static site generator.

## Features

- Built with Hugo static site generator
- DoIt theme for modern, responsive design
- Supports Markdown-based posts
- Search functionality
- Comments system with Giscus
- Responsive and accessible design

## Prerequisites

Before setting up this blog locally, ensure you have the following installed:

- **Git** (for version control and submodules)
- **Hugo Extended** (version 0.148.2 or higher)
- **Go** (optional, for Hugo modules)

## Installation

### 1. Install Hugo

#### On macOS (using Homebrew):
```bash
brew install hugo
```

#### On Windows (using Chocolatey):
```bash
choco install hugo-extended
```

#### On Linux (using Snap):
```bash
sudo snap install hugo
```

#### Manual Installation:
Download the latest Hugo Extended release from [Hugo Releases](https://github.com/gohugoio/hugo/releases) and follow the installation instructions for your operating system.

Verify installation:
```bash
hugo version
```

### 2. Clone the Repository

#### Option A: Clone with submodules (Recommended)
```bash
git clone --recurse-submodules https://github.com/amedhat3/blog-aothman.git
cd blog-aothman
```

#### Option B: Clone and initialize submodules separately
```bash
git clone https://github.com/amedhat3/blog-aothman.git
cd blog-aothman
git submodule update --init --recursive
```

### 3. Setup Git Submodules

This blog uses Git submodules for themes. If you cloned without `--recurse-submodules` or if submodules are not properly initialized:

```bash
# Initialize and update all submodules
git submodule update --init --recursive

# Verify submodules are properly loaded
git submodule status

# Check that theme files exist
ls -la themes/DoIt/
```

### 4. Troubleshooting Submodules

If you encounter issues with submodules on a new machine:

```bash
# Force update submodules
git submodule update --init --recursive --force

# Sync submodule URLs (if they changed)
git submodule sync --recursive

# Reset submodules to their tracked commits
git submodule foreach --recursive git reset --hard

# Update submodules to latest versions
git submodule update --remote --recursive
```

### 5. Clean Content (if needed)

If you see content reference citations like `:contentReference[oaicite:X]{index=X}` in the content, clean them:

```bash
# Remove AI-generated content references from all markdown files
find content -name "*.md" -exec sed -i '' 's/:contentReference\[[^]]*\]{[^}]*}//g' {} \;
```

## Development

### Start the Development Server

```bash
# Start Hugo development server
hugo server

# Include draft posts
hugo server --buildDrafts

# Bind to all interfaces (for external access)
hugo server --bind=0.0.0.0 --port=1313
```

The site will be available at `http://localhost:1313`

### Build for Production

```bash
# Build the site for production
hugo

# Build including drafts
hugo --buildDrafts

# Build with specific environment
hugo --environment production
```

The generated site will be in the `public/` directory.

## Project Structure

```
├── archetypes/          # Content templates
├── assets/              # CSS, images, and other assets
├── config/              # Hugo configuration files
│   ├── _default/        # Default configuration
│   └── production/      # Production-specific config
├── content/             # Blog content (Markdown files)
│   ├── about/           # About page
│   └── posts/           # Blog posts
├── data/                # Data files
├── layouts/             # Custom HTML templates
├── static/              # Static files (images, favicon, etc.)
├── themes/              # Hugo themes (Git submodules)
│   └── DoIt/            # DoIt theme
└── public/              # Generated site (created by Hugo)
```

## Configuration

The site configuration is split into multiple files in the `config/` directory:

- `_default/hugo.toml`: Main Hugo configuration
- `_default/params.en.toml`: Theme-specific parameters
- `_default/menu.en.toml`: Navigation menu configuration
- `production/`: Production-specific overrides

## Creating Content

### Create a new post:
```bash
hugo new posts/my-new-post/index.md
```

### Create a new page:
```bash
hugo new about/index.md
```

## Common Issues and Solutions

### Theme Not Found
```bash
# Ensure submodules are properly initialized
git submodule update --init --recursive

# Check if theme exists
ls -la themes/DoIt/
```

### Hugo Version Compatibility
This blog requires Hugo Extended version 0.148.2 or higher. If you encounter build errors:

```bash
# Check Hugo version
hugo version

# Update Hugo to latest version
brew upgrade hugo  # macOS
```

### Content Reference Citations
If you see `:contentReference[...]` in your content, clean them:

```bash
find content -name "*.md" -exec sed -i '' 's/:contentReference\[[^]]*\]{[^}]*}//g' {} \;
```

## License

Copyright (c) 2025 Ahmed Othman

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
