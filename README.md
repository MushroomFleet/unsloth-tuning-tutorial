# Unsloth Tuning Tutorial

An interactive, multi-page educational website that teaches LLM fine-tuning using [Unsloth](https://github.com/unslothai/unsloth) and Google Colab GPU runtimes — directly from Visual Studio Code.

## Live App

**[https://scuffedepoch.com/unsloth-tuning/](https://scuffedepoch.com/unsloth-tuning/)**

## About

This project transforms the official Unsloth VS Code + Colab guide into a rich, navigable web experience featuring:

- **Step-by-step tutorial** across 7 pages covering the full workflow
- **Interactive progress tracking** with localStorage persistence
- **Dark/light theme** toggle with Unsloth-inspired green accent design
- **Syntax-highlighted code blocks** with copy-to-clipboard
- **Expandable troubleshooting panels** for common issues
- **Responsive layout** for desktop, tablet, and mobile
- **Locally hosted screenshots** — no external image dependencies
- **Embedded video walkthrough** from the official Unsloth channel

### Tutorial Coverage

1. Prerequisites checklist
2. Installing the Google Colab extension in VS Code
3. Cloning & opening Unsloth fine-tuning notebooks
4. Connecting to a Colab GPU runtime (authentication, GPU selection, kernel)
5. Running the fine-tuning notebook
6. Troubleshooting & next steps

### Tech Stack

| Layer | Technology |
|---|---|
| Build | Vite 6 |
| Framework | React 19 |
| Language | TypeScript 5 |
| Routing | React Router v7 |
| Styling | CSS Modules + CSS Custom Properties |
| Icons | Lucide React |
| Syntax Highlighting | prism-react-renderer |

## TINS (There Is No Source)

This repository does not contain application source code. Instead, it includes the **TINS specification** — a comprehensive README that serves as a complete blueprint for reproducing the full implementation using any capable LLM.

See **[UNSLOTH-tuningwithcolab-web.md](./UNSLOTH-tuningwithcolab-web.md)** for the full specification including:

- All page content and component specifications
- Project structure and file layout
- Data models and context architecture
- CSS theme system and style guide
- Accessibility requirements
- Testing scenarios

To reproduce the source code, provide the TINS document to an LLM and follow the implementation instructions within.

## Source Material

The tutorial content is based on the official Unsloth documentation:

- [Unsloth VS Code + Colab Guide](https://unsloth.ai/docs/get-started/beginner-vscode)
- [Unsloth GitHub](https://github.com/unslothai/unsloth)
- [Unsloth Notebooks](https://github.com/unslothai/notebooks)

## License

MIT

---

## 📚 Citation

### Academic Citation

If you use this codebase in your research or project, please cite:

```bibtex
@software{unsloth_tuning_tutorial,
  title = {Unsloth Tuning Tutorial: Interactive educational website for LLM fine-tuning with Unsloth and Google Colab},
  author = {Drift Johnson},
  year = {2025},
  url = {https://github.com/MushroomFleet/unsloth-tuning-tutorial},
  version = {1.0.0}
}
```

### Donate:

[![Ko-Fi](https://cdn.ko-fi.com/cdn/kofi3.png?v=3)](https://ko-fi.com/driftjohnson)
