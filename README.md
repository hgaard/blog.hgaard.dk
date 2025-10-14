# blog.hgaard.dk

A personal blog built with Hugo static site generator, featuring the minimalistic Cactus theme.

## Overview

- **URL**: <https://blog.hgaard.com/>
- **Generator**: Hugo v0.151.0+
- **Theme**: hugo-cactus-theme (vendored)
- **Deployment**: GitHub Pages (output to `/docs` directory)

## Prerequisites

- **Hugo** (v0.151.0 or later)

  ```bash
  brew install hugo
  ```

## Getting Started

### Clone the repository

```bash
git clone https://github.com/hgaard/blog.hgaard.dk.git
cd blog.hgaard.dk
```

### Local Development

Start the Hugo development server:

```bash
hugo server
```

The site will be available at `http://localhost:1313` with live reload enabled.

To include drafts in the development server:

```bash
hugo server -D
```

## Content Management

### Creating a New Blog Post

```bash
hugo new blog/my-new-post.md
```

This creates a new post in `content/blog/` with the following front matter:

```yaml
---
title: "My New Post"
date: 2025-10-14
draft: true
---
```

### Content Structure

```text
content/
├── about.md              # About page
├── blog/                 # Blog posts
│   └── *.md
├── drafts/               # Draft posts
│   └── *.md
└── images/               # Images for posts
```

### Front Matter

Each blog post should include front matter at the top:

```yaml
---
title: "Post Title"
date: 2025-10-14
draft: false
slug: "post-title"
description: "Brief description of the post"
---
```

## Building the Site

### Production Build

Build the site for production (outputs to `/docs` directory):

```bash
hugo --gc --minify
```

Options:

- `--gc`: Run garbage collection after build
- `--minify`: Minify the output HTML, CSS, and JS

### Clean Build

```bash
hugo --gc --cleanDestinationDir
```

## Configuration

Site configuration is managed in [config.toml](config.toml):

- **Site settings**: Title, base URL, language
- **Theme settings**: Colors, fonts, social icons
- **Navigation**: Menu items, about/resume links
- **Analytics**: Google Analytics, Disqus comments
- **Social links**: Twitter, GitHub, LinkedIn, Instagram

## Theme Customization

The theme is vendored in `themes/hugo-cactus-theme/`. Key customization points:

- **Layouts**: `themes/hugo-cactus-theme/layouts/`
- **CSS**: `themes/hugo-cactus-theme/static/css/`
- **Images**: `themes/hugo-cactus-theme/static/images/`

To customize the site appearance, you can:

1. Override theme files by creating matching files in the root `layouts/` directory
2. Add custom CSS in the theme's CSS directory
3. Use `customCSS` parameter in config.toml

## Deployment

This site uses GitHub Pages for hosting. The build output is in the `/docs` directory.

### Automated Deployment

1. Build the site:

   ```bash
   hugo --gc --minify
   ```

2. Commit and push changes:

   ```bash
   git add .
   git commit -m "Update blog"
   git push origin master
   ```

3. GitHub Pages automatically serves content from the `/docs` directory

## Project Structure

```text
.
├── archetypes/           # Content templates
├── content/              # All site content
│   ├── about.md
│   └── blog/            # Blog posts
├── docs/                # Hugo build output (GitHub Pages)
├── themes/              # Hugo theme
│   └── hugo-cactus-theme/
├── config.toml          # Site configuration
└── README.md
```

## Useful Commands

| Command | Description |
|---------|-------------|
| `hugo server` | Start development server |
| `hugo server -D` | Start server including drafts |
| `hugo new blog/post.md` | Create new blog post |
| `hugo --gc --minify` | Build for production |
| `hugo config` | Display site configuration |
| `hugo version` | Show Hugo version |

## Troubleshooting

### Build Errors

If you encounter build errors after updating Hugo:

1. Check Hugo version: `hugo version`
2. Review deprecated features in [Hugo release notes](https://github.com/gohugoio/hugo/releases)
3. Test build locally before pushing: `hugo --gc`

### Theme Issues

The hugo-cactus-theme has been updated for Hugo v0.151.0 compatibility. If you encounter issues:

1. Ensure you're using Hugo v0.151.0 or later
2. Check for deprecated template functions
3. Review the [Hugo documentation](https://gohugo.io/documentation/)

## Maintenance Notes

- **Theme Status**: The original hugo-cactus-theme is archived (no longer maintained since 2020). The vendored copy has been updated for modern Hugo compatibility.
- **Hugo Version**: Keep Hugo updated via `brew upgrade hugo`
- **Dependencies**: This project has no external dependencies beyond Hugo itself

## Resources

- [Hugo Documentation](https://gohugo.io/documentation/)
- [Hugo Cactus Theme](https://github.com/digitalcraftsman/hugo-cactus-theme)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)

## License

Content copyright © Jakob Højgaard. Theme licensed under MIT.
