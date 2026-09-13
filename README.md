# Prog3

Adresář `images/` obsahuje podadresáře studentů podle příjmení bez diakritiky, stejně jako v repozitáři `Prog2`.
V každém podadresáři je připravený soubor `README.md` pro vložení odkazu na osobní repozitář studenta.

## GitHub Pages – losovátko

1. Otevřete v GitHubu tento repozitář a přejděte do **Settings** → **Pages**.
2. V části **Build and deployment** nastavte:
   - **Source:** `Deploy from a branch`
   - **Branch:** `main`
   - **Folder:** `/ (root)`
3. Klikněte na **Save**.
4. Losovátko pak najdete na adrese ve tvaru:
   - `https://OWNER.github.io/REPO/losovatko.html`
5. Pro aktuální repozitář `motol2/Prog3` tedy vychází adresa:
   - `https://motol2.github.io/Prog3/losovatko.html`
6. Pokud se někdy změní owner nebo název repozitáře, GitHub po publikaci ukáže přesnou aktuální URL přímo v nastavení **Pages**.

Poznámka: po prvním zapnutí GitHub Pages může publikace trvat pár minut.

## Markdown Cheatsheet

Nejpoužívanější formátovací značky:

- `**tučně**` → **tučně**
- `*kurzíva*` → *kurzíva*
- `~~přeškrtnuté~~` → ~~přeškrtnuté~~
- `# Nadpis 1` až `### Nadpis 3` → nadpisy
- `- položka seznamu` → odrážkový seznam
- `1. položka` → číslovaný seznam
- `` `kód` `` → inline kód
- blok kódu:

```html
<p>Ahoj</p>
```

- `[text odkazu](https://example.com)` → odkaz
- `> citace` → citace

Tip: pro novou řádku uvnitř odstavce použijte dvě mezery na konci řádku nebo prázdný řádek pro nový odstavec.
