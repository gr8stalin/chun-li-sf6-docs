---
name: add-new-matchup-page
description: Instructions for generating a new character matchup page.
disable-model-invocation: true
---

When this skill is invoked, the user will provide a character's name as a parameter. If no character name is provided, stop and ask the user to supply a character name before proceeding.

1. Check if a file for this character already exists at the sanitized filename path (e.g., `root/docs/matchups/ryu.md`) that would be generated for the provided character name. If a file at that exact path exists, stop and notify the user. If it does, stop and notify the user instead of overwriting it.
2. Find the markdown file in `root/docs/matchups` that has the highest numeric `nav_order` value defined in its frontmatter. Ignore any files that do not have a `nav_order` field. Ignore `index.md` in `root/docs/matchups`. Use that highest value plus 1 as the `nav_order` for the new file. If, contrary to expectation, no file with a `nav_order` field is found, stop and notify the user that nav_order cannot be determined.
3. If `root/docs/matchups/ken.md` cannot be found, stop and notify the user that the reference template is missing. Otherwise, copy the frontmatter structure from `root/docs/matchups/ken.md:1-6` exactly, replacing only the values for `title` (use the character name exactly as provided by the user) and `nav_order` (from step 2). Preserve all other frontmatter fields and keys unchanged.
4. Create the new markdown file at `root/docs/matchups/<sanitized name>.md` using the frontmatter from step 3. Leave the file body empty (no additional content below the closing `---`).

## Guidelines for handling character names

Some characters will have names with special characters, such as `E. Honda` and `A.K.I`. When creating a markdown file for that character, remove all punctuation, special characters, and spaces from the filename. For example, `E. Honda` would be `ehonda.md`, `A.K.I.` would be `aki.md`, `Ryu` would be `ryu.md`, and both `Chun Li` and `Chun-Li` would be `chunli.md`.

Regardless if a character's name contains special characters, preserve the character name as it was provided for the `title` field in their markdown file's frontmatter. That value is what end users will see in the documentation.