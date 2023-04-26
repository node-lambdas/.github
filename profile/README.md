# Node Lambdas

![Node Lambdas](https://avatars0.githubusercontent.com/u/69599650?s=100&v=4)

## Introduction

`node-lambdas` is a collection of tiny Node.JS servers that implement common modules or services as API's for ease of composition.

**Why?**

Quite often I need to do simple tasks like formatting a JSON file or decoding a base64 string. Sometimes I need that on my phone or in a restricted environment.

## Using with @node-lambdas/cli

`@node-lambdas/cli` is a terminal script that pipes the input/output of your CLI commands to a cloud microservice via HTTPS.

The general idea of any function is the following:
```
input >> POST https://[service].jsfn.run/[function] >> output
```

For example: you have a JSON and you want to convert it to YAML from your terminal, but you don't want or cannot install a program for that.

```bash
cat file.yaml | fn yaml decode | tee file.json
```

## Can I use it with cURL?

Absolutely!

```bash
curl -X POST https://yaml.jsfn.run -d @file.json
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
