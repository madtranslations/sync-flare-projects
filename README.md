# Sync Flare projects GitHub action
A GitHub action to keep target language Flare projects up-to-date with the source Flare project. It works by copying all files from the source Flare project that are not handled by the translation process into the translated Flare projects, and then removing any stale files (files that have been deleted in the source project) from the translated projects.

## Variables
- The `source_flare_project` variable specifies the name of the root-level folder containing your **source** Flare project (i.e. the folder containing the `.flprj` file).
- The `exclude_during_update` variable specifies the files or file types that will not be copied from the source Flare project to the translated projects – this list must match the files that are handled by the translation process.
- The `exclude_during_delete` variable specifies files that should not be deleted from the translated projects, even if the file does not exist in the source Flare project. This is intended for files that only exist in the translated project (e.g. a custom import file).

# Adding this action to your repo
To add this action to your Flare translation repo:
1. Create a new YAML file in your repo at this location: `.github/workflows/sync-flare-projects.yml`
2. Copy the sample configuration below and paste it as the contents of the file
3. Replace `<Source Flare project folder>` with the name of your source Flare project folder
4. Make sure the list of files specified in the `exclude_during_update` and `exclude_during_delete` variables are correct
5. Commit the changes (this file must exist on the `main` branch as well as on any branch you wnat to run the action on)

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

# Running this action
This action must be run **after** the files handled by the translation process have been exported to the translated Flare projects. Then you can run the action by going to `Actions`, selecting the name of this action and then clicking `Run workflow` (top right). Be sure to run the action from the branch the translated files have been exported to.
