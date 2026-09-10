# Tajik Cyrillic → Latin: the transliteration scheme

The scheme used throughout this repository. The **this project** column is the
convention actually applied to the files; the remaining columns are the
established schemes it was set against while the convention was being decided.

| Cyrillic | IPA | this project | ISO 9 (1995) | KNAB (1981) | WWS (1996) | ALA-LC | Allworth | BGN/PCGN |
|---|---|---|---|---|---|---|---|---|
| А а | /æ/ | **a** | a | a | a | a | a | a |
| Б б | /b/ | **b** | b | b | b | b | b | b |
| В в | /v/ | **v** | v | v | v | v | v | v |
| Г г | /ɡ/ | **g** | g | g | g | g | g | g |
| Ғ ғ | /ʁ/ | **ġ** | ġ | gh | gh | ḡ | gh | gh |
| Д д | /d/ | **d** | d | d | d | d | d | d |
| Е е | /jeː, eː/ | **e** | e | e, ye | e | e | ye‐, ‐e‐ | e |
| Ё ё | /jɔː/ | **ýā** | ë | yo | ë | ë | yo | yo |
| Ж ж | /ʒ/ | **ž** | ž | zh | zh | ž | zh | zh |
| З з | /z/ | **z** | z | z | z | z | z | z |
| И и | /i/ | **i** | i | i | i | i | i | i |
| Ӣ ӣ | /ɘ/ | **ī** | ī | ī | ī | ī | ī | í |
| Й й | /j/ | **y** | j | y | ĭ | j | y | y |
| К к | /k/ | **k** | k | k | k | k | k | k |
| Қ қ | /q/ | **q** | ķ | q | q | ķ | q | q |
| Л л | /l/ | **l** | l | l | l | l | l | l |
| М м | /m/ | **m** | m | m | m | m | m | m |
| Н н | /n/ | **n** | n | n | n | n | n | n |
| О о | /ɔː/ | **ā** | o | o | o | o | o | o |
| П п | /p/ | **p** | p | p | p | p | p | p |
| Р р | /r/ | **r** | r | r | r | r | r | r |
| С с | /s/ | **s** | s | s | s | s | s | s |
| Т т | /t/ | **t** | t | t | t | t | t | t |
| У у | /u/ | **u** | u | u | u | u | u | u |
| Ӯ ӯ | /ɵː/ | **ū** | ū | ū | ū | ū | ū | ŭ |
| Ф ф | /f/ | **f** | f | f | f | f | f | f |
| Х х | /χ/ | **x** | h | kh | kh | x | kh | kh |
| Ҳ ҳ | /h/ | **ḥ** *or* **h** | ḩ | h | ḩ | x | h | h |
| Ч ч | /tʃ/ | **č** | č | ch | ch | č | ch | ch |
| Ҷ ҷ | /dʒ/ | **ĵ** *or* **j** | ç | j | j | č̦ | j | j |
| Ш ш | /ʃ/ | **š** | š | sh | sh | š | sh | sh |
| Ъ ъ | /ʔ/ | **'** | ' | ' | ' | ' | " | ' |
| Э э | /eː/ | **ė** | è | è, e | ė | è | e | ė |
| Ю ю | /ju/ | **ýu** | û | yu | i͡u | ju | yu | yu |
| Я я | /jæ/ | **ýa** | â | ya | i͡a | ja | ya | ya |

## Notes on the scheme

**о → ā but а → a.** Tajik о is /ɔː/, corresponding to Persian long ā; Tajik а
is /æ/, the short vowel. So `осори` becomes `āsāri`, not `osori`. This is the
single most important thing to understand about these files: a reader expecting
a Russian-style romanisation will misread every long ā in the text.

**х → x and ҳ → ḥ.** Both are given as `kh`/`h` in most published schemes. This
project keeps them distinct and unambiguous: `x` for /χ/, `ḥ` for /h/. The cost
is that `x` looks unfamiliar; the benefit is that the mapping is reversible.

**ҳ and ҷ have two forms in the files.** The draft table gave plain `h` and `j`.
`complete/shahnameh-complete.txt` uses `ḥ` and `ĵ`, which is the settled
convention; every other file in the repository still uses `h` and `j`. They have
not been merged. See the README for which file is which and how to convert.

**ъ → `'`.** The apostrophe is U+0027 APOSTROPHE, not U+2019. This matters when
matching: `ĵāme'e`, `ma'lum`. The only U+2019 in the repository is inside a
Western-language book title in the bibliography (`Firdosil’s`, in
`complete/introduction.txt` line 128 and `complete/shahnameh-complete.txt` line
296), where it is correct typography and has been left alone.

## Reversibility

The scheme is reversible. Because /ʃ/ /tʃ/ /ʒ/ /χ/ are written `š` `č` `ž` `x`
rather than `sh` `ch` `zh` `kh`, the letter `h` is never part of a digraph — in
the plain-convention files every `h` is ҳ. Sequences that look like digraphs are
a consonant followed by the plural suffix ҳо: `baythāi` = байтҳои, `rūzhā` =
рӯзҳо, `ranghā` = рангҳо.

So converting a plain-convention file to `ḥ`/`ĵ` is a straight substitution with
no exceptions to guard:

```bash
perl -CSD -Mutf8 -pe 'tr/hj/ḥĵ/' volumes/shahnameh-vol-1.txt
```

The one thing that is *not* recoverable is capitalisation, which the source
applied inconsistently to words beginning with а, қ and ғ. See the README.
