# haraldur.pro — lagfæringar sem þarf að gera

Þetta er `index.html` — ein skrá, engin build-skref. Allt er í þeirri einni skrá.

Gerðu allar lagfæringar hér að neðan **í einni commit** á `main` branch. Skrifaðu skýrt commit message.

---

## 1. Bæta við `<meta>` tags í `<head>` (vantar alveg)

Bæta við þessum þremur tags rétt á eftir `<meta name="viewport" ...>`:

```html
<meta name="description" content="Haraldur Karlsson — visual artist and technologist based in Reykjavík. Technical consultancy, policy research, and workshops for cultural organisations.">
<meta property="og:title" content="Haraldur Karlsson">
<meta property="og:description" content="I make the work and build the tools I wish existed — for any space, any body, any scale.">
<meta property="og:image" content="https://haraldur.pro/hero.jpg">
<meta property="og:url" content="https://haraldur.pro">
<meta property="og:type" content="website">
```

---

## 2. Gera `haraldur.net` smellanlegt í about-texta (öll þrjú tungumál)

Í `strings` hlutnum í JavaScript — í `about` gildunum fyrir `en`, `is` og `no` — er `haraldur.net` skrifað sem venjulegur texti. Þetta þarf að breyta þannig að linkurinn sé sýnilegur.

**Vandinn:** `el.textContent = s[key]` ræður ekki við HTML. Við þurfum að nota `innerHTML` þar sem lykillinn inniheldur HTML-link.

**Lausn:**

1. Breyta `about`-gildunni í öllum þremur tungumálum þannig að `haraldur.net` verði:
   ```
   <a href="https://haraldur.net" target="_blank" rel="noopener">haraldur.net</a>
   ```
   (Hafðu restina af textanum óbreyttan.)

2. Í `setLang()` fallinu — breyta `.textContent` í `.innerHTML` **eingöngu** fyrir `about`-lykil. Einfaldasta leiðin: bætið við sérstakri athugun:
   ```js
   if (key === 'about') {
     el.innerHTML = s[key];
   } else {
     el.textContent = s[key];
   }
   ```

---

## 3. Laga `contact_href` bug — email-linkurinn uppfærist ekki við tungumálaskipti

**Vandinn:** `<a href="mailto:haraldur@haraldur.pro" data-i18n-href="contact_href">` — `data-i18n-href` attributinn er aldrei lesinn í `setLang()`. Þetta er harmless í dag (emailinn er alltaf sá sami), en kóðinn er misleidandi.

**Lausn:** Fjarlægja `data-i18n-href="contact_href"` attribute úr `<a>` taginu (línur ~242). Emailinn `href="mailto:haraldur@haraldur.pro"` er rétt og á að vera harðkóðaður.

---

## 4. Bæta við `<link rel="canonical">` í `<head>`

Rétt á eftir `<title>` taginu:
```html
<link rel="canonical" href="https://haraldur.pro">
```

---

## 5. Bæta við `favicon` í `<head>`

Einfaldasta lausnin (enginn sérstakur favicon-skrá þarf):
```html
<link rel="icon" href="data:,">
```
Þetta kemur í veg fyrir 404-villa í console þegar vafrinn biður um favicon.

---

## Ekki breyta

- Hönnun, litir, layout — ekkert af þessu.
- Tagline textana — þeir eru réttir og settlir.
- Hero og portrait myndir.
- Þrjú þjónustukort og innihald þeirra.
- Footer og SÍM-link.
- Tungumálaskiptakerfi (nema breytingarnar í lið 2 og 3 hér að ofan).

---

## Eftir commit

Cloudflare Pages deployar sjálfkrafa á hvert push á `main`. Engar aðrar aðgerðir þarf.
