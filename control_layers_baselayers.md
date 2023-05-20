# Layer Control für Hintergrundlayer der basemap.at

## Zutaten

- das Resultat vom Rezept [Leaflet Provider Plugin für Hintergrundlayer](https://webmapping.github.io/cookbook/plugin_leaflet_provider) ([siehe Source](https://github.com/webmapping/cookbook/blob/main/examples/plugin_leaflet_provider.html))
- WMTS Hintergrundlayer der <https://basemap.at> über das Leaflet Provider Plugin

## Ablauf

1. Einbau der Hintergrundlayer

    - den bestehenden `L.tileLayer.provider` Aufruf durch einen Aufruf von `L.control.layers` mit sieben `L.tileLayer.provider` Aufrufen für die <https://basemap.at> ersetzen

        ```javascript
        L.control.layers({
            "BasemapAT Grau": L.tileLayer.provider("BasemapAT.grau").addTo(map),
            "BasemapAT Standard": L.tileLayer.provider("BasemapAT.basemap"),
            "BasemapAT High-DPI": L.tileLayer.provider("BasemapAT.highdpi"),
            "BasemapAT Gelände": L.tileLayer.provider("BasemapAT.terrain"),
            "BasemapAT Oberfläche": L.tileLayer.provider("BasemapAT.surface"),
            "BasemapAT Orthofoto": L.tileLayer.provider("BasemapAT.orthofoto"),
            "BasemapAT Beschriftung": L.tileLayer.provider("BasemapAT.overlay")
        }).addTo(map);
        ```

        > siehe Dokumentation [L.control.layers()](https://leafletjs.com/reference.html#control-layers)

2. Kombination des Orthofotos mit der Beschriftung

    - die beiden Tilelayer für das Orthofoto und die Beschriftung können mit einer `L.layerGroup` übereinandergelegt werden

        ```javascript
            "BasemapAT Orthofoto mit Beschriftung": L.layerGroup([
                L.tileLayer.provider("BasemapAT.orthofoto"),
                L.tileLayer.provider("BasemapAT.overlay")
            ])
        ```

        > siehe Dokumentation [L.layerGroup()](https://leafletjs.com/reference.html#layergroup)

## Ergebnis

[Layer Control für Hintergrundlayer der basemap.at Beispiel](https://webmapping.github.io/cookbook/examples/control_layers_baselayers.html) ([Source](https://github.com/webmapping/cookbook/blob/main/examples/control_layers_baselayers.html))

___
[Inhaltsverzeichnis](https://webmapping.github.io/cookbook/index)
