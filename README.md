# Bridge Public School Website

A Hugo-based website for Bridge Public School, deployed via GitHub Pages.

## Local Development

### Prerequisites

- [Hugo Extended](https://gohugo.io/installation/) (v0.142.0 or later)

### Running Locally

1. Clone the repository with submodules:
   ```bash
   git clone --recurse-submodules https://github.com/YOUR-USERNAME/bridgeps.git
   cd bridgeps
   ```

2. Start the development server:
   ```bash
   hugo server -D
   ```

3. Open http://localhost:1313 in your browser

### Building for Production

```bash
hugo --gc --minify
```

The built site will be in the `public/` directory.

## Content Management

### Adding News Posts

Create a new Markdown file in `content/news/`:

```bash
hugo new news/my-new-post.md
```

### Editing Pages

Content pages are in the `content/` directory:

- `content/_index.md` - Homepage
- `content/about/` - About section
- `content/academics/` - Academics section
- `content/admissions/` - Admissions page
- `content/contact/` - Contact page
- `content/news/` - News/announcements

### Configuration

Site configuration files are in `config/_default/`:

- `hugo.toml` - Main site settings
- `params.toml` - Theme parameters
- `menus/menu.en.toml` - Navigation menus

## Deployment

The site automatically deploys to GitHub Pages when changes are pushed to the `main` branch.

### Enabling GitHub Pages

1. Go to your repository Settings > Pages
2. Under "Build and deployment", select "GitHub Actions"
3. Push to `main` to trigger a deployment

## Theme

This site uses the [Hugo Clarity](https://github.com/chipzoller/hugo-clarity) theme.
