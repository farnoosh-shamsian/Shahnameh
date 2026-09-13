# Editions

The Persian text of the _Shahnameh_ in five editions. Scans are kept locally and
not tracked (see the root [`.gitignore`](../.gitignore)); the transcribed text is
here.

| Folder     | Text in the repo                                                    | Notes                                                                                                                                                                 |
| ---------- | ------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `ganjoor/` | 842 JSON files under `shahname/`, one per section                   | Exported from [Ganjoor](https://ganjoor.net). Provenance and re-sync instructions: [PROVENANCE.md](ganjoor/PROVENANCE.md), [upstream-API.md](ganjoor/upstream-API.md) |
| `moscow/`  | `Moscow searchable.txt` and the same text as `.doc`                 | Nine volume scans are local-only                                                                                                                                      |
| `tajiki/`  | Six volumes as `.docx`, `.txt` and one `.xml` (`sho-noma-ildi-1…6`) | The Cyrillic source behind [`shahnameh-transliteration/`](../shahnameh-transliteration/README.md)                                                                     |
| `macan/`   | **none — scan only**                                                | Turner Macan edition. The PDF is local-only, so this folder does not appear in a clone                                                                                |
| `vullers/` | **none — scan only**                                                | Vullers edition, five PDFs, all local-only                                                                                                                            |

Only `ganjoor/` has documented provenance. The others are working copies
gathered for further work. More to come.
