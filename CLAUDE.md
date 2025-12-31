# CLAUDE.md - AI Assistant Documentation

This document provides comprehensive guidance for AI assistants working with this codebase.

## Repository Overview

**Project Type:** Jekyll-based GitHub Pages personal blog
**Site Title:** 一枚码农边跑边读的故事 (A Programmer's Story of Running and Reading)
**Custom Domain:** rm404.net
**Primary Language:** Chinese (Simplified)
**Jekyll Version:** ~4.2
**Theme:** Minima ~2.5

### Purpose
This is a personal blog focused on:
- **Reading Notes** (啃书笔记): Book reviews, reading reflections, and knowledge synthesis
- **Running Journal** (跑路人生): Running experiences, training logs, and fitness journey
- **Talks** (演讲): Public speaking notes and presentations

## Directory Structure

```
proheng.github.io/
├── _config.yml              # Jekyll configuration
├── _layouts/                # Custom layout templates
│   └── post.html           # Post layout override
├── _posts/                  # Blog posts organized by category
│   ├── reading/            # Reading-related posts
│   ├── running/            # Running-related posts
│   └── talk/               # Speaking-related posts
├── assets/                  # Static assets (images, etc.)
│   ├── running/            # Running-related images
│   └── 失落的卫星/          # Book-specific assets
├── index.markdown           # Homepage
├── reading.markdown         # Reading posts index page
├── running.markdown         # Running posts index page
├── Gemfile                  # Ruby dependencies
├── Gemfile.lock            # Locked dependency versions
├── CNAME                   # Custom domain configuration
└── .gitignore              # Git ignore rules
```

## File Naming Conventions

### Blog Posts

**Format:** `YYYY-MM-DD-title.md`

**Examples:**
- `2024-09-13-为什么我要开这个网站.md`
- `2024-12-06-kick-off.md`
- `2025-01-23-精力管理-新理论.md`

**Rules:**
1. Date must be in ISO format (YYYY-MM-DD)
2. Title follows the date with a hyphen separator
3. Title should be descriptive and URL-friendly
4. Use hyphens for multi-word titles
5. File extension must be `.md`

### Category Organization

Posts MUST be placed in category-specific subdirectories:
- Reading posts: `_posts/reading/`
- Running posts: `_posts/running/`
- Talk posts: `_posts/talk/`

## Post Front Matter Structure

Every blog post MUST include YAML front matter at the top:

```yaml
---
layout: post
title: Post Title Here
categories: category_name
---
```

**Required Fields:**
- `layout`: Always use `post` for blog posts
- `title`: Post title (displayed as H1 on the page)
- `categories`: Must match the subdirectory name (reading, running, or talk)

**Example:**
```yaml
---
layout: post
title: 为什么我要开这个网站
categories: reading
---
```

## Content Writing Guidelines

### Language
- Primary language: Chinese (Simplified)
- Content should be written in clear, conversational Chinese
- Technical terms may use English when appropriate

### Formatting
- Use standard Markdown syntax
- External links should include `{:target="_blank"}` to open in new tabs
- Example: `[link text](url){:target="_blank"}`

### Common Content Patterns

**Reading Posts:**
- Often reference books from Douban (豆瓣)
- Include personal reflections and insights
- May contain quotes or key takeaways
- Focus on knowledge synthesis and personal growth

**Running Posts:**
- Training experiences and goals
- Physical and mental aspects of running
- May include metrics, images, and progress tracking
- Inspirational and reflective tone

## Jekyll Configuration

### Permalink Structure
```
/:categories/:year/:month/:day/:title.html
```

**Example:** A post with categories `reading` dated 2024-09-13 with title "为什么我要开这个网站" generates:
```
/reading/2024/09/13/为什么我要开这个网站.html
```

### Theme
The site uses the **Minima** theme with minimal customization:
- Custom post layout in `_layouts/post.html`
- Displays title and date before content
- Inherits from Minima's default layout

## Development Workflow

### Local Development

1. **Prerequisites:**
   ```bash
   # Ensure Ruby is installed (compatible with 3.4+)
   # Install bundler if needed
   gem install bundler
   ```

2. **Install Dependencies:**
   ```bash
   bundle install
   ```

3. **Run Local Server:**
   ```bash
   bundle exec jekyll serve
   ```
   Site will be available at `http://localhost:4000`

4. **Build Static Site:**
   ```bash
   bundle exec jekyll build
   ```
   Output in `_site/` directory (ignored by git)

### Git Workflow

1. **Create Feature Branch:**
   ```bash
   # Branch names should start with 'claude/' for CI/CD compatibility
   git checkout -b claude/feature-name-xxxxx
   ```

2. **Commit Changes:**
   ```bash
   git add .
   git commit -m "Descriptive commit message"
   ```

3. **Push to Remote:**
   ```bash
   # Always use -u flag for new branches
   git push -u origin branch-name
   ```

4. **Network Retry Policy:**
   - If push/pull fails due to network errors, retry up to 4 times
   - Use exponential backoff: 2s, 4s, 8s, 16s between retries

### Deployment

This is a GitHub Pages site that auto-deploys when changes are pushed to the main branch.

## Common Tasks for AI Assistants

### Creating a New Blog Post

1. **Determine Category:** Reading, running, or talk
2. **Generate Filename:** Use current date + descriptive title
   ```
   _posts/reading/2025-12-31-new-post-title.md
   ```
3. **Create File with Front Matter:**
   ```yaml
   ---
   layout: post
   title: Post Title
   categories: reading
   ---

   Post content here...
   ```
4. **Commit and Push:**
   ```bash
   git add _posts/reading/2025-12-31-new-post-title.md
   git commit -m "Add new reading post: Post Title"
   git push -u origin branch-name
   ```

### Updating an Existing Post

1. **Locate the Post:** Search in appropriate `_posts/` subdirectory
2. **Read the File:** Always read before editing
3. **Make Changes:** Preserve front matter and formatting
4. **Commit Changes:**
   ```bash
   git add _posts/category/YYYY-MM-DD-title.md
   git commit -m "Update post: brief description of changes"
   git push
   ```

### Adding Images/Assets

1. **Organize by Category:**
   - Running images: `assets/running/`
   - Book-related: `assets/[book-name]/`

2. **Use Descriptive Filenames:**
   - Chinese names are acceptable
   - Use hyphens or underscores for spaces

3. **Reference in Posts:**
   ```markdown
   ![Alt text](/assets/category/image-name.jpg)
   ```

### Creating Category Index Pages

Index pages use Jekyll's Liquid templating to list posts by category:

```liquid
{% for post in site.posts %}
  {% if post.categories contains "category_name" %}
    <li>
      <a href="{{ post.url }}">{{ post.title }}</a>
      <small>({{ post.date | date: "%Y-%m-%d" }})</small>
    </li>
  {% endif %}
{% endfor %}
```

## Configuration Files

### _config.yml
```yaml
title: "一枚码农边跑边读的故事"
permalink: /:categories/:year/:month/:day/:title.html
theme: minima
```

**Important:** Changes to `_config.yml` require server restart during development.

### Gemfile Dependencies

```ruby
gem "jekyll", "~> 4.2"
gem "minima", "~> 2.5"
gem "csv"               # Required for Ruby 3.4+
gem "logger"            # Required for Ruby 3.4+
gem "base64"            # Required for Ruby 3.4+

group :jekyll_plugins do
  gem "jekyll-timeago", "~> 0.13.1"
end
```

### .gitignore

```
_site/*     # Jekyll build output
.DS_Store   # macOS system files
```

## Troubleshooting

### Common Issues

1. **Build Failures:**
   - Check front matter syntax (YAML must be valid)
   - Ensure post filename follows date format
   - Verify all required gems are installed

2. **Missing Posts:**
   - Check post is in correct category subdirectory
   - Verify front matter `categories` matches directory
   - Ensure date in filename is not in the future

3. **Broken Links:**
   - Use relative paths for internal links
   - Verify asset paths match actual file locations

4. **Git Push Failures (403):**
   - Branch must start with `claude/` and end with matching session ID
   - Verify remote URL and authentication

## Best Practices for AI Assistants

### Before Making Changes

1. **Read Relevant Files First:** Never propose changes to unread code
2. **Understand Context:** Review recent posts for tone and style
3. **Check Existing Patterns:** Follow established naming and organization conventions
4. **Verify Category:** Ensure content matches the intended category

### When Creating Content

1. **Maintain Consistency:** Follow existing writing style and formatting
2. **Preserve Tone:** Keep the personal, reflective nature of the blog
3. **Use Proper Chinese:** Ensure correct grammar and natural phrasing
4. **Date Accuracy:** Use actual current date for new posts
5. **Meaningful Titles:** Create descriptive, engaging titles

### When Editing

1. **Minimal Changes:** Only modify what's necessary
2. **Preserve Structure:** Don't alter front matter unless required
3. **Keep History:** Don't remove StackEdit metadata comments
4. **Test Locally:** Build and preview before committing when possible

### Git Commits

1. **Descriptive Messages:** Clear explanation of changes
2. **Atomic Commits:** One logical change per commit
3. **No Uncommitted Changes:** Don't leave work half-done
4. **Follow Branch Naming:** Use `claude/` prefix for branches

## Security Considerations

### Sensitive Information

- No credentials or API keys should be committed
- Personal contact information should be minimal
- CNAME file contains only the domain name

### Public Repository

- This is a public GitHub Pages site
- All content is publicly accessible
- No private or sensitive information in posts

## Character Encoding

- **File Encoding:** UTF-8 (required for Chinese content)
- **Line Endings:** LF (Unix-style)
- **Text Editor:** Must support UTF-8 and Chinese characters

## External References

- **Jekyll Documentation:** https://jekyllrb.com/docs/
- **Minima Theme:** https://github.com/jekyll/minima
- **GitHub Pages:** https://pages.github.com/
- **Markdown Guide:** https://www.markdownguide.org/

## Version Information

- **Last Updated:** 2025-12-31
- **Jekyll Version:** 4.2.x
- **Ruby Compatibility:** 3.4+
- **Theme Version:** Minima 2.5.x

---

**Note for AI Assistants:** This documentation should be treated as the authoritative guide for working with this repository. When in doubt, refer to this file and inspect existing posts for patterns. Always prioritize consistency with existing content over introducing new patterns.
