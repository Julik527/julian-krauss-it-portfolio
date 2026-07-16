# Qualitätsprüfung

Stand: 16. Juli 2026

## Automatisierte Prüfungen

- `npm run lint`: bestanden
- `npm run typecheck`: bestanden
- `npm run build`: bestanden
- Produktions-Build mit 73 statisch erzeugten Seiten und einem dynamischen Kontakt-Endpunkt
- Interner Link-Crawl ab `/de` und `/en`: 39 erreichbare Seiten/Dateien geprüft, keine fehlerhaften internen Links
- `sitemap.xml`, `robots.txt`, Open-Graph-Bild, App-Icon, Manifest und Lebenslauf-PDF: HTTP 200
- Kontakt-Endpunkt: Validierung, Mindest-Ausfüllzeit, Honeypot und Fehlermeldungen geprüft

## Visuelle Stichproben

- Startseite Desktop
- Startseite Smartphone
- Projektdetailseite Desktop
- Lebenslauf-PDF nach dem Rendern kontrolliert
- Hell-/Dunkel-Farbsystem, Fokuszustände und reduzierte Animationen im Stylesheet geprüft

Die Vorschaubilder liegen unter `docs/previews/`.

## Vor Veröffentlichung zwingend ergänzen

1. Echte Domain in `NEXT_PUBLIC_SITE_URL`
2. Öffentliche Kontakt-E-Mail-Adresse
3. GitHub- und optional LinkedIn-Profil
4. Korrekte Impressumsanschrift
5. Versanddienst für das Kontaktformular, etwa Resend oder ein privater Webhook
6. Individuelle Praktikumsdaten und gegebenenfalls genauere Schulangaben im Lebenslauf
7. Rechtstexte passend zum tatsächlichen Hosting- und Mailanbieter prüfen

Diese Werte wurden bewusst nicht erfunden. Ohne Versandkonfiguration zeigt das Kontaktformular in Produktion eine ehrliche Fehlermeldung statt eines falschen Erfolgs.
