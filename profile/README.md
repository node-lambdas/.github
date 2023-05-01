# Node Lambdas

![Node Lambdas](https://avatars0.githubusercontent.com/u/69599650?s=100&v=4)

## Introduction

`node-lambdas` is a collection of tiny Node.JS servers that implement common NPM modules or HTTP services as API's for convenience.

**Why?**

Quite often I need to do simple tasks, like formatting a JSON file or decoding a base64 string.
Sometimes I need that on my phone or in a restricted environment.

## Using with @node-lambdas/cli

`@node-lambdas/cli` is a terminal script that pipes the input/output of your CLI commands to an HTTP server.

The general idea of any function is the following:

```
input >> POST https://[service].jsfn.run/[function] >> output
```

For example: you have a JSON and you want to convert it to YAML, but you cannot install a program for that.

```bash
cat file.json | fn yaml encode | tee file.yml
```

## Can I use it with cURL?

Absolutely!

```bash
curl -d @file.json https://yaml.jsfn.run/encode
```

### Examples

```bash
# convert JSON to YAML
cat your.json | fn yaml

# calculate the sha256 hash for the content of file.txt
cat file.txt | fn sha 256

# convert Markdown to HTML
cat README.md | fn markdown

```

## Available Node.js micro services

Use `fn discover` to get a list of available services.

> Missing a function? Open an issue and [request a new one](https://github.com/node-lambdas/discover/issues).
