# Repository for ACM Foundations 2023 Website

## Contributing Guidelines

You may fork this repository or create a separate branch within the same repository to begin working.

To add content to a session, simply open `docs/` any folder within. Here you may edit the README.md files, add assets to the `asset` folder, to use within your README files.

To add a session, make a new folder in the same format of the existing folders. You must reference this folder in `mkdocs.yml` under `nav:` for it to reflect in the website.

### Local Deployment

This website runs on mkdocs, and uses the material theme. The instructions to run is simple, you need to have python installed, a venv is optional but recommended.

```
pip install mkdocs
pip install mkdocs-material
mkdocs serve
```

This will run the website, which can be opened locally.