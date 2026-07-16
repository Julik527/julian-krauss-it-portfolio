# Julian Krauß | IT Portfolio

Eine moderne, zweisprachige und produktionsfähige Portfolio-Website für IT-Praktika, Ausbildungsbewerbungen, technische Projekte und die langfristige Dokumentation eines Homelabs.

## Technischer Stack

- Next.js 16 mit App Router
- React 19
- TypeScript
- Tailwind CSS 4
- Server Components und gezielte Client Components
- Route Handler für das Kontaktformular
- Keine UI-Bibliothek, keine externen Schriftarten, kein Tracking

## Enthaltene Seiten

- Startseite
- Über mich / About
- Projektübersicht mit Filter
- Sechs ausführliche Projektdetailseiten
- Homelab mit eigener SVG-/CSS-Architekturvisualisierung
- Kenntnisse ohne künstliche Prozentwerte
- Digitaler Lebenslauf und PDF-Download
- Blog mit drei vollständigen Artikeln
- Kontaktformular mit Spam-Schutz
- Impressum und Datenschutz
- Eigene 404-, Lade- und Fehleransicht

## Lokale Installation

Voraussetzungen: Node.js 22 LTS oder neuer und npm.

```bash
npm install
cp .env.example .env.local
npm run dev
```

Danach ist die Website unter `http://localhost:3000` erreichbar. Die deutsche Version startet unter `/de`, die englische Version unter `/en`.

## Umgebungsvariablen

Vor einer öffentlichen Veröffentlichung müssen mindestens folgende Werte korrekt gesetzt werden:

```env
NEXT_PUBLIC_SITE_URL=https://deine-domain.de
NEXT_PUBLIC_CONTACT_EMAIL=deine-echte-mailadresse@example.de
NEXT_PUBLIC_GITHUB_URL=https://github.com/dein-benutzername
NEXT_PUBLIC_LINKEDIN_URL=

NEXT_PUBLIC_LEGAL_STREET=Straße und Hausnummer
NEXT_PUBLIC_LEGAL_POSTAL_CODE=PLZ
NEXT_PUBLIC_LEGAL_CITY=Ort
```

Eine ladungsfähige Anschrift und echte Kontaktadresse dürfen aus rechtlichen und sachlichen Gründen nicht erfunden werden. Die Website zeigt bei fehlender Konfiguration im Impressum einen deutlichen Hinweis.

### Kontaktformular

Für den Versand kann entweder Resend oder ein eigener privater Webhook verwendet werden.

Resend:

```env
RESEND_API_KEY=re_...
CONTACT_TO_EMAIL=ziel@example.de
CONTACT_FROM_EMAIL=Portfolio <portfolio@deine-domain.de>
```

Webhook:

```env
CONTACT_WEBHOOK_URL=https://dein-privater-endpunkt.example/webhook
```

Ohne Versandkonfiguration werden Nachrichten in der lokalen Entwicklung in der Serverkonsole ausgegeben. In Produktion wird kein falscher Erfolg angezeigt, sondern eine verständliche Fehlermeldung.

## Qualität prüfen

```bash
npm run typecheck
npm run lint
npm run build
```

Zusätzlich sollten vor jeder Veröffentlichung geprüft werden:

1. Alle echten Kontakt- und Impressumsdaten
2. GitHub- und LinkedIn-Links
3. Lebenslauf-PDF und individuelle Praktikumsangaben
4. Kontaktversand in der echten Hostingumgebung
5. Mobile Navigation auf realen Geräten
6. Lighthouse für Performance, Accessibility, Best Practices und SEO
7. Datenschutztext passend zum tatsächlich eingesetzten Hosting- und Mailanbieter

## Deployment auf Vercel

1. Repository zu GitHub übertragen.
2. Projekt in Vercel importieren.
3. Umgebungsvariablen im Vercel-Dashboard eintragen.
4. Build Command `npm run build` verwenden.
5. Domain verbinden und `NEXT_PUBLIC_SITE_URL` auf die endgültige HTTPS-Adresse setzen.
6. Kontaktformular mit Resend oder Webhook testen.

Vercel ist für diese Next.js-Anwendung der einfachste Veröffentlichungsweg.

## Deployment auf Cloudflare

Für Cloudflare Workers kann die Anwendung mit dem offiziellen OpenNext-Adapter erweitert werden. Diese Abhängigkeiten sind bewusst nicht standardmäßig installiert, damit die normale Installation schlank und zuverlässig bleibt.

```bash
npm install -D @opennextjs/cloudflare wrangler
npx opennextjs-cloudflare build
npx opennextjs-cloudflare deploy
```

Vor dem Deployment müssen die aktuelle OpenNext-Konfiguration gemäß der Cloudflare-Dokumentation sowie alle Secrets im Cloudflare-Dashboard eingerichtet werden. Für eine reine statische Veröffentlichung auf Cloudflare Pages müsste das serverseitige Kontaktformular durch einen externen Formular-Endpunkt ersetzt oder deaktiviert werden.

## Ordnerstruktur

```text
src/
├── app/
│   ├── [lang]/              # Deutsche und englische Seiten
│   ├── api/contact/         # Serverseitiges Kontaktformular
│   ├── icon.tsx             # Dynamisches App-Icon
│   ├── opengraph-image.tsx  # Social-Preview
│   ├── robots.ts
│   └── sitemap.ts
├── components/              # Wiederverwendbare UI-Komponenten
└── lib/
    ├── data/                 # Projekt- und Blogdaten
    ├── i18n/                 # Übersetzbare UI-Texte
    ├── site.ts               # Öffentliche Konfiguration
    ├── types.ts
    └── utils.ts
```

## Inhalte bearbeiten

- Projekte: `src/lib/data/projects.ts`
- Blogartikel: `src/lib/data/blog.ts`
- Navigation und allgemeine Texte: `src/lib/i18n/`
- Kontaktdaten und Domain: Umgebungsvariablen
- Lebenslauf-PDF: `public/downloads/lebenslauf-julian-krauss.pdf`

## Sicherheit und Datenschutz

- Keine geheimen Schlüssel im Repository
- Serverseitige Formularvalidierung
- Honeypot und Mindest-Ausfüllzeit
- Einfaches Rate Limiting pro IP
- Security Header und Content Security Policy
- Keine extern geladenen Fonts
- Kein Analytics- oder Werbetracking
- Keine eingebetteten Drittanbieterinhalte
- Theme-Auswahl nur lokal im Browser

Das im Arbeitsspeicher geführte Rate Limiting ist ein sinnvoller Basisschutz. Für stark frequentierte produktive Deployments sollte es durch einen zentralen Store wie Cloudflare KV oder einen vergleichbaren Dienst ersetzt werden.

## Rechtlicher Hinweis

Die enthaltenen Rechtstexte sind auf die technische Grundkonfiguration zugeschnitten, aber keine individuelle Rechtsberatung. Hostinganbieter, Versanddienst, tatsächliche Anschrift, Aufbewahrungsdauer und weitere Integrationen müssen vor Veröffentlichung korrekt eingetragen und geprüft werden.
