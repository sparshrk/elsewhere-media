# Binary files not yet pushed

The finished `rule-ep2-graduate-route.mp4` (1080x1920, 30fps, 27.8s, -14 LUFS) and `poster.jpg` exist locally in the
production repo at `films/rule-ep2-graduate-route/` but could not be pushed to this GitHub repo in this session:
the available GitHub MCP tools (`create-or-update-file`, `push-files`) transmit `content` as literal text and do
not base64-decode it (verified by a roundtrip test: a base64 string was stored on GitHub as the literal base64
text, not the decoded binary). No authenticated `git`/`gh` CLI credential was available in this sandbox
(`GH_TOKEN`/`GITHUB_TOKEN` were empty; the `gh` CLI itself is disabled here) to push the real binary via git.
A human with push access (or a tool/token that can carry binary content) needs to copy these two files in from
the production machine. Everything else in this episode (treatment, facts, credits, subtitles, captions) is
pushed as real text in this same commit.
