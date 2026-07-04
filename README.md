# CMM201 Learning Guide Website

A single-page learning guide website for **CMM201 — Material and Surface Texture Studies**, School of Information and Communication Technology, Asia e University (AEU). The guide adapts the course's texturing syllabus for a **Blender 4.5 LTS / 5.x (2025+)** workflow and curates 28 YouTube tutorials across the seven course topics.

**Lecturer:** Mohd Faiz Alias
**Semester:** May 2026
**Design style:** Creative Retro — Vintage Print (aged cream paper, letterpress slab type, ticket stubs, rubber stamp, sepia photo cards)

---

## 1. What's in the box

| File | Description |
|---|---|
| `cmm201-learning-guide.html` | The entire website — HTML, CSS and JavaScript in one self-contained file. The AEU logo is embedded as base64, so no image folder is needed. |
| `README.md` | This file. |

There are no build steps, no frameworks, no dependencies to install. The only external requests the page makes are to Google Fonts (typefaces) and `img.youtube.com` (video thumbnails).

---

## 2. Page sections

The site is a single page with a sticky navigation bar and smooth scrolling. Sections in order:

1. **Hero** — AEU logo, course title, and a meta strip (course code, 3 credit hours, 7 topics, 28 videos), with a rotating "Approved Syllabus" stamp.
2. **Subject Details** — specimen-label table: title, code CMM 201, credit hours, pre-requisite, lecturer, office, e-mail, software focus and full course synopsis.
3. **Course Objectives** — the four official objectives, numbered in Roman numerals.
4. **Learning Outcomes** — the four CLOs, each tagged with its Bloom's Taxonomy level (CLO1 C2, CLO2 C4, CLO3 C2, CLO4 C1).
5. **Course Assessment** — ticket-stub cards: Assignment 1 Part A (30%), Part B (40%), Final Project (30%).
6. **Case Study** — the Final Project brief: the *SDG Awareness Asset Pack* (3–5 game-ready textured props built from real-world surface observation, mapped to CLO2), with suggested SDG themes.
7. **Seven Topics** — each topic shows its number, title, learning outcomes, a short blurb and **4 curated YouTube tutorial cards** (28 total).
8. **Footer** — AEU logo, lecturer credit, course identification.

---

## 3. The 28 curated tutorials

Each video card links directly to YouTube in a new tab and shows the title, channel/type, and year. Videos from **2025–2026 (Blender 4.5 LTS / 5.0)** carry a green year badge; a small number of evergreen classics (Blender 3.x–4.x) fill gaps where the technique is unchanged in current Blender.

| Topic | Focus | 2025+ videos |
|---|---|---|
| 1 | Reading Surfaces — styles, materials & shader basics (Principled BSDF, Blender 4.5/5.0 features) | 4 of 4 |
| 2 | Visual Communication & UV Unwrapping | 2 of 4 |
| 3 | Defining Materials — image maps vs procedural maps (PBR, node networks) | 1 of 4 |
| 4 | Defining Shaders — bump, normal & displacement maps, seamless tiles | 0 of 4 (classics; technique unchanged) |
| 5 | Digital Lights & Lighting — three-point, HDRI, sky environments | 3 of 4 |
| 6 | 3D Texturing Techniques — texture painting, layers, projection | 1 of 4 |
| 7 | Effects & Rendering — Eevee course, render speed, render passes, depth of field | 4 of 4 |

All links were sourced from live web search results and verified working at publication time. If a creator ever removes a video, search its card title on YouTube for a re-upload, then update the link (see §5.3).

---

## 4. Running the site

**Locally:** double-click `cmm201-learning-guide.html` — it opens in any modern browser (Chrome, Edge, Firefox, Safari). No server needed.

**On a web host / LMS:** upload the single HTML file anywhere static files are served, e.g.:

- **AEU LMS / Moodle** — upload as a File resource, or paste into a Page resource.
- **GitHub Pages** — rename to `index.html`, push to a repo, enable Pages.
- **Netlify / Vercel** — drag-and-drop the file into a new site.

Because everything is embedded, the file can also be e-mailed or shared on a drive and will render identically.

---

## 5. Customisation guide

Open the HTML file in any text editor. Everything is in one place.

### 5.1 Colours (design tokens)

At the top of the `<style>` block:

```css
:root{
  --paper:#F1E7D0;    /* page background (aged cream)   */
  --paper-deep:#E7D9BC;/* alternate section background  */
  --ink:#2B2118;      /* text / borders (letterpress)   */
  --rust:#B0402A;     /* primary accent (poster red)    */
  --mustard:#D9A441;  /* secondary accent               */
  --teal:#3E6B5E;     /* tertiary accent / badges       */
  --card:#FAF3E1;     /* card background                */
}
```

Change any hex value and the whole site follows.

### 5.2 Course facts

- **Credit hours** — set to `3` (the standard for this course level; the source syllabus does not state it). Appears twice: in the hero meta strip and in the Subject Details table. Search for `Credit Hours` to edit both.
- **Lecturer / semester / contact** — search for `Mohd Faiz Alias`, `May 2026` or `sict.coordinator` and edit in place.
- **Assessment weights** — edit the `.ticket` blocks in the Assessment section.

### 5.3 Swapping a video

Each card is one `<a class="vid">` block. To replace a video you only need the new YouTube ID (the part after `watch?v=`):

1. Replace the ID in the `href`.
2. Replace the same ID in the thumbnail URL: `https://img.youtube.com/vi/<ID>/hqdefault.jpg`.
3. Update the `.vtitle`, channel and year text. Add `<span class="badge-new">2025</span>` inside the title for 2025+ releases, or remove it for older ones.

### 5.4 Adding a topic

Copy an entire `<div class="topic reveal"> … </div>` block, change the number in `<div class="no">`, the heading, outcomes line, blurb and the four cards. The grid, hover effects and reveal animation apply automatically.

### 5.5 Replacing the logo

The AEU logo is embedded twice (hero and footer) as `data:image/png;base64,…`. Replace the base64 string with your own (`base64 -w0 logo.png` on Linux/macOS), or swap the whole `src` for a normal image path if you prefer an external file.

---

## 6. Features & behaviour

- **Sticky nav with scroll-spy** — the current section is highlighted as you scroll.
- **"Develop the photograph" hover** — video thumbnails render in sepia and fade to full colour on hover, echoing the course's photo-reference workflow.
- **Scroll-reveal animations** — sections fade in on entry; fully disabled when the visitor has `prefers-reduced-motion` set.
- **Thumbnail fallback** — if a YouTube thumbnail fails to load, the card shows a solid colour panel instead of a broken image.
- **Responsive** — 4-column video grid on desktop, 2 on tablet, 1 on mobile; the stamp hides on small screens.
- **No tracking, no cookies, no analytics.**

---

## 7. Credits & notices

- Course content adapted from the official **CMM201 Material and Surface Texture Studies** syllabus, Asia e University. The original syllabus references Autodesk Maya; this guide maps the same seven topics to Blender 4.5+ equivalents.
- All tutorial videos remain the property of their respective YouTube creators (Blender Guru, Ryan King Art, CG Boost, Blender Secrets, Blender Inferno and others). The site links to them; it does not host or embed any video content.
- The AEU logo is the property of Asia e University and is used here for internal course-guide purposes.
- Typefaces: *Alfa Slab One*, *Crimson Pro* and *Special Elite* via Google Fonts (SIL Open Font License).
- Blender is free and open-source software by the Blender Foundation — download at [blender.org](https://www.blender.org/download/).

---

*CMM201 Learning Guide · May 2026 Semester · School of ICT, Asia e University*
