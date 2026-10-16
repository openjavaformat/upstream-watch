# upstream-watch

Daily watch over two upstream repositories (google-java-format and
palantir-java-format) for ideas, fixes and regressions worth adopting in
open-java-format.

- `collect.py`: trusted collector. Runs on a schedule outside the agent
  sandbox, GET-only access to GitHub, writes a `data/` snapshot.
- `prompt.md`: instructions for the analysis agent. The agent reads the
  snapshot, has no network access, and writes local ticket files.

Security model: everything fetched from GitHub is untrusted data. The
agent has no credentials. Updating the prompt is manual: pull, read the
diff, copy it into the agent's workspace.
