# Settings

## Theme Selection

GitNotebooks supports dark mode. To change the theme:

1. Sign in
2. Select your user avatar on the top right
3. Choose a theme

<img src="./images/settings/theme-selection.png" alt="Theme selection in GitNotebooks" width="400px" />

<img src="./images/settings/dark-theme.png" alt="GitNotebooks in dark theme" width="700px">

## Notebook Settings

To access notebook diff settings open the gear icon to the right of the pull request title.

![Settings](./images/settings/settings.png)

These settings will apply to all notebook diffs.

### Hide Outputs

Enabling `Hide Outputs` will collapse all cell outputs.

### Collapse Notebooks

Enabling `Colapse Notebooks` will collapse the notebooks by default. This can be helpful if you have a lot of changed notebooks to review and you'd rather see them one at a time.

### Raw Markdown

Enabling `Raw Markdown` will show the markdown cells in their unrendered format.

Note that markdown comments will work for both rendered and unrendered markdown comments. If a comment is made to markdown
in a rendered format they will appear in the unrendered view and vice versa.

### Show Entire Notebooks

Enabling `Show Entire Notebook` will render the entire notebook, not just the changed cells. By default GitNotebooks will show
only the cells that have changed with a single cell above and below for context. The change this setting more precisely, see `Cells to show around changes`

### Cells to show around changes

You can control how many unchanged cells appear above and below a changed cells. If you only want to see changed cells without their surrounding context,
set `Cells to show around changes` to `0`.
