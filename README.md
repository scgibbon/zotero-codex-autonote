# Zotero Codex Auto Note

This is a Zotero plugin for generating concise AI notes from PDF papers.

## Main Functions

- works on Zotero items with PDF attachments
- generates a Zotero child note automatically or manually
- uses Codex CLI as the summarization engine
- adds short useful Zotero tags
- links note content back to the paper
- can include extracted figure snapshots and equation-style formatting

## Note Structure

The generated note focuses on four sections:

1. Core Result
2. The Innovation Idea
3. Method
4. Parameter Detail

## Intended Workflow

1. Save a paper PDF into Zotero
2. Let the plugin process it, or trigger it manually
3. Read the generated note under that Zotero item
4. Use the note as a quick research summary with source links

## Important Limitation

The plugin depends on local tools already installed on the user machine:

- Codex CLI
- Python
- Poppler PDF tools
## What You Need

Before installing the plugin, make sure this computer has:

- Zotero 7
- Codex CLI
- Python 3
- Poppler PDF tools available in terminal:
  - `pdftotext`
  - `pdftoppm`
  - `pdfimages`

This plugin package does not bundle Codex, Python, or the PDF tools.

## Files In This Folder

- `zotero-codex-autonote.xpi`
- `requirements.txt`
- `INTRODUCTION.md`
- `INSTALL.md`

## Step 1: Install The Python Package

Open PowerShell in this folder and run:

```powershell
pip install -r requirements.txt
```

## Step 2: Check The Required Commands

Run these commands in PowerShell:

```powershell
codex --version
python --version
pdftotext -v
pdftoppm -v
pdfimages -v
```

If one of them fails, install or fix that tool before continuing.

## Step 3: Install The Zotero Plugin

1. Open Zotero.
2. Go to `Tools -> Plugins`.
3. Click the gear button.
4. Choose `Install Add-on From File...`
5. Select `zotero-codex-autonote.xpi`
6. Restart Zotero

## Step 4: First-Time Setup

After Zotero restarts:

1. Open the plugin preferences.
2. Make sure the `Codex executable path` is correct.
3. If Codex is already installed and auto-detection works, no change is needed.
4. If auto-detection fails, set the full path to `codex.cmd` or `codex.exe`.

## Step 5: Test The Plugin

Use one paper with a local PDF attachment.

You can test it in two ways:

- Save a new PDF into Zotero and let the plugin process it automatically
- Open or select an existing PDF item and trigger the plugin manually from the Zotero UI

Expected result:

- a child note is created under the Zotero item
- the note includes the four summary sections
- tags are appended to the parent item

## What The Plugin Does

For a Zotero item with a PDF, the plugin:

1. finds the PDF attachment
2. extracts paper content locally
3. calls Codex CLI once with structured content
4. creates a Zotero child note
5. adds a few smart tags

## If It Does Not Work

Check these first:

- `codex --version` works in PowerShell
- `python --version` works in PowerShell
- `pdftotext`, `pdftoppm`, and `pdfimages` work in PowerShell
- the Zotero item really has a local PDF attachment
- the Codex executable path in plugin settings is correct

## Notes

- The plugin is currently tested mainly on Windows.
- The `.xpi` is enough for installation, but not enough by itself to supply the external tools.
- No source-code modification should be needed on another Windows machine if the required tools are installed correctly.
