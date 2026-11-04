# Project K

> A context-aware coding agent that helps you build, debug, review, learn, and plan — with your voice and project memory in the loop.

Project K is a focused coding workspace for developers who want more than a blank chat window. It combines a set of intentional coding modes with voice dictation and a visual memory graph so the agent can keep useful context close to the work.

## What is included

The current release is a zero-dependency browser prototype that demonstrates the product experience:

- **Five coding modes**
  - **Build** — turn an idea into a practical implementation.
  - **Debug** — trace symptoms back to the root cause.
  - **Review** — find risks and improve code with precise feedback.
  - **Learn** — explain unfamiliar code and concepts clearly.
  - **Plan** — break complex work into an executable sequence.
- **Voice dictation** — speak a prompt directly into the composer through the browser's Web Speech API.
- **Context-aware pairing** — a conversation surface that exposes the active mode and loaded context.
- **Memory graph** — a visual map of the current task's relationships to tokens, caching, errors, and tests.
- **Saved memories** — project decisions, conventions, and preferences that can be promoted into future context.
- **Responsive interface** — works on desktop and adapts to smaller screens.

## Run locally

No package manager or build step is required.

```bash
git clone https://github.com/palamakulameghanadhgoud/project-k.git
cd project-k
```

Open `index.html` in a browser, or serve the folder locally:

```bash
# Python 3
python -m http.server 8000
```

Then visit [http://localhost:8000](http://localhost:8000).

Voice dictation requires a browser with Speech Recognition support, such as a recent Chrome or Edge build. The browser may ask for microphone permission. The prototype does not send audio anywhere.

## Project structure

```text
project-k/
├── index.html    # Application layout and accessible UI markup
├── styles.css    # Dark workspace theme and responsive layout
├── app.js        # Modes, chat composer, memory actions, and voice input
├── README.md     # Product and developer documentation
└── .gitignore    # Keeps unrelated workspace checkouts out of this repo
```

## How to use it

1. Select a mode at the top of the workspace.
2. Type a request into the composer, or select **Voice** and dictate one.
3. Use **Add context** in a future integration to attach files, symbols, or prior decisions.
4. Explore the memory graph to understand which project knowledge is informing the current task.
5. Save durable decisions as memories instead of repeating them in every session.

The current chat and memory controls are intentionally lightweight UI interactions. They provide the foundation for wiring a real model, repository index, and persistent memory service.

## Product architecture

Project K is designed around three cooperating layers:

1. **Agent layer** — selects a mode-specific system prompt and coordinates tools such as file search, patching, testing, and terminal execution.
2. **Context layer** — retrieves relevant code, recent conversation, repository conventions, and saved decisions within a bounded context window.
3. **Memory layer** — stores durable facts as a graph of entities and relationships, allowing future sessions to retrieve why a decision was made rather than only what was typed.

The interface in this repository is the first layer of that experience. It keeps the front end dependency-free so the product direction can be evaluated before committing to a framework or backend.

## Roadmap

- [ ] Connect the chat composer to a streaming model API.
- [ ] Add repository selection, file search, and safe patch previews.
- [ ] Persist sessions and memories in a local database.
- [ ] Index symbols and relationships into a real project graph.
- [ ] Add command approval, sandboxing, and an audit log for agent actions.
- [ ] Add a desktop shell with global push-to-talk voice capture.
- [ ] Add automated tests for mode behavior, memory retrieval, and tool permissions.

## Contributing

Keep changes focused and preserve the no-build-step developer experience unless a dependency is justified by a real product capability.

1. Create a branch from `main`.
2. Make a focused change.
3. Test the interface in a modern browser.
4. Update this README when behavior or setup changes.
5. Open a pull request with screenshots for visual changes.

## License

Project K does not currently declare a license. Add one before distributing or accepting external contributions.
