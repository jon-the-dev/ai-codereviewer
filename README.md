# ⚠️ **PROJECT MOVED TO V2** ⚠️

## 🚀 **NEW REPOSITORY**: [GitHub AI Autobot Action v2](https://github.com/jon-the-dev/github-ai-autobot-action)

**This repository has been superseded by a complete v2 rewrite with enhanced features.**

### ✨ **What's New in v2**
- **🔧 Enhanced Architecture**: Complete TypeScript rewrite with modern patterns
- **🤖 Multi-Provider Support**: Both OpenAI GPT and Anthropic Claude models
- **🔒 Enterprise Security**: Enhanced input validation and error handling
- **⚡ Better Performance**: Optimized processing with improved logging
- **📊 Professional UX**: Branded comments and clear status indicators

### 🎯 **Migration Guide**
Replace your workflow action reference:
```yaml
# Old (this repository)
uses: jon-the-dev/ai-codereviewer@main

# New (v2 repository) 
uses: jon-the-dev/github-ai-autobot-action@v2
```

**All existing configuration options are supported** - no breaking changes!

### 🔗 **Links**
- **New Repository**: https://github.com/jon-the-dev/github-ai-autobot-action
- **Documentation**: Complete setup guide and advanced examples
- **Issues**: Please create new issues in the v2 repository

---

## 📚 Original Documentation (Legacy)

> **Note**: The content below is for historical reference only. Please use the v2 repository for new projects.

# AI Code Reviewer

AI Code Reviewer is a GitHub Action that leverages OpenAI's APIs to provide intelligent feedback and suggestions on
your pull requests. This powerful tool helps improve code quality and saves developers time by automating the code
review process.

## Features

- Reviews pull requests using OpenAI's APIs.
  - Tested with: gpt-4, gpt-4o, o1, and o1-mini
- Provides intelligent comments and suggestions for improving your code.
- Filters out files that match specified exclude patterns.
- Easy to set up and integrate into your GitHub workflow.

## Setup

1. To use this GitHub Action, you need an OpenAI API key. If you don't have one, sign up for an API key
   at [OpenAI](https://beta.openai.com/signup).

2. Add the OpenAI API key as a GitHub Secret in your repository with the name `OPENAI_API_KEY`. You can find more
   information about GitHub Secrets [here](https://docs.github.com/en/actions/reference/encrypted-secrets).

3. Create a `.github/workflows/main.yml` file in your repository and add the following content:

```yaml
name: AI Code Reviewer

on:
  pull_request:
    types:
      - opened
      - synchronize
permissions: write-all
jobs:
  review:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout Repo
        uses: actions/checkout@v3

      - name: AI Code Reviewer
        uses: mrc0der/ai-codereviewer@main
        with:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
          # OPENAI_API_MODEL: "gpt-4o" # Defined a model or use the upstream action as an org action
          exclude: "**/*.json, **/*.md"
```

4. Replace `your-username` with your GitHub username or organization name where the AI Code Reviewer repository is
   located.

5. Customize the `exclude` input if you want to ignore certain file patterns from being reviewed.

6. Commit the changes to your repository, and AI Code Reviewer will start working on your future pull requests.

## How It Works

The AI Code Reviewer GitHub Action retrieves the pull request diff, filters out excluded files, and sends code chunks to
the OpenAI API. It then generates review comments based on the AI's response and adds them to the pull request.

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests to improve the AI Code Reviewer GitHub
Action.

Let the maintainer generate the final package (`yarn build` & `yarn package`).

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more information.
