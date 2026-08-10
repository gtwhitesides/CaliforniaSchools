The CAASPP data files go in THIS folder, alongside manifest.json.

They are not included in the download — they come from the California
Department of Education, not from the tool. Without them the published
page falls back to asking every visitor to upload their own copies.

Get them from:
  https://caaspp-elpac.ets.org/caaspp/ResearchFileListSB

Required (both are already listed in manifest.json with auto: true):
  sb_ca2025_1_csv_v1.zip       8 MB   English and math
  sb_ca2025entities_csv.zip    1 MB   School and district names

Optional (listed with auto: false, so they appear as buttons):
  cast_ca2025_1_csv_v1.zip     2 MB   Science
  sb_ca2024_1_csv_v1.zip       8 MB   Year-over-year change

Leave the zips zipped. Do not rename them - the names in manifest.json
must match exactly. Then redeploy the whole folder.

To check a live deploy, open these URLs directly in a browser:
  <your-site>/data/manifest.json          should show JSON
  <your-site>/data/sb_ca2025_1_csv_v1.zip should download a file
A 404 on the second one is the problem.
