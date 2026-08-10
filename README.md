# CAASPP school results explorer

A single-page tool for exploring California school-level CAASPP results. Every
school in the state as one dot; put any measure on either axis.

Data: California Department of Education / ETS, CAASPP research files.

## Publishing this

The whole site is `index.html` plus a `data/` folder. No build step, no server
code, no database. Everything runs in the visitor's browser.

### 1. Add the data

Download from https://caaspp-elpac.ets.org/caaspp/ResearchFileListSB and drop
the zips into `data/` unchanged — do not unzip them.

| File | Size | Unlocks |
|---|---|---|
| `sb_ca2025_1_csv_v1.zip` | 8 MB | English and math (required) |
| `sb_ca2025entities_csv.zip` | 1 MB | School and district names (required) |
| `cast_ca2025_1_csv_v1.zip` | 2 MB | Science |
| `sb_ca2024_1_csv_v1.zip` | 8 MB | Year-over-year change |
| School directory, TXT | 7 MB | Charter / magnet / online / referral school types |

The school directory is at
https://www.cde.ca.gov/schooldirectory/report?rid=dl1&tp=txt — use the **TXT**
link, not the XLSX listed above it on the CDE page, and not the "Public
Districts" file below it.

Skip `sb_ca2025_all_csv_v1.zip`. At 154 MB it exceeds GitHub's 100 MB file
limit and is too slow to fetch on page load. Visitors who want the
socioeconomic measures can download it themselves and drag it in — the drop
zone stays available even when data is published alongside the page.

### 2. Edit `data/manifest.json`

List only the files you actually shipped. `auto: true` loads on page open;
`auto: false` renders a button the visitor can click.

Keep the required two on `auto` and everything else on a button. That way the
page is usable in about nine megabytes and nobody waits for data they didn't
ask for.

### 3. Put it somewhere

**Netlify Drop** — https://app.netlify.com/drop, drag this folder onto the
page. Live URL in seconds, no account needed to try it.

**GitHub Pages** — create a repository, upload these files, then Settings →
Pages → Source: deploy from branch, root. Published at
`https://<user>.github.io/<repo>/` within a minute or two. Free and durable.

**Cloudflare Pages** — connect the repository, leave the build command empty,
set the output directory to `/`.

## If no manifest is present

The tool falls back to the drag-and-drop loader. That means `index.html` also
works on its own, opened straight from disk with no server at all.
