# CARLA Paper | Notes on Workflow 

Template: 
- Repository: \url{https://gitlab.lrz.de/AM/TUMlatex}
- School: CIT
- Chair: Robotics, Artificial Intelligence and Real-time Systems

## MacOS

### LaTeX setup

- Install LaTeX **compiler** for Mac: 
```bash
brew install texlive
# Or, for a more minimal install use basictex + install requirements
brew install --cask basictex
# Then install the required packages (may not be exhaustive)
sudo tlmgr update --self
sudo tlmgr install latexmk xetex fontspec xunicode
```

- Editor: [VSCode](https://code.visualstudio.com/) 

- VSCode LaTeX **typesetting, linting, etc.**: [LaTeX Workshop extension](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) is recommended for editing LaTeX documents.

- For **formatting**: [latexindent](https://github.com/cmhughes/latexindent.pl?tab=readme-ov-file). To use, `CMD + shift + P` (VSCode command palette) and search for "format document". To install, Simply use brew (should work in VSCode out-of-the-box):

```bash
brew install latexindent
```

### Citations

- **Citation manager**: Using [Zotero](https://www.zotero.org/)
```bash
brew install --cask zotero
```

- **Zotero plugin for VSCode**: [Citation Picker for Zotero](https://marketplace.visualstudio.com/items?itemName=mblode.zotero). This allows you to search and insert citations directly from Zotero into your LaTeX documents in VSCode using `alt + shift + Z`

- Requires **Better BibTeX**: [Installation instructions](https://retorque.re/zotero-better-bibtex/installation/)

- VSCode setting: in `settings.json`, add the following to set citations to use LaTeX format `\cite{<citation key>}` (instead of the default pandoc format `@<citation key>`):
```json
"zotero-citation-picker.port": "http://127.0.0.1:23119/better-bibtex/cayw?format=latex"
```

#### Zotero Settings

- Set **IEEE style**: 
  - In Zotero, goto `Preferences > Cite`, and select `IEEE` in the `Cite > Style Manager` window.
  - In `Preferences > Better BibTeX > Export` set `BibLaTeX style` to `IEEE`.

- Set **automatic export**: 
    - Right click your collection
    - Select `Export Collection...`
    - Choose `Better BibTeX` as the format
    - Check `Keep updated`
    - Choose your file in the file dialog
    - Click `Save`
    - If prompted, choose to replace the existing file

- Enable **drag & drop** for inserting citation keys: Under `Preferences > Quick Copy > Item Format`, choose `Better BibTeX Citation Key Quick Copy`

- **Omit fields**: Under `Preferences > Export > Fields`, set `Fields to omit from export (comma-separated)` to `file` (optionally later add things like `abstract,note,urldate`, etc.)

- Automatic **URL inserting**: Under `Preferences > Export > BibTeX` Set `Add URLs to BibTeX export` to `In the 'url' field`

#### Optional
- If needed, change LaTeX command from the default `cite` to something else (like `parencite`) under `Preferences > Quick-Copy > LaTeX command`

- Modify **citation key format** (`WARNING` Might mess up existing cites... might wanna back up your `.bib` file): Using default `auth.lower + shorttitle(3, 3) + year`