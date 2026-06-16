# web-copy-cat

A powerful and efficient website cloning tool that enables you to download and clone entire websites locally for offline access, archiving, or development purposes.

## Description

**web-copy-cat** is a comprehensive web scraping and cloning solution designed to create perfect copies of websites. It intelligently downloads all pages, assets, styles, scripts, and media files while preserving the original structure and functionality. Perfect for developers, researchers, and content creators who need to work with websites offline.

## Features

- **Complete Website Cloning**: Downloads entire websites with all assets and resources
- **Asset Management**: Automatically handles images, stylesheets, JavaScript, fonts, and media
- **Link Preservation**: Converts external links to local references for offline navigation
- **Recursive Crawling**: Intelligently follows internal links up to configurable depth
- **Performance Optimized**: Fast downloads with concurrent requests
- **Flexible Output**: Multiple format options (HTML, single-file, etc.)
- **Customizable**: Configure depth, exclusions, and output preferences
- **Well Documented**: Comprehensive guides and examples

## Installation

### Prerequisites

- Node.js (v14.0.0 or higher)
- npm or yarn package manager
- Git
- At least 1GB free disk space (depending on target website size)

### Setup Steps

1. **Clone the repository**
   ```bash
   git clone https://github.com/privatekontrak47-stack/web-copy-cat.git
   cd web-copy-cat
   ```

2. **Install dependencies**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Configure the project**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

4. **Verify installation**
   ```bash
   npm run test
   ```

## Usage

### Basic Clone

Clone a website to your local machine:

```bash
# Simple clone to default directory
web-copy-cat clone https://example.com

# Clone with custom output directory
web-copy-cat clone https://example.com --output ./my-website

# Clone with specific depth (default: 3)
web-copy-cat clone https://example.com --depth 2
```

### Advanced Usage

```bash
# Clone with custom user-agent
web-copy-cat clone https://example.com --user-agent "Mozilla/5.0..."

# Clone specific subdirectory only
web-copy-cat clone https://example.com/blog --depth 2

# Clone with asset filtering
web-copy-cat clone https://example.com --include-images --exclude-videos

# Generate offline-ready version
web-copy-cat clone https://example.com --offline-mode

# Clone with concurrency limit (default: 5)
web-copy-cat clone https://example.com --concurrency 3

# Verbose logging
web-copy-cat clone https://example.com --verbose
```

### Configuration

Edit the `.env` file to customize default settings:

```env
# Default output directory
OUTPUT_DIR=./cloned-websites

# Default crawl depth
DEFAULT_DEPTH=3

# Concurrent requests
CONCURRENCY=5

# Request timeout (ms)
REQUEST_TIMEOUT=30000

# User-Agent string
USER_AGENT=web-copy-cat/1.0

# Enable logging
DEBUG=false

# Proxy settings (optional)
# HTTP_PROXY=http://proxy.example.com:8080
```

### Command Options

| Option | Description | Default |
|--------|-------------|---------|
| `--output, -o` | Output directory path | `./cloned-websites` |
| `--depth, -d` | Crawl depth (0 = single page) | `3` |
| `--timeout, -t` | Request timeout in ms | `30000` |
| `--concurrency, -c` | Concurrent requests | `5` |
| `--user-agent` | Custom User-Agent header | `web-copy-cat/1.0` |
| `--include-images` | Include image assets | `true` |
| `--include-css` | Include stylesheets | `true` |
| `--include-js` | Include JavaScript files | `true` |
| `--exclude-videos` | Skip video files | `false` |
| `--offline-mode` | Optimize for offline use | `false` |
| `--verbose, -v` | Verbose logging | `false` |
| `--dry-run` | Show what would be cloned | `false` |

## Examples

### Clone a Blog

```bash
web-copy-cat clone https://myblog.com --depth 3 --output ./my-blog-backup
```

### Archive a Documentation Site

```bash
web-copy-cat clone https://docs.example.com --depth 5 --offline-mode
```

### Clone Single Page with Assets

```bash
web-copy-cat clone https://example.com/page --depth 0 --include-images --include-css
```

### Preview Before Cloning

```bash
web-copy-cat clone https://example.com --dry-run --verbose
```

## Limitations & Considerations

- ⚠️ **JavaScript-Heavy Sites**: Dynamic content loaded via JavaScript may not be fully captured
- ⚠️ **Authentication**: Sites requiring login/authentication cannot be cloned without valid credentials
- ⚠️ **Large Sites**: Cloning very large websites may take considerable time and disk space
- ⚠️ **Terms of Service**: Always check website's ToS before cloning - respect robots.txt
- ⚠️ **Rate Limiting**: Some sites may block rapid requests; use `--concurrency 1` if needed
- ⚠️ **Relative URLs**: Internal links are converted to relative paths for offline use

## Contributing

We welcome contributions! Here's how to get involved:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. **Make your changes** and commit them
   ```bash
   git commit -m "Add your feature description"
   ```
4. **Push to your fork**
   ```bash
   git push origin feature/your-feature-name
   ```
5. **Submit a Pull Request** with a clear description of your changes

### Development Guidelines

- Follow the existing code style
- Write clear commit messages
- Add tests for new features
- Update documentation as needed
- Test with various website types before submitting PR

## Troubleshooting

### Clone is slow
- Reduce `--concurrency` value
- Check your internet connection
- The target site may be rate-limiting requests

### Missing assets
- Increase `--depth` value
- Check if assets are loaded dynamically (JavaScript)
- Verify `--include-images`, `--include-css`, `--include-js` flags

### "Access Denied" errors
- Check if site blocks automated requests (User-Agent)
- Review site's robots.txt
- Try with custom User-Agent: `--user-agent "Mozilla/5.0..."`

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

**Last Updated**: 2026-06-16

For more information, questions, or support, please open an issue on the [GitHub repository](https://github.com/privatekontrak47-stack/web-copy-cat).
