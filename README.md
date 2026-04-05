# 🔍 Docfind Blog: Serverless WebAssembly Search

This repository contains the companion code for my blog post on building a lightning-fast, zero-server search engine using **WebAssembly** and **Rust**. 

It uses [docfind](https://github.com/microsoft/docfind), an open-source tool developed by the VS Code Engineering team, combined with a custom "Glassmorphism" premium UI to demonstrate how to handle massive search scale directly in the user's browser.

## ✨ Features
* **Zero Backend Costs:** 100% client-side search.
* **Lightning Fast:** Powered by a Finite State Transducer (FST) compiled to WebAssembly.
* **Premium UI:** A glassy, modern interface built with vanilla HTML/CSS.
* **Easy Integration:** No complex bundlers required (uses standard ES Modules).

## 🚀 Getting Started

Follow these steps to test the search engine on your local machine.

### 1. Clone the Repository
```bash
git clone [https://github.com/404rakshit/docfind-blog.git](https://github.com/404rakshit/docfind-blog.git)
cd docfind-blog
```

### 2. Install the `docfind` CLI
You need the official CLI tool to compile the raw data into a WebAssembly index.

**Mac/Linux:**
```bash
curl -fsSL [https://microsoft.github.io/docfind/install.sh](https://microsoft.github.io/docfind/install.sh) | sh
```
**Windows (PowerShell):**
```powershell
irm [https://microsoft.github.io/docfind/install.ps1](https://microsoft.github.io/docfind/install.ps1) | iex
```

### 3. Build the WebAssembly Index
This repository includes a large sample data file located at [`documents.json`](https://github.com/404rakshit/docfind-blog/blob/main/documents.json). This file contains the dummy data we will use to populate the search engine.

Run the following command to generate your WebAssembly files:
```bash
docfind documents.json public/search
```
*This command reads the `documents.json` file and outputs `docfind.js` and `docfind_bg.wasm` into the `public/search/` directory.*

### 4. Serve Locally
Because WebAssembly files must be fetched securely, **you cannot just double-click `index.html`**. You must serve the folder using a local web server.

If you have Node.js installed:
```bash
npx serve .
```
Or with Python:
```bash
python3 -m http.server 8000
```
*(Alternatively, use the "Live Server" extension in VS Code).*

Open your browser to the local address provided (e.g., `http://localhost:8000`), and start searching!

## 📂 Project Structure

* `index.html`: The main user interface, featuring the glassy CSS styling and the inline JavaScript module to initialize WebAssembly.
* `documents.json`: The raw sample data used to build the search index.
* `public/search/`: The target folder where the compiled `.wasm` and `.js` glue files are stored after running the CLI.

## 🏆 Credits & Resources

* **Original Engineering Blog:** [Building docfind: Fast Client-Side Search with Rust and WebAssembly](https://code.visualstudio.com/blogs/2026/01/15/docfind)
* **Official Microsoft Repo:** [microsoft/docfind](https://github.com/microsoft/docfind)
* **Interactive Demo:** [VS Code docfind Demo](https://microsoft.github.io/docfind/)