# How to publish this local repository on GitHub

1. Sign in as `HikmatGhathe` and create a **Public** repo named `Multi-Zone-Conveyor-TIA-Portal` at https://github.com/new .
2. Extract this ZIP locally; **upload the files inside** the `Multi-Zone-Conveyor-TIA-Portal` folder, not only the ZIP file. GitHub web UI: **Add file → Upload files → Commit changes**.
3. Ensure that `README.md` is at repository root. GitHub will render it automatically along with linked diagrams/screenshots.
4. Check direct link `https://github.com/HikmatGhathe/Multi-Zone-Conveyor-TIA-Portal` after publishing. This link is **not live before repository creation**.
5. Later export the real SCL code (complete interface) and `.zap21` archive from TIA Portal and add them under `source/tia-export/` and `tia-portal-project/`. Use Git/Git LFS for large archive files rather than the browser uploader if the archive exceeds size limits.
6. Before publishing review all screenshots/exports to make sure they contain no employer-internal data, login information, IPs intended to stay private or other confidential material. The included images have had Windows title bars removed where possible.

## Via Git commands instead of the browser

From inside the extracted folder, after you create the empty GitHub repository:

```bash
git init
git add .
git commit -m "Document Multi-Zone Conveyor TIA Portal portfolio"
git branch -M main
git remote add origin https://github.com/HikmatGhathe/Multi-Zone-Conveyor-TIA-Portal.git
git push -u origin main
```

Do **not** claim unexecuted PLCSIM tests as passed. Add simulation evidence and outcome videos later.