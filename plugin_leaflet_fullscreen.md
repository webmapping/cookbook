# Leaflet.fullscreen Plugin

## Zutaten

- das Resultat vom Rezept [Leaflet Provider Plugin für Hintergrundlayer](https://webmapping.github.io/cookbook/plugin_leaflet_provider) ([siehe Source](https://github.com/webmapping/cookbook/blob/main/examples/plugin_leaflet_provider.html))
- das Leaflet.fullscreen Plugin unter <https://github.com/Leaflet/Leaflet.fullscreen>

## Ablauf

1. das Plugin einbinden

    - auf der Plugin Seite unter [Including via CDN](https://github.com/Leaflet/Leaflet.fullscreen#including-via-cdn) finden wir die Links zu den Plugin Dateien

    - Einbau in `index.html` über "*Copy / Paste"*

        ```html
        <!-- Leaflet.fullscreen -->
        <script src='https://api.mapbox.com/mapbox.js/plugins/leaflet-fullscreen/v1.0.1/Leaflet.fullscreen.min.js'></script>
        <link href='https://api.mapbox.com/mapbox.js/plugins/leaflet-fullscreen/v1.0.1/leaflet.fullscreen.css' rel='stylesheet' />
        ```

2. Einbau im SCRIPT Element

    - es gibt mehrere Möglichkeiten, das Plugin zu initialisieren, eine davon ist direkt beim Initialisieren der Karte

        ```javascript
        let map = L.map("map", {
            fullscreenControl: true
        });
        ```

        > siehe Dokumentation [Leaflet.fullscreen Usage](https://github.com/Leaflet/Leaflet.fullscreen#usage)

## Ergebnis

[Leaflet.fullscreen Plugin Beispiel](https://webmapping.github.io/cookbook/examples/plugin_leaflet_fullscreen.html) ([Source](https://github.com/webmapping/cookbook/blob/main/examples/plugin_leaflet_fullscreen.html))

___
[Inhaltsverzeichnis](https://webmapping.github.io/cookbook/index)
