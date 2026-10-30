# Recepti i kalkulacija

Aplikacija za recepte koja računa **cenu koštanja po porciji** na osnovu liste sastojaka i cena —
isti princip kao Excel kalkulator (`Lista sastojaka` + `Recepture` → `Cene jela po porciji`).

Jedna aplikacija (`app/index.html`) radi na dva načina:

| Platforma | Kako |
|---|---|
| **Windows** | Dvoklik na `Pokreni-na-Windows.bat` (ili `app/index.html`) — otvara se u Edge/Chrome, radi bez interneta. |
| **Android** | APK napravljen iz foldera `android/` (WebView koji prikazuje istu aplikaciju). |

## Šta aplikacija radi

- **Jela** — naziv, broj porcija, sastojci (po nazivu ili OCIS šifri), količina u kg/g/l/dl/ml/kom.
  Odmah računa cenu koštanja recepta, **cenu po porciji**, normativ po porciji i predlog prodajne cene (prema % udela namirnica).
- **Namirnice** — šifra, naziv, jedinica (kg / l / kom), cena po jedinici. Pretraga po nazivu i šifri.
- **Uvoz iz Excela** — učitava `.xlsx/.xlsm` kalkulator: list `Lista sastojaka` (Code, Item, Case, Case Value)
  i list `Recepture` (Ime jela, Broj porcija, Ocis sastojka, Količina sastojaka).
  Ponovni uvoz ažurira cene po šifri, pa se cene jela automatski preračunaju.
- **Izvoz u Excel** — „Cene jela po porciji“ i ceo kalkulator (Lista sastojaka + Recepture).
- **Rezervna kopija** (.json) — za prenos podataka između telefona i računara.

Podaci se čuvaju lokalno na uređaju (ništa se ne šalje na internet).

## Pravljenje APK-a

### Varijanta A — automatski preko GitHub-a (ne treba ništa instalirati)
1. Napravi repozitorijum na GitHub-u i postavi ceo folder `recepti`.
2. Na kartici **Actions** pokreće se „Build APK“ (traje ~3–5 min).
3. Kad završi, otvori taj build → **Artifacts** → `recepti-apk` → preuzmi zip, u njemu je `app-debug.apk`.
4. Prebaci APK na telefon i instaliraj (dozvoli „instalaciju iz nepoznatih izvora“).

### Varijanta B — Android Studio
1. Otvori folder `android/` u Android Studiju.
2. **Build → Build App Bundle(s) / APK(s) → Build APK(s)**.
3. APK je u `android/app/build/outputs/apk/debug/`.

Za objavu na Google Play potreban je potpisan *release* build (Build → Generate Signed Bundle / APK).
