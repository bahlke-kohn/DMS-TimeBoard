# DMS-TimeBoard
Mit diesem Skript können Inhalte wie Webseiten oder Bilder dynamisch in einem fullscreen-iFrame angezeigt werden.



Dieses Dokument beschreibt die grundlegenden Funktionen und Einstellungen des DMS-TimeBoards. 
Mit diesem Skript können Inhalte wie Webseiten oder Bilder dynamisch, nach Zeitplan in einem fullscreen-iFrame angezeigt werden.


## Funktionen
- **Fullscreen-Inhalte**: Zeigt Webseiten oder Bilder im Vollbildmodus an.
- **Zeitgesteuerte Inhalte**: Ändert die angezeigten Inhalte basierend auf einem Tageszeitplan.
- **Debug-Modus**: Zeigt zusätzliche Informationen wie Zeit, aktive URL und Zeitpläne an.
- **Automatische Aktualisierung**: Synchronisiert sich automatisch zu vollen Minuten.



## Konfigurierbare Parameter

### 1. `config.showDebugInfo`
- **Beschreibung**: Aktiviert oder deaktiviert den Debug-Modus.
- **Werte**: 
  - `true`: Debug-Banner wird angezeigt.
  - `false`: Debug-Banner wird ausgeblendet.

### 2. `config.dailySchedules`
- **Beschreibung**: Legt fest, welche Inhalte zu bestimmten Zeiten an welchem Wochentag angezeigt werden.
- **Struktur**:
  ```javascript
  dailySchedules: {
      1: [ // Montag
                    { from: "01:00", to: "05:00", url: "test.jpg" },
                    { from: "05:01", to: "15:00", url: "departure.html" },
                    { from: "15:01", to: "23:59", url: "depot.html" }
      ]
  }
  ```

### 3. `config.defaultUrl`
- **Beschreibung**: URL, die angezeigt wird, wenn kein passender Eintrag im Zeitplan gefunden wird.
- **Beispiel**: `"fallback.html"`

### 4. Aktualisierungsrate
- **Beschreibung**: Die Inhalte werden alle 60 Sekunden aktualisiert.
- Ändern Sie `setInterval updateIframeUrl` von `60000` auf den gewünschten Wert.

1. **Zeitplan anpassen**:
   - Bearbeiten Sie das Objekt `config.dailySchedules`, um Ihre Inhalte und Zeiten festzulegen.
2. **Debug-Modus aktivieren**:
   - Setzen Sie `config.showDebugInfo` auf `true`, um das Debug-Banner einzublenden.
3. **Bereitstellung**:
   - Laden Sie die HTML-Datei und die referenzierten Inhalte (z. B. Bilder, Webseiten) auf Ihren Server hoch bzw. geben im `config.dailySchedules` die URL oder FilePath an.

## Beispiel-Zeitplan
```javascript
        const config = {
            showDebugInfo: true, // HIER KANN DER DEBUG MODE EIN UND AUS GESTELLT WERDEN
            dailySchedules: {

                // Montag
                1: [
                    { from: "02:00", to: "02:59", url: "test.jpg" },
                    { from: "09:00", to: "16:32", url: "departure.html" },
                    { from: "17:01", to: "22:00", url: "depot.html" }
                ],
                // Dienstag
                2: [
                    { from: "09:00", to: "12:00", url: "departure.html" },
                    { from: "17:01", to: "22:00", url: "depot.html" }
                ],
                // Mittwoch
                3: [
                    { from: "09:00", to: "12:00", url: "departure.html" },
                    { from: "17:01", to: "22:00", url: "depot.html" }
                ],
                // Donnerstag
                4: [
                    { from: "09:00", to: "12:00", url: "departure.html" },
                    { from: "17:01", to: "22:00", url: "depot.html" }
                ],
                // Freitag
                5: [
                    { from: "02:00", to: "02:59", url: "test.jpg" },
                    { from: "11:27", to: "11:28", url: "departure.html" },
                    { from: "13:00", to: "21:44", url: "depot.html" }
                ],
                // Samstag
                6: [
                    { from: "09:00", to: "12:00", url: "departure.html" },
                    { from: "17:01", to: "22:00", url: "depot.html" }
                ],
                // Sonntag
                0: [
                    { from: "01:59", to: "02:03", url: "departure.html" },
                    { from: "02:07", to: "11:26", url: "depot.html" },
                    { from: "11:27", to: "11:28", url: "departure.html" }
                ]
            },
            defaultUrl: "fallback.html" // HIER KANN DIE FALLBACK URL GESTELLT WERDEN
        };
```


