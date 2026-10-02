# COSMOS Screen Builder

A visual editor for [OpenC3 COSMOS](https://openc3.com) telemetry screens. Drag widgets onto a live preview, edit their parameters in a form, and copy the generated screen definition text into COSMOS.

COSMOS screens are normally written by hand in a text format (`SCREEN`, `VERTICALBOX`, `LABELVALUE INST HEALTH_STATUS TEMP1`, `END`, …). This tool writes that text for you, and can also load existing screens so you can edit them visually.

## Running it

It's a single self-contained HTML file with no dependencies and no build step. It loads nothing from the internet, so it works offline and on isolated networks.

- **Locally:** open `index.html` in a current version of Chrome, Edge, Firefox, or Safari.
- **Hosted:** put `index.html` on any static web server, or enable GitHub Pages for this repo (Settings → Pages → deploy from the `main` branch, root folder).

## Features

- Drag-and-drop from a palette of about 50 COSMOS widgets: layout, decoration, telemetry, limits bars, LEDs, graphs, buttons and inputs, tabs, and canvas drawing items
- Drag existing widgets to move them, including between containers
- Inspector form for every widget parameter, plus `SETTING`, `SUBSETTING`, `TOOLTIP`, and `NAMED_WIDGET`
- Free positioning inside a `CANVAS`: drag items anywhere (hold Shift to snap to 10px)
- Preview styled like COSMOS, with placeholder values
- Load existing screens by pasting the text and pressing **Apply**, or with **Open…**. Handles line continuations (`&`, `+`, `\`), ERB tags (`<%= target_name %>`), and comments.
- **Copy screen text** to paste into the COSMOS screen editor, or **Download .txt** for a plugin's `targets/<TARGET>/screens/` folder
- Undo/redo, keyboard shortcuts, and autosave in the browser

## Using the output

1. Build the screen, then click **Copy screen text**.
2. In COSMOS, open Telemetry Viewer, create or edit a screen, paste the text, and save. Or save it as `targets/<TARGET>/screens/<name>.txt` in your plugin.

## Notes and limitations

- The preview approximates the COSMOS look. Check the final result in COSMOS.
- Target, packet, and item names aren't validated against your COSMOS system.
- Comments at the end of a line are dropped when a screen is loaded. Comments on their own line are kept.
- Custom widgets from other plugins are kept unchanged, but they show as placeholder boxes.
- Your work is saved in your browser's local storage. Other people who open the file get their own copy.

Built against the syntax used by COSMOS 7.4.1. Tested by round-tripping all of the demo plugin's screens.

## License

MIT. See [LICENSE](LICENSE). This project isn't affiliated with OpenC3.
