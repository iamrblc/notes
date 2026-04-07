# Elméleti háttér

## **ELMÉLETI RÉSZ — VÁZLAT**

### **Felütés**

- Példák (rossz, félrevezető, vicces)
    
- Beszélgetés: _Mit próbál átadni? Sikerül? Miért / miért nem?_
    

---

### **0. Adatkommunikáció területei (keretezés)**

- Data Discovery / EDA → magunknak
    
- Data Visualization → másoknak (egy ábra → egy üzenet)
    
- Data Storytelling → narratíva + kontextus + következtetés
    
- Dashboards → folyamatos monitorozás, döntéstámogatás
    
- (Infografika → vizuális ismeretterjesztés, nem célunk)
    

> _Mi ma az „egy ábra jól” témában vagyunk._

---

### **1. Miért vizualizálunk?**

- mintázatok felismerése
    
- eltérések és trendek gyors észlelése
    
- memorizálhatóság és érthetőség → agy vizuális
    
- döntéstámogatás → könnyebb érvelés
    
- _Viz → nem dekoráció, hanem gondolkodási eszköz._
    

---

### **2. Különböző vizualizációs kontextusok**

- EDA → gyors, piszkos, sok ábra, magadnak
    
- „Ábra” / grafikon → egy üzenet, konkrét közlés
    
- Dashboard → standardizált, frissül, nincs magyarázó ember mellette
    
- Prezentáció → vezetett figyelem, narratíva
    
- Infografika → történet, branding, szépség is szerepet kap
    

> _Itt mi a „Tiszta ábra üzleti környezetben” témát bontjuk ki._

---

### **3. Vizuális nyelv / vizuális gondolkodás**

- Vizuális hierarchia (mi látszik először / másodszor)
    
    - méret, vastagság, kontraszt, szín, pozíció
        
- Gestalt elvek
    
    - közelség
        
    - hasonlóság
        
    - csoportosítás
        
    - mintázatkeresés
        
- „Rendet csinálunk a képen”
    
    - grid / alignment
        
    - whitespace
        
    - egy fókuszpont
        

---

### **4. Adat → Ábra logika (chart selection)**

**Első kérdés:** _Mit akarok megmutatni?_

|Cél|Példa adathelyzet|Ajánlott ábra|
|---|---|---|
|Összehasonlítás|kategóriák között|bar chart (hosszabb nevek → horizontális)|
|Idősor / trend|idő → érték|line chart (+ rolling átlag opcionális)|
|Eloszlás|egy változó terjedése|histogram / box / violin|
|Kapcsolat|X és Y viszonya|scatter (+ trendline ha kell)|
|Részek egésze|ritkán jó|ha nagyon muszáj: stacked bar, NE pie|

- _Legfontosabb 3: bar, line, scatter._
    

---

### **5. Változótípusok**

- Kategóriás vs. folytonos (más vizuális csatornák)
    
- Nominális / ordinális → szín vagy sorrend kérdése
    
- Több változó:
    
    - szín mint kategóriás kódolás
        
    - méret vagy forma mint kiegészítő marker
        
    - ha túl sok → inkább **faceting** (sok kicsi ábra), nem egy ábra
        

---

### **6. Szín és skálák**

- Kevés szín → kevesebb kognitív terhelés
    
- Egy highlight szín → fókusz
    
- Paletták:
    
    - **folytonos** → sequential vagy diverging (ha van középérték ≠0 → diverging)
        
    - **kategóriás** → jól elválasztható, színtévesztő-biztos
        
- Színtévesztés + kontraszt → _ne piros-zöld, ha nem muszáj_
    

---

### **7. Adattisztaság & értelmezési alapok (2–3 mondatos blokkok)**

- **Nulláról induló tengely** bar chartnál → különben arányokat torzít
    
- **Normalizálás** → arányok vs. darabszám (pl. különböző populációk)
    
- **Aggregálás** → lehet félrevezető (Simpson-paradoxon említése)
    
- **Idősoroknál** → zaj csökkentése rolling mean-nel
    

---

### **8. Rossz gyakorlatok (interaktív példaelemzés)**

- 3D effekt (nincs értelme)
    
- Pie chart kategória-pornó
    
- 12 szín egy térképen → olvashatatlan
    
- Ornamentika dekoráció helyett
    
- Túl sok szöveg / nincs fókusz
    
- Legendák elrejtik a lényeget → direkt címkézés jobb
    

---

### **9. Eszközök áttekintése**

- Excel / Sheets — gyors, de limitált finomhangolás
    
- PowerBI / Tableau — dashboard/üzleti környezet
    
- D3.js — custom webes viz, de fejlesztőmennyiség
    
- Python:
    
    - matplotlib → alacsonyszintű
        
    - seaborn → stat-friendly defaultok
        
    - plotnine (ggplot-szerű)
        
    - **Plotly** → interaktív, prezentációbarát → ezt használjuk
	
# Közös gyakorlat (code along)

## 0) Setup (2–3 perc)

- Colab: `!pip install plotly` (ha kell), import: `plotly.express as px`, `plotly.graph_objects as go`, `plotly.subplots as sp`
    
- Dataset: **Gapminder** (px-ben benne), később opcionálisan **egy tiszta HU/EU CSV** (sport/birds/PECBMS)
    
- Template: `px.defaults.template = "plotly_white"` → „tiszta ábra” alap
    

**Elméleti híd:** „alap tisztaság” = vizuális hierarchia, kevés tinta.

---

## 1) „Hello px” — egy _nagyon_ egyszerű chart (5–8 perc)

- **Cél:** syntax megismerése (data, x, y, color → mapping)
    
- Feladat: `px.bar` v. `px.scatter` 1 országra/évre (Gapminder)
    
- Mutasd: `fig.show()`, `hover_data`, `labels` paraméter
    

**Elméleti híd:** adat→ábra; encoding („x/y/color mint csatornák”).

---

## 2) Bar chart — összehasonlítás, rendezés, horizontális (10–12 perc)

- `px.bar` több ország egy évben; **rendezés** érték szerint
    
- **Horizontális** sáv (hosszú nevek → olvashatóbb)
    
- **Zero baseline** ellenőrzés; **highlight 1 kategória** (color+manual)
    
- Opcionális: **százalékos normalizálás** (arány vs. darab)
    

**Elméleti híd:** „mikor bar”; nulláról induló tengely; normalizálás.

---

## 3) Bar chart — csoportosított vs. stacked + 100% stacked (10 perc)

- `barmode="group"` vs `barmode="stack"` vs **100%** (előtte arányosítás)
    
- **Legend minimalizálás** → direkt címkézés (px: `text_auto=True`)
    
- **Egy highlight szín**, többi neutrális
    

**Elméleti híd:** részek-egésze ritkán; legend vs. direct labels; kognitív terhelés.

---

## 4) Line chart — idősor + görgetett átlag (10–12 perc)

- `px.line` 1–2 ország, több év
    
- **Rolling mean** (pandas) opcionálisan második trace-ként
    
- **Annotáció**: 1 kiemelt csúcs vagy fordulópont (`add_annotation` vagy `fig.add_vline`)
    

**Elméleti híd:** trend vs. zaj; cím = következtetés, nem változónév.

---

## 5) Scatter — kapcsolat + skálák + trendline (12–15 perc)

- `px.scatter` (pl. GDPpc vs lifeExp egy évben)
    
- **Log skála** az x-en (`log_x=True`) + **trendline="ols"**
    
- **Outlier** jelölés annotációval
    
- **Hover**: `hover_name`, `hover_data` → csak hasznos mezők
    

**Elméleti híd:** kapcsolat; skála megválasztása; információsűrítés hoverben.

---

## 6) Scatter multivariáns — szín + méret + facet (12–15 perc)

- `size=` (pl. population), `color=` (continent)
    
- **Figyelmeztetés**: túl sok encoding → túlterhel
    
- **Faceting**: `facet_col="continent"` vagy `facet_row=...`
    
- **Egységes tengelyek** faceteknél (összehasonlíthatóság)
    

**Elméleti híd:** többváltozós ábrázolás; faceting > túlzsúfolt egyábra.

---

## 7) Több ábra egy figure-ön — subplots (10–12 perc)

- `sp.make_subplots(rows=1, cols=2, shared_yaxes=True)`
    
- Bal: bar; jobb: line (ugyanarról a jelenségről két nézet)
    
- **Közös cím** + alcímek; **legend pozíció** kézi beállítás
    

**Elméleti híd:** layout, alignment, „rend a képen”.

---

## 8) Layout polishing — „egy üzenetes” finomhangolás (8–10 perc)

- **Cím = üzenet**, alcím = kontextus
    
- Tengelyfeliratok, **tickformat** (pl. ezres elválasztó, %)
    
- **Legend pozíció**, **margin**, **height/width**
    
- **Színpaletta**: kategóriás vs. folytonos (diverging, ha van közép)
    

**Elméleti híd:** hierarchia, színek, olvashatóság.

---

## 9) px → go átjáró — „ha kell a csavar” (10–12 perc)

- px-szel létrehozott `fig` **trace-einek módosítása** (`fig.data[i].marker`, `line`)
    
- **Hovertemplate** finomhangolás (üzleti „valutás” megjelenítés)
    
- **Shapes**: referencia-vonal (`add_hline/vline`), célérték sáv
    
- **Annotations**: callout a lényegre (nyíl + rövid szöveg)
    

**Elméleti híd:** „interaktivitás ≠ jobb” — csak ami támogatja az üzenetet.

---

## 10) Export (2–3 perc)

- PNG: `fig.write_image(...)` (kell `kaleido`)
    
- HTML: `fig.write_html(...)` (megosztható, interaktív)
    
- **Megfelelő arányok** prezentációhoz (16:9, 4:3)
    

**Elméleti híd:** célközönség / felhasználási kontextus.

---

## 11) „Mini önálló előkészítése” (5 perc brief)

- Válassz 1 kérdést → **egy üzenet**
    
- Válassz megfelelő chartot (bar/line/scatter elsődleges)
    
- Kötelező: **cím=következtetés**, 1 highlight szín, null-tengely (bar)
    
- Extra: 1 annotáció vagy referencia-vonal
    

**Elméleti híd:** 5 kérdéses ellenőrző lista (üzenet, típus, encoding, redukció, hierarchia).