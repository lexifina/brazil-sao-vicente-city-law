# São Vicente (city): law history in git

Part of [lexifina/global-law](https://github.com/lexifina/global-law), one git history for every country's law: this is the law of Sao Vicente, São Paulo, Brazil, which global-law reads at `brazil/sao-paulo/sao-vicente/acts/`.

The municipal law of São Vicente, São Paulo (Brazil), as a git history. The Lei Orgânica and 203 municipal laws use article files; another 53 laws use complete-text files. Paragraphs remain separate lines for `git blame`, `git log` and `git diff`. The text is Portuguese.

It follows the shared design of [lexifina/global-law](https://github.com/lexifina/global-law).

## What this repository holds

| Folder | Act | Versions |
| --- | --- | ---: |
| `lei-organica/` | Lei Orgânica do Município de São Vicente (1990), with SAPL history | 3 |
| `lei-*/`, `lc-*/` | Municipal laws, as enacted: 203 split into article files and 53 in complete-text files | one each (256 laws) |

**The Lei Orgânica with its history.** SAPL supplies a structured text for each recorded period of vigência. Each change is credited to the amendment SAPL names.

**Municipal laws as enacted.** The record contains 256 ordinary and complementary laws, each credited to itself. Later amendments are not incorporated into the original wording. The original 203 laws use article files; the additional 53 use `texto-integral.md`, preserving the complete PDF text layer, including signatures, textual annexes, tables, printed headings and page numbers. Decorative crests and accessibility badges are excluded from law text. Scans and acts with unresolved source, normative-image or commencement issues remain outside the record.

State law is in [brazil-sao-paulo-law](https://github.com/lexifina/brazil-sao-paulo-law); federal law is in [brazil-law](https://github.com/lexifina/brazil-law).

## Source

[Câmara Municipal de São Vicente, SAPL](https://sapl.saovicente.sp.leg.br/norma/2325). Each version names its official source URL and source-byte SHA-256 in `data/versions.json`.

## Dates

The first version of the Lei Orgânica is the text SAPL gives in force from 1990-04-05. Each later version is dated by the first day of the period of vigência SAPL gives it and credited to the act SAPL names for it ("Dada por ..."); a period SAPL starts without naming an act is committed as a publisher commit, not guessed. The original 203 municipal laws use SAPL publication dates, or the act dates when publication metadata is absent, under their publication/signature commencement clauses. The additional 53 laws follow their own vigência clauses: publication, the printed act/promulgation date, an express commencement date, or the specified interval after publication. They include five laws commencing on an express date after publication and LC 1,177, commencing 180 days after publication. Dates when particular provisions produce delayed or retroactive effects remain in the source text and do not replace the act's express commencement date. No retrieval-day commencement is used for these additions. Commits are at noon in São Vicente.

## How it is built

Lexifina reads the sources listed here and records each act's dated versions, and the laws that made each change, in one corpus file. `tools/build.py` writes this repository from that file, and the same corpus always gives the same commit hashes; `REPRODUCE.md` gives the details and the checks. A model (Claude) wrote Lexifina's code; it wrote no legal text, and no model runs when the history is built.

The Lei Orgânica uses one file per article, with provision labels and headings retained; SAPL amendment annotations and superseded blocks are excluded. The original 203 municipal laws use one file per article, containing text from the PDF heading through its closing date line. Their signatures, repeated page furniture and page numbers are excluded. The additional 53 laws instead use one complete `texto-integral.md` per act. Their signatures, textual annexes, tables and printed page text are retained; they are not cut at the closing date line. Text stays in the source's order, with only schema typesetting and paragraph normalization.

## How it is checked

Each version read from git on its entry-into-force date must match the corpus. Independent source comparisons cover the structured SAPL text and the municipal PDFs. For the 53 complete-text additions, every page's word and punctuation stream is compared with an independent PDF extraction, including text after signatures. Results are recorded in `REPRODUCE.md`.

## What "author" means

Each commit credits the law that supplied its wording, or the publisher for unexplained consolidated text. Author addresses are non-existent placeholders; the committer is Lexifina.

## Limits

This is a partial as-enacted record: 256 municipal laws and the Lei Orgânica with its recorded SAPL history. SAPL lists 7,004 ordinary and 1,252 complementary laws, so the record does not claim catalogue completion or a current consolidated text for every law. The text is not the authoritative official version: only the Diário Oficial do Município is authoritative.

## Licence

See [LICENSE](LICENSE): Brazilian law texts are not protected by copyright (Lei 9.610/1998, art. 8, IV). Fonte: Câmara Municipal de São Vicente, SAPL. SAPL states “Conteúdo e dados sob licença Creative Commons 4.0 Atribuir Fonte - Compartilhar Igual”.
