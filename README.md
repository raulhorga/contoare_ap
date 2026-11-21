# Casa mea — contoare și facturi

Aplicație web independentă, optimizată pentru telefon și desktop, inspirată din tabelul fotografiat și din aspectul aplicației „Notițele noastre”.

## Pornire

Deschide `index.html` într-un browser pentru o utilizare locală sau publică toate cele 5 fișiere (`index.html`, `styles.css`, `app.js`, `manifest.webmanifest`, `icon.svg`) într-un director pe un site HTTPS (de exemplu GitHub Pages). Pe telefon, folosește opțiunea „Adaugă pe ecranul principal”.

## Ce conține

- Citiri cumulative lunare: apă baie mică, apă baie mare, gaz și curent.
- Consumul calculat ca diferența dintre citirea lunii și ultima citire anterioară disponibilă, inclusiv între ani. Dacă nu există o citire precedentă, consumul este „—”. Dacă valoarea scade, consumul nu este calculat (posibil contor schimbat).
- Cheltuieli lunare în RON: factură gaz, factură curent, întreținere bloc, internet / televizune, altele. O factură de curent este un singur câmp, deoarece cererea o repeta de două ori; poate fi extinsă dacă sunt două facturi diferite.
- Dashboard cu total pe lună/an, grafic pe 12 luni, defalcare, tabele și export CSV.
- Ani anteriori și viitori, RO/EN și temă zi/noapte (preferințe memorate pe dispozitiv).

## EtherCalc și siguranța datelor

Foaie configurată: https://calc.domainepublic.net/efzx9g0n1r12

Aplicația încearcă să citească CSV din `/_/efzx9g0n1r12/csv` sau `/=efzx9g0n1r12.csv` și să scrie CSV cu `PUT /_/efzx9g0n1r12`. Datele sunt salvate imediat în `localStorage`, apoi sincronizate dacă serverul permite CORS și operațiile de scriere/citire. Salvarea online este confirmată doar după o recitire și verificare a înregistrărilor.

**Atenție:** nu am putut testa efectiv scrierea în această foaie. Dacă foaia conține deja alte informații sau o structură necunoscută, aplicația refuză să o suprascrie. Dacă serverul nu acceptă sincronizarea directă, datele rămân doar pe dispozitiv; utilizează Export CSV pentru copii de rezervă. Nu șterge datele din browser înainte de a verifica salvarea pe server. EtherCalc nu oferă automat autentificare privată; persoanele cu linkul ar putea avea acces la date.

Schema CSV: `record_type,month,water_small,water_large,gas,electricity,gas_bill,electric_bill,maintenance,internet_bill,other,notes,updated_at,deleted`. Fiecare lună are cheia `YYYY-MM` și este un rând din foaie. Câmpurile necompletate sunt distincte de zero.

## Datele din fotografii

Fotografiile sunt folosite ca inspirație pentru câmpuri și structură. Nu am importat automat citirile istorice de mână, pentru a nu introduce valori greșite; ele pot fi transcrise manual, lună de lună.
