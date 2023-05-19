# Leaflet-hash Plugin implementieren

## Zutaten

- das Resultat vom Rezept [Leaflet Provider Plugin für Hintergrundlayer verwenden](https://webmapping.github.io/cookbook/plugin_leaflet_provider) ([siehe Source](https://github.com/webmapping/cookbook/blob/main/plugin_leaflet_provider_example.html))
- das Leaflet-hash Plugin unter <https://github.com/mlevans/leaflet-hash>

## Ablauf

1. das Plugin einbinden

    - Suche bei <https://cdnjs.com> nach *"leaflet-hash"* liefert <https://cdnjs.com/libraries/leaflet-hash>

    - Einbau in `index.html` über "*Copy Script Tag"* (\</>) Icon beim Suchergebnis

        ```html
        <!-- Leaflet-hash -->
        <script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet-hash/0.2.1/leaflet-hash.min.js" integrity="sha512-0A4MbfuZq5Au9EdpI1S5rUTXlibNBi8CuZ/X3ycwXyZiCjNzpiO9YH6EMqPgzZm6vfNCuZStBQHjnO17nIC0IQ==" crossorigin="anonymous" referrerpolicy="no-referrer"></script>
        ```

2. Einbau im SCRIPT Element

    - ganz am Ende des Scripts wird Leaflet-hash mit einem einzigen Aufruf initialisiert. Wir verwenden `let` statt `var`....

        ```javascript
        let hash = new L.Hash(map);
        ```

        > siehe Dokumentation [Leaflet-hash Getting started](https://github.com/mlevans/leaflet-hash#getting-started)

3. Im Hashtag der URL können wir Zoomlevel, Latitude und Longitude direkt ablesen (z.B. `#13/47.2672/11.3928`). Die Werte werden bei Zoom/Pan entsprechend angepasst und erlauben damit das Boorkmarken von Ausschnitten.

## Ergebnis

[Leaflet-hash Plugin implementieren](https://webmapping.github.io/cookbook/plugin_leaflet_hash_example.html) ([Source](https://github.com/webmapping/cookbook/blob/main/plugin_leaflet_hash_example.html))

___
[Inhaltsverzeichnis](https://webmapping.github.io/cookbook/index)
