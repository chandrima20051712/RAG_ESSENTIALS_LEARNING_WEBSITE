# RAG_ESSENTIALS_LEARNING_WEBSITE
Interactive, browser-based RAG lesson for exploring chunking, retrieval, embeddings, prompt assembly, evaluation, and safe fallbacks without a backend or API key.
Link: https://jazzy-beignet-78fda3.netlify.app/
# RAG Rescue

RAG Rescue is a self-contained, interactive 45-minute lesson about Retrieval-Augmented Generation (RAG). Learners explore chunking, retrieval, embeddings, prompt assembly, evaluation, citations, and safe fallbacks through a browser-based simulation.

There is no build step, backend, API key, or account required.

## Live Demo

Open `index.html` directly in a modern browser, or deploy the project folder to any static host such as Netlify, GitHub Pages, or Azure Static Web Apps.

For the most reliable embeddings experience, serve the folder over HTTP instead of opening the file directly:

```bash
python -m http.server 8000
```

Then visit <http://localhost:8000>.

## What You Can Explore

- A guided 10-chapter course with a 45-minute core path
- Adjustable chunk size and overlap, with a visual chunk preview
- Lexical retrieval using weighted word overlap and cosine similarity
- Optional real in-browser embeddings using `Xenova/all-MiniLM-L6-v2`
- A semantic similarity meter for comparing phrases
- Retrieval simulations and a small labelled test bench
- Prompt construction from instructions, evidence, questions, and source IDs
- Query rescue activities for vocabulary mismatches
- Citation support and grounded-answer exercises
- Workshop tabs for technical checks, teaching design, evaluation, and application planning
- JSON and Markdown exports for learning notes and application plans
- Reduced-motion support, keyboard-friendly controls, responsive layouts, and saved progress

## How It Works

| Component | Implementation |
| --- | --- |
| Chunking | Local word-window chunking with adjustable size and overlap |
| Lexical search | Weighted word overlap with cosine similarity, computed in the browser |
| Embedding search | `Xenova/all-MiniLM-L6-v2` through Transformers.js, 384-dimensional vectors, mean pooling, and cosine similarity |
| Prompt preview | Real string assembly from the selected blocks |
| Answers | Source excerpts and scripted teaching examples; no generated answer is returned |
| Vector database | Explained visually, but no hosted vector database or ANN index is connected |
| Evaluation | A tiny teaching set for document hit and sentence coverage, not a production benchmark |

The embeddings model is downloaded from jsDelivr the first time Embeddings mode is enabled. It is cached by the browser and may require roughly 23 MB of network access. Lexical mode works offline.

## Honest Limits

RAG Rescue is an educational simulator, not a production RAG service. It does not call an LLM, upload documents, provide production authentication, or guarantee that a retrieved passage is correct. Similarity scores are ranking signals, not probabilities or confidence values. The evaluation set is intentionally small, and the vector database, production monitoring, and access-control portions are illustrated rather than implemented.

Do not enter confidential or personal information into the demo.

## Project Files

| File | Purpose |
| --- | --- |
| `index.html` | Complete standalone lesson and application |
| `README.md` | Project documentation |
| `Upgrade_Installer.html` | Browser-only installer for adding the older workshop add-on to a previous lesson build |
| `rubric-enhancements.js` | Optional legacy workshop add-on used by the installer |
| `RAG_Rescue.html` | Earlier standalone lesson artifact |
| `README.txt` | Historical implementation and handoff notes |
| `README_Upgrade.txt` | Historical upgrade instructions |

Use the current `index.html` as the normal entry point. Do not load `rubric-enhancements.js` alongside it unless you are intentionally working with the older upgrade workflow; the current page already contains the workshop experience.

## Saved Data

The lesson stores progress, the reduced-motion preference, the last chapter, and planner fields in browser `localStorage` under:

```text
rag-rescue-mascot-v4
```

Use **Restart Course** inside the lesson to reset course progress. Clearing site data also removes the locally saved state.

## Suggested Learning Path

1. Start with the short scenario and choose the evidence that should answer it.
2. Explore how preparation, chunking, retrieval, prompt assembly, and answering fit together.
3. Change chunk boundaries and compare lexical retrieval with embeddings.
4. Run the retrieval simulator and labelled test bench.
5. Build a grounded prompt and inspect citation support.
6. Finish with the practical application planner and safe fallback.

## Development

This is intentionally a no-build HTML project. Edit `index.html`, then refresh the browser. No package installation is required.

Before sharing a change, check the main course flow in desktop and mobile widths, test Lexical mode with the network disabled, test Embeddings mode with a network connection, and verify keyboard navigation and reduced motion.

## Deployment

Deploy the project folder as a static site with `index.html` at the site root. There is no build command and no server-side configuration. If the host supports clean URLs, configure its fallback behavior only if you add additional pages later.

## License

No license file is currently included. Add a license before distributing or accepting external contributions.

