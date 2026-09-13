# Translations

Translations of the _Shahnameh_ in four languages, plus the scans and OCR they
derive from. This file records where each item came from and what, if
anything, has been changed here.

## Acknowledgement:

**Every XML text in this folder originates in Gregory Crane's Shahnameh
project: <https://github.com/gregorycrane/Shahnameh>**

That work is the foundation of this repository. The attribution is preserved inside the files themselves, in the
TEI header. The corrections to the Warner translation in this repository were made upon
the version Gregory Crane created.

---

## warner-english/

Arthur George Warner and Edmond Warner, _The Sháhnáma of Firdausí_, 9 vols.,
Kegan Paul, Trench, Trübner & Co., 1905–1925. Complete verse translation, in
the public domain.

| Path               | Origin                                                                                                                                                                                                |
| ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `scans/`           | Volume PDFs for vols. 1–4, plus a scanned review of the Rustam and Suhrab translation. Crane's TEI header cites Internet Archive items `shahnama01firduoft` … `shahnama09firduoft` as the OCR sources |
| `text/`            | Crane's TEI and working files, copied in unmodified (49 files, ~36 MB)                                                                                                                                |
| `text-diacritics/` | The same 9 volume XMLs, with diacritics restored here                                                                                                                                                 |

**From Crane:** the OCR of all nine volumes, the TEI conversion, and the markup
that makes the text usable — one `<lb/>` per verse line, `<pb n="vol.page"/>`
page breaks, section `<div>`s with `<head>`s, and the cross-edition alignment
milestones (**1,798** `unit="vullers"` and **810** `unit="calced"` across the
set). Also `<persName>`, `<placeName>` and `<rs>` tagging.

**Added here:** restoration of the transliteration diacritics, which the OCR
had dropped (`Iran` → `Írán`, `Faridun` → `Farídún`). Accents were sourced
from the PHI Persian edition of the same translation
(<https://persian.packhum.org>) by aligning the two editions on printed page
numbers, then on lines and tokens using Claude Opus 5. **26,744 substitutions** across **769
forms**. The patch adds accents and nothing else.

The canonical texts are the nine `shahnameh.warn01.xml` … `shahnameh.warn09.xml`
volumes. The rest of `text/` is Crane's own working material — indexes, TEI
fragments, per-volume plain text, and some intermediate and backup files
(`*-tmp.xml`, `*-fixed.xml`, `shahnameh.warner.xml`). Only the nine volume
files were patched.

Be aware that the volumes are not uniformly encoded, which matters when writing
tools against them: **vols. 1–5 are TEI-namespaced and vols. 6–9 are not**, and
**vol. 6 contains no `<lb/>` elements at all**, marking verse lines with bare
newlines inside `<p>` instead.

## mohl-french/

Jules Mohl, _Le livre des rois_, the French prose translation with facing
Persian text.

| Path     | Origin                                                        |
| -------- | ------------------------------------------------------------- |
| `scans/` | Gallica / BnF (ark `bpt6k5774334p`) and 8 further volume PDFs |
| `text/`  | Crane's repository — 14 XML, 16 TXT, 1 TSV                    |

**From Crane:** the OCR and cleaned-up volumes with proper-noun tagging. These
files share the conventions of the Warner set — `<pb n="vol.page"/>`,
`<div type="textpart">`, section heads — and carry `<xref>` links pointing to
the corresponding Warner sections, which is what makes Mohl and Warner
alignable.

**Added here:** nothing yet but kept so the repo has everything in one place for further work.

## rückert/

Friedrich Rückert's German verse translation.

| File                     | What it is                                             |
| ------------------------ | ------------------------------------------------------ |
| `Rückert_searchable.pdf` | Same scan with an OCR text layer (368 MB, not tracked) |
| `Rückert_OCR.txt`        | Raw OCR text as the engine produced it (774 KB)        |
| `Rückert_OCR_clean.txt`  | The same text with Fraktur artifacts normalised        |

OCR'd for this project from a 500-page scan held by Universitäts- und
Landesbibliothek Sachsen-Anhalt, set in Fraktur. Tesseract 5.4 with the
`script/Fraktur` model from `tessdata_best`; the German (`deu`) model reads
blackletter far worse, misreading even `Zal` as `Bal`.

The searchable PDF exceeds GitHub's 100 MB file limit and is covered by the
`*.pdf` rule in `.gitignore`, as the other scans are.

**Normalisation.** Tesseract emits Fraktur ligature glyphs literally, which is
mechanical to reverse: `<` is the _ch_ ligature and `>` the _ck_ ligature, and
the engine sometimes repeats the ligature's trailing letter, so both `ſi<h` and
`ſi<` mean _sich_. **21,000 substitutions** — long-s `ſ` → `s` (17,095),
`<` → `ch` (538), `>` → `ck` (820), plus stray rule-marks and margin speckles
(~3,800). Nothing was changed beyond these character rules.

**Status: partly corrected.** The character-level artifacts are resolved. Two
classes remain: the ~10% of high-confidence flags that are archaic forms rather
than errors (`dieß`, `eignes`), and real-word errors, which this method cannot
see by construction — where the scan misread `Blut` as `Baut`, both are valid
German. Those need proofreading against the page images.

## atkinson-abridgement/

James Atkinson's abridged translation (1832), taken from **Project Gutenberg
eBook #10315**, _The Persian Literature, Comprising The Shah Nameh, The
Rubaiyat, The Divan, and The Gulistan, Volume 1_.

`Atkinson.txt` is the Gutenberg plain text, `pg10315-images.html` the Gutenberg
HTML, `10315-cover.png` the cover image. Unmodified, Gutenberg licence terms
included in the files.

## zimmern-abridgement.txt

Prose abridgement from the Internet Classics Archive
(`classics.mit.edu/Ferdowsi/kings.html`), saved from a Google cache of the
plain-text version.

## Licensing

CC-BY-SA

Work partly assisted by Claude Opus 5.
