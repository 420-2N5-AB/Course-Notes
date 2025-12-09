# Course-Notes

Academic Jekyll site for Computer Networking course notes.

## Overview

This repository contains a complete Jekyll-based website for hosting networking course materials. The site includes structured modules covering fundamental to advanced networking topics.

## Course Modules

1. **Introduction to Computer Networks** - Network types, topologies, and OSI model
2. **Physical Layer** - Transmission media, encoding, and physical devices
3. **Data Link Layer** - MAC addressing, framing, and Ethernet
4. **Network Layer and IP Addressing** - IPv4/IPv6, subnetting, and routing
5. **Transport Layer** - TCP and UDP protocols
6. **Application Layer Protocols** - HTTP, DNS, email, and more

## Local Development

### Prerequisites

- Ruby 2.7 or higher
- Bundler
- Jekyll

### Setup

1. Clone the repository:
   ```bash
   git clone https://github.com/420-2N5-AB/Course-Notes.git
   cd Course-Notes
   ```

2. Install dependencies:
   ```bash
   bundle install
   ```

3. Build the site:
   ```bash
   jekyll build
   ```

4. Serve locally:
   ```bash
   jekyll serve
   ```

5. Visit `http://localhost:4000` in your browser

## GitHub Pages Deployment

This site is configured to work with GitHub Pages. To enable:

1. Go to repository Settings
2. Navigate to Pages section
3. Select the branch to deploy (e.g., `main`)
4. Save the settings

The site will be automatically built and deployed by GitHub Pages.

## Site Structure

```
Course-Notes/
├── _config.yml           # Jekyll configuration
├── _layouts/            # Page layouts
│   ├── default.html     # Main layout
│   └── module.html      # Module-specific layout
├── _modules/            # Course module content
│   ├── 01-introduction.md
│   ├── 02-physical-layer.md
│   └── ...
├── assets/              # Static assets
│   └── css/
│       └── style.css    # Custom styling
├── index.md             # Homepage
├── about.md             # About page
├── modules.md           # Module listing page
└── Gemfile              # Ruby dependencies
```

## Adding New Modules

To add a new module:

1. Create a new markdown file in `_modules/` directory
2. Use the following front matter template:

```yaml
---
title: Your Module Title
module_number: X
description: Brief description of the module
---

## Overview

Module content here...
```

3. The module will automatically appear in the modules list

## Customization

- **Site title and description**: Edit `_config.yml`
- **Styling**: Modify `assets/css/style.css`
- **Layouts**: Update files in `_layouts/` directory
- **Navigation**: Edit header_pages in `_config.yml`

## License

Educational content for academic use.
