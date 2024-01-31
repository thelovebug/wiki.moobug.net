# wiki.moobug.net

![GitHub Actions Workflow Status](https://img.shields.io/github/actions/workflow/status/thelovebug/wiki.moobug.net/hugo.yml)
![GitHub repo size](https://img.shields.io/github/repo-size/thelovebug/wiki.moobug.net)
![GitHub contributors](https://img.shields.io/github/contributors/thelovebug/wiki.moobug.net)
![GitHub stars](https://img.shields.io/github/stars/thelovebug/wiki.moobug.net)
![GitHub forks](https://img.shields.io/github/forks/thelovebug/wiki.moobug.net)
![Twitter Follow](https://img.shields.io/twitter/follow/thelovebug?style=social)
![Coffee status](https://img.shields.io/badge/coffee-strong_and_hot-red?logo=coffeescript)

This repo holds the files of the Moobug Wiki site [wiki.moobug.net](https://wiki.moobug.net).

This blog is built with [Hugo](https://gohugo.io/), one of the most popular and fast open-source static site generators.

## Set up the blog for local development

### Requirements

[Hugo](https://gohugo.io/) and [Git](https://git-scm.com/) must be installed and configured.

### Cloning

```bash
# Clone the repo
git clone git@github.com:thelovebug/wiki.moobug.net.git

# Pull the theme files (Git submodule)
git submodule update --init --recursive
```

### Updating

```bash
# Update the repo
git pull

# Update the theme files (Git submodule)
git submodule update --remote --merge
```

### Testing

```bash
# Start Hugo locally
hugo server -D --disableFastRender --bind 0.0.0.0 --baseURL http://<LAN_IP>:1313
# This will serve the blog to all LAN addresses, so tests can be made from multiple devices.
```
