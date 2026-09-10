# Shahnameh

Two things: a Latin-script transliteration of Ferdowsi's *Shahnameh* made from the
Tajik Cyrillic edition, and a parallel-text reader for one passage of the poem.

## `shahnameh-transliteration/`

The Tajik Cyrillic text, OCR'd and then transliterated by hand into Latin script
following [the scheme](shahnameh-transliteration/transliteration-guide.md).

Six volumes, 71,017 words, plus the editors' introduction. It is not the whole
poem but roughly the first half, ending around the story of Goštasp and Katayun
in the reign of Kay Lohrasp — about the first four volumes of Khaleghi-Motlagh's
edition and a few sections of the fifth. `%%` marks the volume boundaries
(`%%Shahnameh part 1%%` … `%%Shahnameh part 6%%`); there are no other added
headings.

See [its README](shahnameh-transliteration/README.md) for the file layout, the
two spelling conventions that were deliberately not merged, and the known issues.

## `multitext/`

A parallel-text reader for one passage — Pizzi's reading 1, Hushang, 68 couplets
— setting six printed Persian editions, the transliteration above and four
nineteenth- and early-twentieth-century translations side by side, one couplet
per row, with each edition switchable on and off. Three of the four translations
are prose and are placed by section; Rückert's German verse is aligned couplet by
couplet. Two layouts of the same collation:
[`shahnameh-reader-sample.html`](multitext/shahnameh-reader-sample.html),
where the translations are columns beside the Persian, and
[`shahnameh-reader-sample2.html`](multitext/shahnameh-reader-sample2.html), where
they run as bands between the couplet rows. Open either in a browser.

Four of the six editions were read off the scans by model OCR and are **not yet
verified**. See [the README beside them](multitext/README.md) for what the
columns are, how the alignment was made and how far the text can be trusted.

---

*This work was prepared with the assistance of Claude Opus 5, run at high reasoning effort.*
