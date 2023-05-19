# Leaflet Provider Plugin für Hintergrundlayer

## Zutaten

- das Resultat vom Rezept [Erste Leaflet Karte mit Marker und Popup](https://webmapping.github.io/cookbook/first_leaflet_map) ([siehe Source](https://github.com/webmapping/cookbook/blob/main/first_leaflet_map_example.html))
- das Leaflet Provider Plugin unter <https://github.com/leaflet-extras/leaflet-providers>

## Ablauf

1. das Plugin einbinden

    - Suche bei <https://cdnjs.com> nach *"leaflet-provider"* liefert <https://cdnjs.com/libraries/leaflet-providers>

    - Einbau in `index.html` über "*Copy Script Tag"* (\</>) Icon beim Suchergebnis

        ```html
        <!-- Leaflet Provider -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet-providers/1.13.0/leaflet-providers.js" integrity="sha512-pb9UiEEi2JIxkMloqYnqgONe9CTcp2BWWq1Hbz60l7f3R3VhZ57dEE58Ritf/HgBw3o/5Scf5gg0T9V+tf48fg==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        ```

2. Einbau im SCRIPT Element

    - den bestehenden `L.tileLayer` Aufruf durch einen Aufruf an das Plugin ersetzen

        ```javascript
        L.tileLayer.provider('Stamen.Watercolor').addTo(map);
        ```

        > siehe Dokumentation [Leaflet-providers Usage](https://github.com/leaflet-extras/leaflet-providers#usage)

    - über die Demoseite <http://leaflet-extras.github.io/leaflet-providers/preview/index.html> sind alle verfügbaren Tilelayer wählbar

        - Beispiele für weltweit verfügbare Tilelayer

            ```javascript
            L.tileLayer.provider('OpenStreetMap.Mapnik');
            L.tileLayer.provider('OpenTopoMap');
            L.tileLayer.provider('Stamen.TonerLite');
            L.tileLayer.provider('Stamen.Watercolor');
            L.tileLayer.provider('Esri.WorldStreetMap');
            L.tileLayer.provider('Esri.WorldTopoMap');
            L.tileLayer.provider('Esri.WorldImagery');
            L.tileLayer.provider('CartoDB.Positron');
            L.tileLayer.provider('CyclOSM');
            ```

        - basemap.at Tilelayer für Österreich

            ```javascript
            L.tileLayer.provider('BasemapAT.basemap');
            L.tileLayer.provider('BasemapAT.grau');
            L.tileLayer.provider('BasemapAT.highdpi');
            L.tileLayer.provider('BasemapAT.terrain');
            L.tileLayer.provider('BasemapAT.surface');
            L.tileLayer.provider('BasemapAT.orthofoto');
            L.tileLayer.provider('BasemapAT.overlay');
            ```

## Ergebnis

[Leaflet Provider Plugin für Hintergrundlayer Beispiel](https://webmapping.github.io/cookbook/plugin_leaflet_provider_example.html) ([Source](https://github.com/webmapping/cookbook/blob/main/plugin_leaflet_provider_example.html))

___
[Inhaltsverzeichnis](https://webmapping.github.io/cookbook/index)
