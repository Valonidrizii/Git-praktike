# Shop.me — ushtrim HTML / CSS

Ky projekt e rikrijon pjesën kryesore të fotos së dhënë: logoja dhe menuja sipër, titulli dhe butoni majtas, personi me sfond lejla djathtas. Poshtë saj janë shtuar katër kategori për të ushtruar Grid dhe për të pasur destinacione për lidhjet e menusë.

## Si e hap në Mac

1. Nxirre folderin `shopme-html-css` nga ZIP-i.
2. Në Visual Studio Code zgjidh **File → Open Folder…** dhe hape këtë folder.
3. Hape `index.html` në browser me dy klikime. Nëse je në Terminal brenda këtij folderi, shkruaj `open index.html`.
4. Pas një ndryshimi në kod, ruaje me **Cmd + S** dhe rifresko browser-in me **Cmd + R**.

Projekti përdor vetëm HTML, CSS dhe një fotografi lokale. Nuk ka nevojë për instalim, npm apo internet që të hapet.

## Skedarët

| Skedari | Puna që bën |
| --- | --- |
| `index.html` | Struktura dhe përmbajtja: logo, menu, tituj, paragrafë, lidhje dhe kategori. |
| `style.css` | Ngjyrat, përmasat, pozicionimi dhe përshtatja për telefon. |
| `assets/model.png` | Fotografia me sfond transparent. |
| `ASSET-NOTES.md` | Origjina dhe mënyra e përgatitjes së fotografisë. |

HTML e lidh CSS-në me këtë rresht brenda `<head>`:

```html
<link rel="stylesheet" href="style.css" />
```

## Çfarë po mëson

| Pjesa | Vetia | Pse përdoret këtu |
| --- | --- | --- |
| `.header-layout` | `display: flex` | Vendos logon dhe menunë në një rresht. |
| `.navigation` | `display: flex` dhe `gap` | Rreshton lidhjet dhe vendos hapësirë mes tyre. |
| `.hero-layout` | `display: grid` | Ndan pjesën kryesore në dy kolona. |
| `.collection-grid` | `repeat(4, minmax(0, 1fr))` | Krijon katër kolona të barabarta. |
| `:root` | `--color-primary` | Deklaron një variabël që mund të përdoret disa herë. |
| Titulli dhe butoni | `var(--color-primary)` | Marrin të njëjtën ngjyrë nga variabla. |
| `.hero-art` | `position: relative` | Krijon pikën e referimit për figurat brenda saj. |
| `.hero-model` | `position: absolute` | Vendos fotografinë mbi rrethin. |
| `.hero-circle` | `border-radius: 50%` | E kthen një katror në rreth. |
| Karta dhe butoni | `padding` | Krijon hapësirë brenda elementit. |
| `.button` | `margin-top` | Krijon hapësirë jashtë elementit, sipër tij. |
| `@media` | `grid-template-columns: 1fr` | Në telefon, teksti dhe fotografia kalojnë njëri poshtë tjetrit. |

**Flex** është i përshtatshëm kur rreshton elemente kryesisht përgjatë një drejtimi. **Grid** është i përshtatshëm për një plan me kolona dhe rreshta. Në këtë faqe përdoren të dyja.

### Lexoje pjesën kryesore të Grid

```css
.hero-layout {
  display: grid;
  grid-template-columns: minmax(0, 1.65fr) minmax(0, 1fr);
  gap: 2rem;
  align-items: center;
}
```

- `display: grid` aktivizon Grid te prindi.
- Kolona e parë merr 1.65 pjesë të hapësirës së disponueshme, kurse e dyta 1 pjesë.
- `minmax(0, ...)` lejon që kolonat të ngushtohen pa u bllokuar nga gjerësia minimale e përmbajtjes.
- `gap` lë hapësirë mes kolonave.
- `align-items: center` i vendos elementet në mes në drejtimin vertikal.

### Provo një variabël

```css
:root {
  --color-primary: #4655b5;
}

.button {
  background: var(--color-primary);
}
```

Variabla është një vlerë e emërtuar. Kur e ndryshon `--color-primary`, ndryshojnë të gjitha pjesët që e përdorin me `var()`.

## Pesë ushtrime për ty

1. Ndrysho titullin në **Hello, I am Valon!**. Gjeje vetë tag-un `<h1>`.
2. Ndrysho `--color-primary` në `#215c49`. Shiko cilat pjesë ndryshojnë.
3. Ndrysho `gap` te `.navigation` dhe shiko distancën mes lidhjeve.
4. Ndrysho Grid-in e kartave nga `repeat(4, ...)` në `repeat(2, ...)`. Provoje në një dritare të gjerë.
5. Zvogëlo browser-in. Gjeje rregullin `@media (max-width: 760px)` dhe shpjego pse teksti kalon sipër fotografisë.

Bëje një ndryshim në herë, ruaje dhe shiko rezultatin. Kështu lidh vetinë e CSS-së me ndryshimin që sheh në faqe.

## Kur do ta ruash në Git

Nëse folderi është pjesë e repository-t tënd, fillo me `git status`. Puno në një branch të veçantë dhe kontrollo `git diff` para commit-it. Mos i zëvendëso skedarët e projektit të mëparshëm pa i ruajtur ndryshimet e tij.

## Shënim për përputhjen me foton

Struktura, ngjyrat dhe vendosja e pjesës kryesore janë bazuar në referencë. Fotografia është përshtatur nga referenca me sfond transparent; nuk është kopje identike piksel për piksel. Përshtatja për telefon dhe kategoritë poshtë janë shtesa të këtij ushtrimi.
