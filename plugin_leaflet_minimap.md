# Leaflet.MiniMap Plugin

## Zutaten

- das Resultat vom Rezept [Leaflet Provider Plugin für Hintergrundlayer](https://webmapping.github.io/cookbook/plugin_leaflet_provider) ([siehe Source](https://github.com/webmapping/cookbook/blob/main/examples/plugin_leaflet_provider.html))
- das Leaflet.MiniMap Plugin unter <https://github.com/Norkart/Leaflet-MiniMap>

## Ablauf

1. das Plugin einbinden

    - Suche bei <https://cdnjs.com> nach *"leaflet-minimap"* liefert <https://cdnjs.com/libraries/leaflet-minimap>

    - Einbau in `index.html` über "*Copy Script Tag"* (\</>) Icon beim Suchergebnis. **Anmerkung**: *toggle.png* und *toggle.svg* wird nicht benötigt.

        ```html
        <!-- Leaflet.MiniMap -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet-minimap/3.6.1/Control.MiniMap.min.js" integrity="sha512-WL3nAJlWFKoDShduxQRyY3wkBnQsINXdIfWIW48ZaPgYz1wYNnxIwFMMgigzSgjNBC2WWZ8Y8/sSyUU6abuF0g==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet-minimap/3.6.1/Control.MiniMap.min.css" integrity="sha512-qm+jY0iQ4Xf5RL79UB75REDLYD0jtvxxVZp2RVIW8sm8RNiHdeN43oksqUPrBIshJtQcVPrAL08ML2Db8fFZiA==" crossorigin="anonymous" referrerpolicy="no-referrer" />
        ```

2. Einbau im SCRIPT Element

    - der Stamen Hintergrundlayer der Karte ist zur Demonstration der MiniMap nicht wirklich geeignet - wir ersetzen ihn deshalb zuerst mit einem Layer der <https://basemap.at>

        ```javascript
        L.tileLayer.provider('BasemapAT.basemap').addTo(map);
        ```

    - für die MiniMap muss ein weiterer, vom Kartenhintergrund unabhängiger (!), Hintergrundlayer definiert werden. Nachdem in unserem Beispiel auch das Leaflet Provider Plugin verfügbar ist, kann die Initialisierung des Plugins einfacher erfolgen als auf der Plugin Seite unter [Using the MiniMap control](https://github.com/Norkart/Leaflet-MiniMap#using-the-minimap-control) beschrieben. Statt dem TileLayer in `osm2` verwenden wir einen neuen Leaflet Provider TileLayer. Über die Option `toggleDisplay` ermöglichen wir das Ein- und Ausklappen der MiniMap.

        ```javascript
        let miniMap = new L.Control.MiniMap(
            L.tileLayer.provider("BasemapAT.basemap"), {
                toggleDisplay: true
            }
        ).addTo(map);
        ```

        > siehe Dokumentation [Using the MiniMap control](https://github.com/Norkart/Leaflet-MiniMap#using-the-minimap-control)

## Ergebnis

[Leaflet.MiniMap Plugin Beispiel](https://webmapping.github.io/cookbook/examples/plugin_leaflet_minimap.html) ([Source](https://github.com/webmapping/cookbook/blob/main/examples/plugin_leaflet_minimap.html))

___
[Inhaltsverzeichnis](https://webmapping.github.io/cookbook/index)
