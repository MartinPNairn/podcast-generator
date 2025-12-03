# Podcast Feed Generator

A GitHub Action that converts a simple YAML file into a fully valid podcast RSS feed. Since YAML is much easier to write and maintain than XML, this action lets you manage your podcast metadata in a friendlier format.

## Usage

### Enable GitHub Pages

In your repository, navigate to **Settings → Pages** and set the source to the **main** branch. This will publish the contents of your main branch and provide a public URL. Make sure to copy that URL—you’ll need it in the next step.

### Create Your YAML File

Add a YAML file to your repository using the structure below:

```yaml
title: <Podcast Title>
subtitle: <Podcast Subtitle>
author: <Author Name>
description: <Podcast Description>
link: <GitHub Pages URL>
image: <Artwork URL or Path>
language: <Language, e.g. en-us>
category: <Podcast Category, e.g. Technology https://podcasters.apple.com/support/1691-apple-podcasts-categories>
format: <File format, e.g. audio/mpeg>
item:
  - title: <Episode Title>
    description: <Episode Description>
    published: <Publish Date e.g. Thu, 12 Jan 2023 18:00:00 GMT>
    file: <File path e.g. /audio/TFIT01.mp3>
    duration: <Duration e.g. 00:00:36>
    length: <File size e.g. 576,324>
  # Add additional episodes in the same format
```

### Example Workflow

You'll also need a GitHub Actions workflow to run the generator. Here is a basic example:

```yaml
name: Generate Feed
on: [push]
jobs:
  generate-feed:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repository
        uses: actions/checkout@v6
      - name: Run Feed Generator
        uses: martinpnairn/podcast-feed-generator@main
```

