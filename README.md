# Sample training courses

A static site: a landing page plus four Articulate Rise 360 sample courses (TC-101 to TC-104), each exported as Web output. GitHub Pages serves it directly, with no build step.

## Folder layout

```
courses-site/
  index.html          landing page that links the four courses
  .nojekyll           tells GitHub Pages to serve files as they are
  phishing/           TC-101 (index.html, assets/, lib/, runtime-data.js)
  passwords-mfa/      TC-102
  devices-email/      TC-103
  ai-tools/           TC-104
```

The exports are already in place. Each course's `index.html` sits directly in its folder.

## Test locally

Opening `index.html` by double-clicking shows a blank page in many browsers. Serve the folder over HTTP instead. From inside `courses-site`:

```
python3 -m http.server 8000
```

Then open http://localhost:8000.

## Publish with GitHub Pages

1. Create a public repository on GitHub, for example `courses`, under the `bushmage` account.
2. Upload or push the contents of this folder to the repository root, keeping `.nojekyll`.
3. In the repository, go to **Settings > Pages**. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, and save.
4. After a minute or two the site is live at `https://bushmage.github.io/courses/`.

## Optional: your own address

To serve the site at something like `courses.kylebushwriting.com`:

1. In **Settings > Pages**, enter the custom domain.
2. At your domain registrar's DNS settings, add a CNAME record for `courses` pointing to `bushmage.github.io`.
3. Turn on **Enforce HTTPS** once GitHub finishes checking the domain.

## Updating a course

Re-export from Rise (Publish > Web), delete the old files in that course's folder, copy in the contents of the zip's `content` folder, and push. Keep folder names the same so the links keep working.

## Notes

- The exports from a Rise trial carry a "Powered by Articulate" watermark across every lesson. To remove it, re-export from a paid Rise 360 subscription.
- Exports are public. There is no password option.
- Web output does not track completion or quiz scores. Use a SCORM export and a learning platform if you need tracking.
- If you rename a folder, update the matching link in `index.html`.
