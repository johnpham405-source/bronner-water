# Bronner Residence — Water Strategy Advisory

Self-contained static site (single index.html, all photos embedded). No build step.

## Deploy to Vercel
From this folder, either:
1. CLI:  npx vercel deploy --prod      (first run opens a browser to log in once)
2. Dashboard: go to vercel.com/new and drag this folder in.

Both produce a live https://<name>.vercel.app URL you can share.

## Maintenance note
`research-summary.html` is the AI-readable plain-HTML twin of `bronner-water-summary.md` (ChatGPT's link reader cannot parse `text/markdown` responses, and the interactive report is JS-rendered). Whenever the markdown changes, regenerate it:

```bash
python3 -c "
import html
md=open('bronner-water-summary.md',encoding='utf-8').read()
src=open('research-summary.html',encoding='utf-8').read()
head,_,_=src.partition('<pre>')
open('research-summary.html','w',encoding='utf-8').write(head+'<pre>'+html.escape(md)+'</pre>\n</main></body></html>\n')
"
```
