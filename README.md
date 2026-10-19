# Rania Hashem — Data Analyst Portfolio

A premium, fully responsive personal portfolio built with **HTML5, CSS3 and Bootstrap 5** (plus Bootstrap Icons and the Poppins font from CDNs). No frameworks, no build step.

```
rania-portfolio/
├── index.html
├── style.css
├── README.md
└── images/
    ├── rania-profile.jpg
    ├── sales-dashboard.jpg
    ├── customer-analysis.jpg
    └── business-analysis.jpg
```

> The four images included are **placeholders** (a neutral silhouette and chart-style thumbnails). Replace them with real ones.

---

## 1. Open and run the website locally

**Option A — double-click.** Open `index.html` in any modern browser (Chrome, Edge, Firefox, Safari). An internet connection is needed the first time so Bootstrap, Bootstrap Icons and Poppins can load from their CDNs.

**Option B — VS Code Live Server (recommended while editing).**
1. Open the `rania-portfolio` folder in VS Code.
2. Install the **Live Server** extension.
3. Right-click `index.html` → **Open with Live Server**. The page refreshes automatically when you save.

**Option C — Python's built-in server.**
```bash
cd rania-portfolio
python -m http.server 8000
# then visit http://localhost:8000
```

---

## 2. Add or replace Rania's profile photo

1. Choose a clear, well-lit portrait. A **4:5 portrait ratio** (e.g. 800 × 1000 px) works best; the image is cropped with `object-fit: cover`, so other sizes also work.
2. Save it as **`rania-profile.jpg`**.
3. Put it in the `images/` folder, replacing the placeholder.

If the file is missing or the name is wrong, the page automatically shows a "Add your photo" placeholder instead of a broken image.

To use a different file name or a PNG, edit the `src` attribute in the hero section of `index.html`:

```html
<img src="images/rania-profile.jpg" alt="Portrait of Rania Hashem, Data Analyst" ...>
```

To change which part of the photo is kept when cropping, adjust `object-position` in `style.css` (`.photo-inner img`), e.g. `center 20%`.

---

## 3. Replace the sample text with real information

Search `index.html` for the comments that start with **`EDIT:`**. The main places to personalize are:

| Section | What to change |
|---|---|
| Hero | Headline, intro text, email link |
| About | The three biography paragraphs inside `<div class="bio">`, and the three feature cards |
| Skills | Add or remove `<li><span class="skill-tag">…</span></li>` items. No proficiency percentages are used on purpose; only list skills you can genuinely demonstrate. |
| Certifications | Every card is a placeholder (`[Provider name]`, `[Month, Year]`). Replace with real ones and delete the "Placeholder" label. Remove any card you don't have. |
| Education | Replace `[Degree]`, `[University Name]`, `[Faculty or Department]`, `[Year]` and the coursework tags |
| Contact | Email address, LinkedIn and GitHub links |

**Add your CV:** save your CV as `Rania-Hashem-CV.pdf` in the project's main folder (next to `index.html`). The "Download My CV" button already points to it. Until you add the file, the button will not download anything.

---

## 4. Add real project screenshots

1. Take a screenshot of each real dashboard or analysis (a **16:10 ratio**, about 1200 × 750 px, looks best).
2. Save them with these names in `images/` (or use your own names and update the `src`):
   - `sales-dashboard.jpg`
   - `customer-analysis.jpg`
   - `business-analysis.jpg`
3. Update the `alt` text so it describes the real screenshot.
4. Edit the project title, description and technology badges:
   ```html
   <ul class="tech-list list-unstyled">
     <li>Power BI</li><li>Excel</li><li>SQL</li>
   </ul>
   ```
5. Once a project is real, **remove the `Sample Project` tag** (`<span class="project-tag">`) and the note below the project cards that says these are sample projects.

To add a fourth project, copy one whole `<div class="col-lg-4 col-md-6"> … </div>` block inside the projects row.

---

## 5. Update LinkedIn, GitHub and email links

These links are placeholders. Use Find & Replace (Ctrl/Cmd + H) across `index.html`:

| Find | Replace with |
|---|---|
| `https://www.linkedin.com/in/your-username` | Rania's real LinkedIn profile URL |
| `https://github.com/your-username` | Rania's real GitHub profile URL |
| `rania.hashem@example.com` | Rania's real email address |

For each project, replace:
- **View Project** → `https://example.com/...` becomes the live dashboard, report or case-study link (for example a Power BI "Publish to web" link, a Tableau Public link, or a README on GitHub).
- **GitHub** → `https://github.com/your-username/<repo-name>` becomes the real repository URL.

---

## 6. Add actual certifications

Copy this block inside the certifications row for each real certificate:

```html
<div class="col-md-6 col-lg-3">
  <article class="cert-card h-100">
    <span class="cert-icon"><i class="bi bi-patch-check"></i></span>
    <h3>Certificate Name</h3>
    <ul class="cert-meta list-unstyled">
      <li><i class="bi bi-building"></i> Provider Name</li>
      <li><i class="bi bi-calendar-check"></i> Month, Year</li>
    </ul>
  </article>
</div>
```

Delete the `<span class="cert-status">Placeholder</span>` line and the placeholder note under the cards. You can also turn the title into a link to the credential. Browse icons at <https://icons.getbootstrap.com/>. Only list courses that have actually been completed.

---

## 7. Customize colors and typography

All theme settings are at the top of **`style.css`** inside `:root`:

```css
:root {
  --navy-900: #0b1b3a;   /* main dark navy */
  --teal:     #14b8a6;   /* accent 1 */
  --blue:     #2563eb;   /* accent 2 */
  --bg-alt:   #f4f8fc;   /* soft section background */
  --font-main: 'Poppins', system-ui, sans-serif;
}
```

- **Change colors:** edit the hex values above. Gradients, buttons, badges and icons update automatically.
- **Change the font:** pick a font at <https://fonts.google.com>, replace the Google Fonts `<link>` in the `<head>` of `index.html` (for example `Inter`), then update `--font-main` in `style.css`.
- **Change rounding and shadows:** adjust `--radius`, `--radius-lg` and `--shadow`.

---

## 8. Make the contact form actually send messages

The form validates input in the browser only. **A plain HTML page cannot deliver email by itself**, so a backend or an external form service is required. The easiest option is a free form service such as **Formspree** or **Getform**:

1. Create a form on the service and copy its endpoint URL.
2. In `index.html`, change the form tag:
   ```html
   <form id="contactForm" action="https://formspree.io/f/YOUR_FORM_ID" method="post" novalidate>
   ```
3. In the `<script>` at the bottom of `index.html`, remove `event.preventDefault();` and the demo success message, so the browser submits the form normally after validation passes (or send it with `fetch()`).

---

## 9. Publish it online (optional)

Free hosting options for static sites: **GitHub Pages**, **Netlify** or **Vercel**. Upload the whole `rania-portfolio` folder and use the resulting link on your LinkedIn profile and CV.

---

## Notes on honesty and accuracy

This template intentionally contains **no invented metrics, client counts, certifications or proficiency percentages**. The projects are labeled as sample portfolio projects. Keep it that way: replace the placeholders only with real, verifiable information.
