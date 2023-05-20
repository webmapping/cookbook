# GeoJSON Daten asynchron laden und visualisieren

## Zutaten

- das Resultat vom Rezept  [Layer Control für Overlays](https://webmapping.github.io/cookbook/control_layers_overlays) ([Source](https://github.com/webmapping/cookbook/blob/main/control_layers_overlays_example.html))
- Open Government Daten der Stadt Wien
- Javascript `async function` mit `fetch`, `await` und `json`
- Leaflet `L.geoJSON()`

## Ablauf

1. die Karte vorbereiten

    - auf Wien mit Zoomlevel 13 blicken

        ```javascript
        map.setView([48.208493, 16.373118], 13);
        ```

    - den Code für die Marker mit Popup löschen

        ~~`let marker = L.marker([47.267222, 11.392778]).addTo(overlays.innsbruck);`~~  
        ~~`marker.bindPopup("Innsbruck");`~~  
        ~~`marker.openPopup();`~~  

    - drei neue Overlays definieren

        ```javascript
        let overlays = {
            points: L.featureGroup(),
            lines: L.featureGroup(),
            zones: L.featureGroup()
        };
        ```

    - die neuen Overlays zur Layercontrol hinzufügen

        ```javascript
        L.control.layers({
            // alle Hintergrundlayer
        }, {
            "Vienna Sightseeing Haltestellen": overlays.points.addTo(map),
            "Vienna Sightseeing Linien": overlays.lines.addTo(map),
            "Fußgängerzonen": overlays.zones.addTo(map),
        }
        ```

2. Eine asynchrone Funktion zum Laden von GeoJSON schreiben

    ```javascript
    async function loadGeoJSON(url, overlay) {
        let response = await fetch(url);
        let jsondata = await response.json();
        L.geoJSON(jsondata).addTo(map);
    }
    ```

    > Hinweis: als Argumente werden die URL zum Datensatz und das Overlay an die Funktion übergeben
    >
    > siehe Dokumentation [async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function), [fetch](https://developer.mozilla.org/en-US/docs/Web/API/fetch), [L.geoJSON()](https://leafletjs.com/reference.html#geojson) und [.addTo()](https://leafletjs.com/reference.html#geojson-addto)

3. die Funktion zum Laden für drei GeoJSON Datensätze mit Punkten, Linien und Flächen verwenden

    ```javascript
    loadGeoJSON(
        "https://data.wien.gv.at/daten/geo?service=WFS&request=GetFeature&version=1.1.0&typeName=ogdwien:TOURISTIKHTSVSLOGD&srsName=EPSG:4326&outputFormat=json",
        overlays.points
    )
    loadGeoJSON(
        "https://data.wien.gv.at/daten/geo?service=WFS&request=GetFeature&version=1.1.0&typeName=ogdwien:TOURISTIKLINIEVSLOGD&srsName=EPSG:4326&outputFormat=json",
        overlays.lines
    )
    loadGeoJSON(
        "https://data.wien.gv.at/daten/geo?service=WFS&request=GetFeature&version=1.1.0&typeName=ogdwien:FUSSGEHERZONEOGD&srsName=EPSG:4326&outputFormat=json",
        overlays.zones
    )
    ```

    - als Datenquellen dienen:

        - [Touristische Kraftfahrlinien Haltestellen Vienna Sightseeing Linie Standorte Wien](https://www.data.gv.at/katalog/de/dataset/touristische-kraftfahrlinien-haltestellen-vienna-sightseeing-linie-standorte-wien)
        - [Touristische Kraftfahrlinien Liniennetz Vienna Sightseeing Linie Wien](https://www.data.gv.at/katalog/de/dataset/touristische-kraftfahrlinien-liniennetz-vienna-sightseeing-linie-wien)
        - [Fußgängerzonen Wien](https://www.data.gv.at/katalog/de/dataset/stadt-wien_fugngerzonenwien)

> **Achtung**: das Laden von GeoJSON Daten über das Web ist nur möglich, wenn der Server auf dem die GeoJSON Daten liegen das auch erlaubt. Erlaubt er es nicht, sehen wir eine Fehlermeldung wie zum Beispiel `Cross-Origin Request Blocked: The Same Origin Policy disallows reading the remote resource at ...`  in der Browserkonsole. Mehr zum diesem Thema bei den MDN Web Docs unter [Cross-Origin Resource Sharing (CORS)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) und [CORS errors](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS/Errors)

## Ergebnis

[GeoJSON Daten asynchron laden und visualisieren Beispiel](https://webmapping.github.io/cookbook/geojson_async_example.html) ([Source](https://github.com/webmapping/cookbook/blob/main/geojson_async_example.html))

___
[Inhaltsverzeichnis](https://webmapping.github.io/cookbook/index)
