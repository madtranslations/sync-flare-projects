# sync-flare-projects
GitHub Action to keep target language Flare projects up-to-date with the source Flare project.

## Sample configuration
```yaml
name: Sync Flare projects

on:
  workflow_dispatch:

jobs:
  sync_folders:
    uses: madtranslations/sync-flare-projects/.github/workflows/sync-flare-projects.yml@main
    with:
      source_flare_project: "<Source Flare project folder>"
      exclude_during_update: "*.css,*.flaix,*.flglo,*.flixl,*.fllng,*.flmco,*.flmsp,*.flpgl,*.flprj,*.flskn,*.flsnp,*.fltar,*.fltoc,*.flvar,*.htm,*.html,*.mcsyns,*.props"
      exclude_during_delete: ""
```
