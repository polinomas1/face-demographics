# Veido atpažinimas ir demografinių savybių įvertinimas

## Projekto apžvalga
Šio darbo tikslas – aptikti veidus vaizdo įrašuose ir kiekvienam aptiktam veidui
įvertinti bent dvi demografines savybes: **apytikslį amžių** ir **lytį**.

Projektas naudoja iš anksto apmokytus dirbtinio intelekto modelius, todėl
modelių mokymas nuo nulio nėra reikalingas. Analizės rezultatai pateikiami
vizualiai (anotuotas vaizdo įrašas) ir struktūrizuotai (CSV failas bei grafikai).

## Naudotos technologijos ir bibliotekos
- **Python**
- **OpenCV** – vaizdo įrašų nuskaitymui, kadrų apdorojimui ir anotuoto vaizdo įrašo generavimui
- **DeepFace** – veidų aptikimui ir demografinių savybių (amžiaus, lyties) įvertinimui
- **Pandas** – rezultatų kaupimui ir CSV failo generavimui
- **Matplotlib** – statistinių grafikų generavimui
- **TQDM** – progreso juostai vaizdo analizės metu

## Repozitorijos struktūra
face-demographics/
├─ src/ # Python skriptai
├─ notebooks/ # Google Colab notebook
├─ data/ # Įvesties vaizdo įrašai
├─ results/ # Sugeneruoti rezultatai
├─ docs/ # Papildoma dokumentacija
├─ requirements.txt # Naudotos bibliotekos
└─ README.md

## Įvesties duomenys
Analizei naudojamas trumpas vaizdo įrašas su žmonių veidais.
Vaizdo įrašas buvo gautas su asmenų sutikimu.

Alternatyviai gali būti naudojami vieši duomenų rinkiniai:
- **UTKFace** – veidų nuotraukų rinkinys su amžiaus ir lyties anotacijomis
- **CelebA** – veidų nuotraukų rinkinys su papildomais atributais

## Metodika
1. Vaizdo įrašas įkeliamas į **Google Colab** aplinką.
2. Kiekvienas vaizdo kadras apdorojamas naudojant **OpenCV**.
3. **DeepFace** biblioteka aptinka veidus ir įvertina:
   - apytikslį amžių,
   - dominuojančią lytį.
4. Aptikti veidai pažymimi rėmeliais, o ant kadro pateikiama amžiaus ir lyties informacija.
5. Analizės rezultatai kaupiami CSV faile.
6. Papildomai sugeneruojami statistiniai grafikai.

Jei kadre veidas neaptinkamas, analizė tęsiama be klaidos (`enforce_detection=False`).

## Išvestis
Projektas sugeneruoja:
- **Anotuotą vaizdo įrašą** su pažymėtais veidais ir demografinėmis savybėmis
- **CSV failą** (`analysis_data.csv`) su šiais stulpeliais:
  - `frame` – kadro numeris
  - `timestamp` – laikas sekundėmis
  - `age` – apytikslis amžius
  - `gender` – dominuojanti lytis
- **Grafikus**:
  - amžiaus pasiskirstymo histogramą
  - lyčių pasiskirstymo diagramą

## Paleidimas (Google Colab)
1. Atidarykite `notebooks/demo_colab.ipynb`.
2. Paleiskite pirmą langelį, kuris įdiegia reikalingas bibliotekas.
3. Įkelkite savo vaizdo įrašą naudodami Colab įkėlimo funkciją.
4. Paleiskite analizės langelius.
5. Atsisiųskite sugeneruotus failus iš `results/` aplanko.

## Atkuriamumas
- Visos naudojamos bibliotekos nurodytos `requirements.txt` faile.
- Naudojami tik iš anksto apmokyti modeliai.
- Analizė yra atkuriama naudojant tą patį vaizdo įrašą ir tą pačią Colab aplinką.

## Žinomos problemos ir ribotumai
- Amžiaus įvertinimas yra apytikslis ir gali skirtis priklausomai nuo apšvietimo ir vaizdo kokybės.
- Esant dideliam vaizdo įrašui, analizė gali užtrukti ilgiau.
- `RetinaFace` veidų aptikimo metodas yra tikslesnis, tačiau lėtesnis.

## Išvados
Projektas sėkmingai demonstruoja, kaip naudojant dirbtinio intelekto metodus
galima aptikti veidus vaizdo įrašuose ir įvertinti jų demografines savybes.
Naudojant iš anksto apmokytus modelius, pasiekiami geri rezultatai be papildomo
modelių mokymo.