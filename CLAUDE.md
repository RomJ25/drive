# drive

Personal cross-computer transfer point for finished project deliverables.
Not for looks, not for prose docs — just for moving files between machines.

## Structure
- One top-level folder per finished project, named after that project's own
  source folder (e.g. `pulse`), not an improvised nickname.
- Each folder holds deliverables only: `/airdocx` `.docx` exports, demo
  screenshots/video, final build/HTML output. Never the source repo's full
  tree, `.git`, or `node_modules`.

## Moving a finished project in
`/airdocx` writes its `.docx` next to the source file by default — it does
not stage anything here on its own. When a project is ready to transfer,
copy its generated `.docx` (and any other deliverables) straight into
`drive/<project-slug>/` in one step. Don't stage through `~/Downloads` or
any intermediate folder first — that's how `~/Downloads/pulse-airdocx`,
`pulse-project`, and `pulse-scripts` ended up as three duplicate copies of
the same files.

## Video
Video extensions (`.mp4`/`.mov`/`.mkv`/`.avi`) are routed through Git LFS
(see `.gitattributes`) — plain git hard-rejects anything over 100MB, and
raw screen recordings on this machine run into multiple GB.

Compress before adding rather than committing raw recordings, e.g.:
```
ffmpeg -i in.mov -vcodec libx264 -crf 28 out.mp4
```
Free-tier LFS is 10 GiB storage + 10 GiB bandwidth/month (verified against
GitHub's docs 2026-09-12 — reconfirm if it's been a long time since). A
single uncompressed multi-GB recording can burn most of a month's bandwidth
in one pull; compressing keeps pulls fast and comfortably inside the quota.
