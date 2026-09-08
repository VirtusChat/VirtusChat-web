# 💬 VirtusChat — Oficiální web & GitHub Pages

Oficiální prezentační web a landing page pro projekt **VirtusChat** (připraveno pro hosting na **GitHub Pages**). Stránka slouží k představení projektu, stažení klientských verzí, přehledu bezpečnostní architektury a prezentaci týmu.

Web je stylizován do unikátního **DirectX 9 / Y2K Aero Obsidian skeuomorfního designu**, který věrně kopíruje nativní rozhraní desktopového klienta.

---

## 🚀 Rychlý start pro GitHub Pages

Tento repozitář je koncipován jako statický web bez nutnosti kompilace či složitého bundlování.

### Zapnutí hostingu přes GitHub Pages:
1. Přejděte do nastavení repozitáře: **Settings** -> **Pages**.
2. V sekci **Build and deployment**:
   - **Source:** Vyberte `Deploy from a branch`.
   - **Branch:** Vyberte `main` (nebo `master`) a složku `/ (root)`.
3. Klikněte na **Save**.
4. Během minuty bude web dostupný na adrese:
   ```text
   https://<uzivatelske-jmeno-nebo-organizace>.github.io/<nazev-repozitare>/
   ```

### Lokální náhled:
Stránku můžete otevřít přímo poklepáním na soubor `index.html` v libovolném moderním webovém prohlížeči, nebo spustit lokální HTTP server:

```bash
# Pomocí Pythonu 3:
python3 -m http.server 8080

# Nebo pomocí npx serve / live-server:
npx serve .
```
Otevřete v prohlížeči `http://localhost:8080`.

---

## 📁 Struktura projektu

```text
.
├── index.html            # Hlavní produkční stránka (s kompletní konfigurací a sekcí týmu)
├── index-bez-lidi.html   # Alternativní/záložní verze stránky bez sekce týmu
├── icons/                # Složka s avatary členů týmu a grafickými prvky
│   ├── queen.png
│   ├── kotak.png
│   ├── mrtomicz.png
│   ├── noname.png
│   └── tobias.png
└── README.md             # Dokumentace a příručka pro vývojáře
```

---

## ⚙️ Správa a úprava obsahu (`VITUS_CONFIG`)

Všechny texty, odkazy na stažení, členové týmu a oznámení se spravují na jednom centrálním místě v souboru `index.html` uvnitř objektu `const VITUS_CONFIG`:

```javascript
const VITUS_CONFIG = {
  // 0. ČERVENÝ OZNAMOVACÍ PÁS (ZAPNOUT: true / VYPNOUT: false)
  announcement: {
    show: true,
    badgeText: "DŮLEŽITÉ OZNÁMENÍ",
    message: "Aplikace VitusChat je ve fázi aktivního testování. Aktivní vývoj"
  },
  ...
}
```

### 1. Změna stavu ke stažení (Releases / Download centrum)
V sekci `downloads` můžete jednotlivé platformy jednoduše aktivovat/deaktivovat přepínačem `active: true / false` a nastavit odkaz na nový GitHub Release:

```javascript
{
  icon: "🪟",
  title: "Windows 11 / 10 / 7",
  subtitle: "Instalátor (.exe)",
  active: true, // true = zelené aktivní tlačítko / false = šedé 'Momentálně nedostupné'
  link: "https://github.com/VirtusChat/VirtusChat-win/releases",
  statusActive: "K dispozici ke stažení (.exe)",
  statusDisabled: "Momentálně nedostupné"
}
```

### 2. Správa a přidávání členů do týmu
V sekci `teamSections` lze snadno spravovat kategorie (Vedení, Vývojáři, Testeři apod.) a jednotlivé profily:

```javascript
teamSections: [
  {
    title: "Vývojový tým (Developers)",
    icon: "💻",
    isLeadership: false,
    members: [
      {
        avatar: "icons/jmeno.png", // cesta k obrázku ve složce icons/
        name: "Nick",
        role: "Developer",
        badgeType: "", // 'owner', 'security', nebo prázdné
        desc: "Popis činnosti a odpovědností člena týmu...",
        contacts: [
          { text: "Discord: Nick", link: "", clickable: false },
          { text: "E-mail: nick@virtuschat.com", link: "mailto:nick@virtuschat.com", clickable: true },
          { text: "GitHub: github.com/nick", link: "https://github.com/nick", clickable: true }
        ]
      }
    ]
  }
]
```

### 3. Otázky a odpovědi (FAQ)
Přidání nové otázky do akordeonu:
```javascript
faqs: [
  {
    q: "Vaše nová otázka?",
    a: "Podrobná odpověď (podporuje i HTML tagy jako <strong>).",
    open: false
  }
]
```

---

## 👥 Tým projektu

- 👑 **Queen** — *Owner & Koordinační vedení*
- 🛡️ **Koťák** — *Dohled nad procesem, architekturou & bezpečností*
- 💻 **MrTomiCZ** — *Developer*
- 💻 **NoName** — *Developer*
- 💻 **Tobias** — *Developer*

---

## 🛠️ Pravidla pro přispívání do repozitáře (Workflow pro tým)

1. **Nenahrávejte přímo do `main`**: Vždy vytvořte samostatnou větev (např. `feat/update-downloads` nebo `content/team-update`).
2. **Optimalizace obrázků**: Nové avatary nahrávejte do složky `icons/` s rozumnou velikostí (čtvercový formát, PNG/WebP, ideálně do 200 KB).
3. **Validace syntaxe JS**: Při úpravách v `VITUS_CONFIG` dbejte na správné čárky a uvozovky, aby nedošlo k chybě parseru v prohlížeči.
4. **Ověření před commitem**: Před odesláním Pull Requestu si otevřete `index.html` lokálně a vyzkoušejte zobrazení na desktopu i mobilním zařízení.
