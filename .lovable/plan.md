
# Fintutto Mieter - Mobile-First Mieter-App

## Übersicht
Eine vollständige Mobile-First Web-App für Mieter mit Supabase-Backend, die Mietzahlungen, Mängelmeldungen, Zählerablesungen und Kommunikation mit der Hausverwaltung vereint.

## Design System
- **Primär**: Indigo (#4F46E5)
- **Sekundär**: Violett (#7C3AED)
- **Hero Gradient**: linear-gradient(135deg, #4F46E5 0%, #7C3AED 100%)
- **Font**: Inter (Google Fonts)
- **Sprache**: Deutsch (formelle Anrede)
- **Mobile-First** mit Bottom-Navigation

---

## 1. Authentifizierung
- Login-Seite mit Email/Passwort
- Registrierung für neue Mieter
- Passwort zurücksetzen
- Geschützter Bereich (nur eingeloggte Nutzer)

## 2. Bottom-Navigation (5 Tabs)
| Tab | Icon | Funktion |
|-----|------|----------|
| Home | 🏠 | Dashboard-Übersicht |
| Finanzen | 💰 | Miete & Zahlungen |
| Melden | ➕ | Floating Action Menu (hervorgehoben) |
| Chat | 💬 | Nachrichten |
| Mehr | ☰ | Weitere Optionen |

## 3. Home-Dashboard
- Persönliche Begrüßung "Hallo, [Name]!"
- **Karte**: Nächste Mietzahlung (Betrag, Fälligkeitsdatum)
- **Karte**: Anzahl offene Meldungen mit Status
- **Quick Actions**: Zähler ablesen, Mangel melden
- **Letzte Nachrichten**: Preview der neuesten Chats

## 4. Finanzen-Bereich
- Aktueller Kontostand (Guthaben/Nachzahlung)
- Miete-Aufschlüsselung:
  - Kaltmiete
  - Nebenkosten
  - Gesamtbetrag
- Zahlungshistorie (Liste vergangener Zahlungen)

## 5. Melden (Floating Action Menu)
Beim Tippen auf den "+" Button erscheinen drei Optionen:

### 5.1 Mangel melden
- Kategorie wählen (Sanitär, Elektrik, Heizung, etc.)
- Beschreibung eingeben
- Foto aufnehmen/hochladen
- Dringlichkeit festlegen (Niedrig, Mittel, Hoch, Notfall)

### 5.2 Zähler ablesen
- Zählertyp wählen (Strom, Gas, Kaltwasser, Warmwasser)
- Foto des Zählers hochladen
- Zählerstand manuell eingeben
- Anzeige: Vorheriger Stand + berechneter Verbrauch

### 5.3 Dokument anfragen
- Dokumenttyp wählen (Mietbescheinigung, Nebenkostenabrechnung, etc.)

## 6. Chat-Bereich
- Liste aller Konversationen
- Chat mit Hausverwaltung
- Chat mit Hausmeister
- Nachrichten mit Zeitstempel
- Gelesen/Ungelesen-Status

## 7. Mehr-Menü
- **Meine Wohnung**: Adresse, Wohnungsdaten
- **Dokumente**: Mietvertrag, Abrechnungen
- **Hausordnung**: PDF/Text-Ansicht
- **Notfallkontakte**: Wichtige Telefonnummern
- **Einstellungen**: Profil, Benachrichtigungen, Logout

---

## Supabase-Datenbank

### Tabellen
1. **profiles** - Mieter-Profile (name, unit_id, phone)
2. **units** - Wohnungen (address, rent_cold, rent_utilities)
3. **issues** - Mängelmeldungen (user_id, category, description, image_url, priority, status)
4. **meter_readings** - Zählerablesungen (user_id, meter_type, value, image_url, previous_value)
5. **messages** - Chat-Nachrichten (sender_id, recipient_id, content, is_read)
6. **payments** - Zahlungshistorie (user_id, amount, payment_date, type)

### Storage
- **issue-images**: Fotos für Mängelmeldungen
- **meter-images**: Fotos von Zählerständen

### Row Level Security
- Mieter sehen nur eigene Daten
- Nachrichten nur für Sender/Empfänger sichtbar

---

## Implementierungsreihenfolge
1. Design System & Layout mit Bottom-Navigation
2. Supabase Setup (Auth, Tabellen, RLS)
3. Login/Registrierung
4. Home-Dashboard
5. Finanzen-Bereich
6. Melden-Funktionen (Mängel, Zähler)
7. Chat-System
8. Mehr-Menü & Einstellungen
