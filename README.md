# Dokumentace projektu MITŘ: chytrý dům ovládaný přes Bluetooth LE

Dokumentace semestrálního projektu v LaTeXu, šablona VŠB-TUO FEI (`diploma.cls`). Projekt má dvě
části: backend na Raspberry Pi (Python) a mobilní aplikaci pro Android (Kotlin). Každá část píše
do svých souborů.

## Překlad a postup

- Hlavní soubor je `main.tex`. Překládá se v Overleafu (pdfLaTeX + biber) a projekt je napojený na
  tento repozitář.
- Postup změny:
  1. Změny se zapíšou do místní kopie repozitáře.
  2. Změny se commitnou a pushnou.
  3. V Overleafu: **Menu → GitHub → Pull GitHub changes**, pak **Recompile**.
- Lokálně LaTeX nainstalovaný není, překlad se ověřuje až v Overleafu. Chyby a varování z logu
  Overleafu opravuje ta strana, jejíž soubor chybu způsobil.

## Kdo píše který soubor

| Soubor | Píše |
|---|---|
| `main.tex`, `diploma.cls`, `diplomalst.sty`, `.gitignore`, `README.md` | backend |
| `Chapters/abstrakt.tex`, `Chapters/abstract-en.tex` | backend (z podkladů obou stran) |
| `Chapters/uvod.tex`, `Chapters/navrh.tex` | backend |
| `Chapters/hardware.tex`, `Chapters/backend.tex`, `Chapters/rozhrani.tex` | backend |
| `Chapters/testovani.tex` (jen rámec kapitoly), `Chapters/testovani-backend.tex` | backend |
| `Chapters/prilohy.tex` | backend |
| `Chapters/zaver.tex` (shrnuje obě části) | aplikace |
| `zkratky.tex` (společné zkratky), `literatura.bib`, `Figures/` (kromě `Figures/aplikace/`) | backend |
| `Chapters/aplikace.tex` | aplikace |
| `Chapters/testovani-aplikace.tex` | aplikace |
| `Chapters/prilohy-aplikace.tex` | aplikace |
| `zkratky-aplikace.tex`, `literatura-aplikace.bib`, `Figures/aplikace/` | aplikace |

Do cizích souborů se nepíše. Když je potřeba změna jinde (nový balík v `main.tex`, oprava
v kapitole druhé strany), domluví se s druhou stranou. Komunikační rozhraní je popsané
v `Chapters/rozhrani.tex` podle `docs/ble-rozhrani.md` z backendu. Kapitola o aplikaci na něj
odkazuje (`\ref{chap:rozhrani}`) a neopakuje ho.

## Pravidla psaní

- **Jazyk a sloh.** Píše se česky, věcně a spisovně. Text popisuje skutečný stav kódu a hardwaru,
  žádné plány ani reklamu. Čísla (piny, časy, prahy, UUID) musí sedět s kódem.
- **Struktura.** Kapitola začíná `\chapter{...}`, uvnitř `\section`, `\subsection`. Výjimkou je
  `testovani-aplikace.tex`, které začíná `\section`, protože kapitolu otevírá `testovani.tex`.
  Přílohy jsou `\chapter{...}` (za `\appendix`).
- **Návěští.** Používají se `chap:`, `sec:`, `fig:`, `tab:` a `lst:`. Návěští aplikace mají za
  dvojtečkou `app-` (např. `fig:app-hlavni-obrazovka`), aby se nepotkala.
- **Nezlomitelné mezery.** Po jednopísmenných předložkách a spojkách se píše vlnovka: `v~`, `s~`,
  `k~`, `z~`, `o~`, `u~`, `a~`, `i~`. Mezi číslem a jednotkou také: `23~°C`, `10~s`, `512~B`.
- **Kód v textu.** Krátký kód v textu se píše makrem `\kod{...}`, např. `\kod{barva_svetla}`
  a `\kod{{"svetlo":"zapnout"}}`. Podtržítka a uvozovky se neescapují, `%` a `#` uvnitř
  `\kod` být nesmí.
- **Ukázky kódu.** `\begin{lstlisting}[language=Python]`, `language=json` nebo `language=kotlin`,
  s `caption=` a `label=lst:...`. Ukázky mají být krátké, jen to podstatné. Česká písmena
  s diakritikou v ukázkách převádí na akcenty nastavení `literate` v `main.tex`; jiné znaky mimo
  ASCII (pomlčky, uvozovky, šipky) do ukázek nepatří.
- **Tabulky.** Jako v šabloně: `\begin{table}[H]`, `\centering`, popisek **nad** tabulkou
  (`\caption`, `\label`), sloupce `|p{...}|` se svislými čarami a `\hline`.
- **Obrázky.** `\begin{figure}[H]`, popisek **pod** obrázkem. Soubory patří do `Figures/`
  (aplikace do `Figures/aplikace/`). Názvy souborů jsou bez mezer a diakritiky.
- **Uvozovky.** `\enquote{...}` nebo české „…“.
- **Literatura.** Citace `\cite{klic}`. Záznamy backendu jsou v `literatura.bib`, záznamy aplikace
  v `literatura-aplikace.bib` s klíči začínajícími `app-`.
- **Zkratky.** `\AddAcronym{zkratka}{význam}` v `zkratky.tex` (společné) nebo
  `zkratky-aplikace.tex`. Zkratka se při prvním použití v textu rozepíše.
- **Balíky.** Nové balíky se v kapitolách nenačítají. Dostupné jsou všechny ze šablony a navíc
  `tikz`, `float`, `caption`, `enumitem`, `array`, `csquotes` a `listings` s jazyky python, json
  a kotlin.
