# Erste Leaflet Karte mit Marker und Popup

## Zutaten

- Browser & Visual Studio Code
- Leafletbibliothek unter <https://leafletjs.com>
- eine `index.html` Datei mit dem Visual Studio Code `html 5` Baustein als Grundgerüst

## Ablauf

1. den Kartenbereich vorbereiten

    - ein DIV Element mit einem ID Attribut `map` hinzufügen

        ```html
        <div id="map"></div>
        ```

    - die zukünftige Kartenfläche über eine STYLE Element im HEAD Bereich festlegen - die Karte wird 90% der Fensterbreite einnehmen, 600 Pixel hoch sein und einen hellgrauen Rahmen aufweisen

        ```html
        <style>
            #map {
                width: 90%;
                height: 600px;
                border: 1px solid silver
            }
        </style>
        ```

2. die Leaflet Bibliothek einbinden

    - der Codeblock zum Einbinden der Leaflet Bibliothek im HEAD Bereich von `index.html` kommt von der Leaflet-Download Seite unter <https://leafletjs.com/download.html> und verlinkt die Leaflet CSS und Javascript Dateien

        ```html
        <head>
            <!-- Leaflet Bibliothek -->
            <link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.3/dist/leaflet.css" integrity="sha256-kLaT2GOSpHechhsozzB+flnD+zUyjE2LlfWPgU04xyI=" crossorigin="" />
            <script src="https://unpkg.com/leaflet@1.9.3/dist/leaflet.js" integrity="sha256-WBkoXOwTeyKclOHuWtc+i2uENFpDZ9YPdf5Hf+D7ewM=" crossorigin=""></script>
        </head>
        ```

3. den Javascript Code für die Karte erstellen

    - unmittelbar nach dem DIV Element der Karte ein SCRIPT Element für die Javascript Befehle einfügen

        ```html
            <script>

            </script>
        ```

    - die Karte im DIV mit der ID `map` initialiseren und im Zoomlevel 13 auf die Koordinaten von Innsbruck blicken

        ```javascript
        let map = L.map("map");
        map.setView([47.267222, 11.392778], 13);
        ```

        > siehe Dokumentation [L.map()](https://leafletjs.com/reference.html#map) und [.setView()](https://leafletjs.com/reference.html#map-setview)

    - einen WMTS Hintergrundlayer für die OpenStreetMap zur Karte hinzufügen

        ```javascript
        L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
            attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors'
        }).addTo(map);
        ```

        > siehe Dokumentation [L.tileLayer()](https://leafletjs.com/reference.html#tilelayer) und [.addTo()](https://leafletjs.com/reference.html#tilelayer-addto)
        >
        > Hinweis: bequemer Einbauen lassen sich Hintegrundlayer über das Leaflet Provider Plugin - [siehe Rezept hier ...](plugin_leaflet_provider)

    - einen Marker mit Popup im Kartenmittelpunkt erstellen und das Popup öffnen

        ```javascript
        let marker = L.marker([47.267222, 11.392778]).addTo(map);
        marker.bindPopup("Innsbruck");
        marker.openPopup();
        ```

        > siehe Dokumentation [L.marker()](https://leafletjs.com/reference.html#marker), [.addTo()](https://leafletjs.com/reference.html#marker-addto), [.bindPopup()](https://leafletjs.com/reference.html#marker-bindpopup) und  [.openPopup()](https://leafletjs.com/reference.html#marker-openpopup)
        >
        > Hinweis: im Popup sind auch HTML Formatierungen zulässig
        >
        > Hinweis: über Template-Syntax (z.B. \`Popup mit ${someVar}\`) sind im Popup auch Variablen verwendbar

## Ergebnis

[Erste Leaflet Karte mit Marker und Popup Beispiel](https://webmapping.github.io/cookbook/examples/first_leaflet_map.html) ([Source](https://github.com/webmapping/cookbook/blob/main/examples/first_leaflet_map.html))

___
[Inhaltsverzeichnis](https://webmapping.github.io/cookbook/index)
