# interview-analyst

A Claude Code skill for qualitative UX research. It helps researchers move faster through interview transcripts — surfacing patterns, organizing quotes, and structuring a narrative draft — without replacing the researcher's judgment.

---

## Disclaimer

**This skill is a research aid, not a research analyst.**

It is designed to supplement your work as a researcher, not substitute it. AI-generated analysis is prone to error — it can misread tone, misattribute quotes, or miss meaning that requires human context. Everything this skill produces is a hypothesis, not a conclusion.

**You are responsible for:**
- Verifying every quote and citation against the source transcript before using it
- Cross-checking interpretations against your own notes and field memory
- Treating all output as a starting point that relies on and builds from your analysis — not the other way around

If the output contradicts your instincts, trust your instincts first. Then use the transcripts to arbitrate.

---

## What it does

- Reads transcript files (`.csv`, `.txt`, `.md`, `.vtt`, `.srt`) from a directory or individually
- Asks the researcher for their brief, early instincts, and preferred output style before starting
- Detects emotional signals, hedging language, frustration markers, and enthusiasm patterns
- Distinguishes what participants *say they do* from what their stories *reveal they actually do*
- Ensures all participants are represented with roughly equal coverage
- Frames findings as signals and interpretations, not conclusions — always with sample size acknowledged
- Follows the researcher's narrative lead; challenges when the data diverges, but defers to researcher judgment

### Output formats

| Command | Output |
|---|---|
| `/interview-analyst <path>` | Synthesis report in-conversation |
| `/interview-analyst /report` | DOCX report via pandoc |
| `/interview-analyst /deck` | PPTX slide deck via python-pptx |
| `/interview-analyst /journey` | Journey map (markdown or mermaid) |
| `/interview-analyst /arc` | Emotional arc diagram (ASCII or mermaid) |
| `/interview-analyst /quoteboard` | Annotated quote board grouped by theme |

---

## Installation

**One-liner:**
```bash
mkdir -p ~/.claude/skills/interview-analyst && \
  curl -o ~/.claude/skills/interview-analyst/SKILL.md \
  https://raw.githubusercontent.com/<your-username>/<your-repo>/main/interview-analyst/SKILL.md
```

**Or clone and copy:**
```bash
git clone https://github.com/<your-username>/<your-repo>.git
cp -r <your-repo>/interview-analyst ~/.claude/skills/
```

Then restart Claude Code. The skill will appear as `/interview-analyst`.

### Optional dependencies

Some output formats require additional tools:

- **DOCX reports** (`/report`): requires [pandoc](https://pandoc.org/installing.html)
- **PPTX decks** (`/deck`): requires [python-pptx](https://python-pptx.readthedocs.io) (`pip install python-pptx`)
- **Journey maps / arc diagrams**: plain text output works without any dependencies; mermaid rendering requires a compatible viewer

---

## Usage

### Analyze a directory of transcripts
```
/interview-analyst /path/to/transcripts/
```
The skill will list all transcript files found and ask you to confirm before proceeding.

### Analyze a single file
```
/interview-analyst path/to/interview.csv
```

### Analyze multiple specific files
```
/interview-analyst p1.txt p2.txt p3.txt
```

### Generate outputs from a completed analysis
```
/interview-analyst /report
/interview-analyst /deck
/interview-analyst /quoteboard
```

### What to expect at the start

Before analyzing, the skill will ask you three questions in a single message:

1. **Research brief** — What was the goal of this research? What questions were you trying to answer?
2. **Researcher's lens** — Any early instincts, mental models, or findings you want surfaced or explored?
3. **Output style** — Plain and direct, or more formal/academic? (Default: plain)

Your answers shape the entire analysis. The more specific you are, the more useful the output.

---

## Supported transcript formats

| Format | Notes |
|---|---|
| `.csv` | Expects columns: `Speaker`, `Time`, `Transcript` (or similar) |
| `.txt` | Plain text, any structure |
| `.md` | Markdown-formatted notes or transcripts |
| `.vtt` / `.srt` | Subtitle/caption files from video recordings |

---

## Design principles

This skill was built with a specific philosophy. If you modify it, these are worth preserving:

- **Researcher autonomy first.** The researcher was in the room. Their judgment overrides AI interpretation.
- **Epistemic honesty always.** Never state findings as facts. Always acknowledge sample size. Treat every insight as a hypothesis.
- **Evidence before interpretation.** Every claim needs a citation and a participant count. No exceptions.
- **Equal participant representation.** No voice should dominate the analysis at the expense of others.
- **Distinguish description from interpretation.** Be precise about what was observed. Be humble about what it means.

---

## Contributing

Contributions welcome — especially from researchers who've used this in practice.

Good areas for improvement:
- Support for additional transcript formats
- Better handling of non-English transcripts
- Improved journey map and arc diagram outputs
- Prompt refinements based on real research use cases

Please open an issue before submitting a large change, so we can discuss approach first.

---

## License

Free to use and modify by researchers. Credit appreciated.

Please preserve the design philosophy when adapting this skill. If you have ideas for how to evolve it — reach out via GitHub: [@radha-nath](https://github.com/radha-nath)

---

*Built by Radha, product thinker, iterated with Claude Code.*
