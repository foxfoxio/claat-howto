summary: Create a codelab page with Codelabs command line tool (claat)
id: howto-md
categories: guide, howto
tags: howto, beginner
status: Draft
authors: foxfox dev team
feedback link: https://github.com/foxfoxio/claat-howto/issues

# Create a codelab page with Codelabs command line tool (claat)

## Overview

Duration: 1

This tutorial walks you through how to create a codelab page by using `claat` (Codelabs command line tool) and deploy it to server

### You will learn

- How to create a codelab source with markdown
- How to generate codelab static HTML files
- How to serve codelab locally

### Prerequisites

- Markdown editor, i.e. [Visual Studio Code](https://code.visualstudio.com/)
- Docker, see [docker docs](https://docs.docker.com/get-docker/)

## Create a Markdown file

Duration: 15

Create a file named `howto-codelab.md`. Open the file in your markdown editor.

### Formatting

Added __Codelab Metadata__ at the top of the file. Metadata, a key/value pair, provide information about the codelab page, i.e. summary, id, tags, status, authors, etc.

__Heading 1__ paragraph uses as a title the codelab.

```markdown
summary: Create a codelab tutorial page
id: tutorial
categories: guide
tags: howto, beginner
status: Published
authors: foxfox dev team
Feedback Link: https://github.com/foxfoxio/claat-howto/issues

# Create a codelab tutorial page
```

Within the steps of your codelab, use __Heading 2__, __Heading 3__, __Heading 4__ paragraph to organize you content

```markdown
## Overview
Duration: 1

### You will learn
- How to create a codelab source with markdown
- How to generate codelab static HTML files
- How to view the generated result

### Prerequisites
- Markdown editor
- Docker

## Getting start
Duration: 15

Lorem ipsum dolor sit amet

### Create a file
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco __laboris nisi ut__ aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum

### Formatting
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut _aliquip ex ea commodo_ consequat. Duis aute [irure dolor in](http://example.com) reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum

| Tables   |      Are      |  Cool |
|----------|:-------------:|------:|
| col 1 is |  left-aligned | $1600 |
| col 2 is |    centered   |   $12 |
| col 3 is | right-aligned |    $1 |

```

Use `Duration:` to annotates time estimates for each step. For last step, set the duration to be `0`

You can use markdown syntax for other formatting, i.e. hyperlink, image, code snippet, table, etc.

See [Codelab Formatting Guide](https://github.com/googlecodelabs/tools/blob/master/FORMAT-GUIDE.md) for the complete information

## Generate static HTML files

Duration: 5

Use `claat export` command to generate HTML files from the markdown file.

We will run claat in a docker container `foxfoxio/claat`, in order to avoid installing `Go`

```bash
docker run -it --rm -v $(pwd):/app foxfoxio/claat export howto-codelab.md
```

The output will be generated to directory as specified in `id` in codelab metadata, otherwise uses source path.

To use binary version directly, see [for more information](https://github.com/googlecodelabs/tools)

## Serve codelab locally

Duration: 5

Use `claat serve` command to create a http server locally.

```bash
  docker run --rm -v $(pwd):/app -p 9090:9090 foxfoxio/claat serve -addr 0.0.0.0:9090
```

Open a browser and navigate to `http://localhost:9090/tutorial`.

## Deployment

Duration: 1

You can deploy static HTML codelab files with the hosting provider you choose

- Firebase hosting
- Github page
- etc.

## Completed

Duration: 0

Happy coding ` _へ__(‾◡◝ )> `
