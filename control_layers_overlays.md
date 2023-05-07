# Layer Control für Overlays

## Zutaten

- das Resultat vom Rezept ["Layer Control für Hintergrundlayer der basemap.at"](https://webmapping.github.io/cookbook/control_layers_baselayers)

## Ablauf

1. Initialisieren des Overlays

    - die gewünschten Overlay Layer vor der Layercontrol als `L.featureGroup` in einem Objekt `overlays` initialisieren

        ```javascript
        let overlays = {
            innsbruck: L.featureGroup(),
            weitere: L.featureGroup()
        };
        ```

        | siehe Dokumentation [L.featureGroup()](https://leafletjs.com/reference.html#featuregroup)

2. Einbau des Overlays in der Layercontrol

    - als zweites Argument von `L.control.layers` können Overlays mit Labeln für die Checkboxen zum Ein-/Ausschalten eingebaut werden

        ```javascript
        L.control.layers({
            // alle Hintergrundlayer
        } , {
            "Innsbruck Marker": overlays.innsbruck.addTo(map),
            "Weitere Marker (noch leer)": overlays.weitere
        }).addTo(map);
        ```

        | Hinweis: `overlays.innsbruck.addTo(map)` bewirkt, dass dieses Overlay beim Laden auch direkt angezeigt wird. Es können so beliebig viele Overlays direkt angezeigt werden

        | siehe Dokumentation [L.control.layers()](https://leafletjs.com/reference.html#control-layers) und [.addTo()](https://leafletjs.com/reference.html#featuregroup-addto)

3. den Innsbruck Marker in das passende Overlay schieben

    - statt in die Karte `map` wird der Innsbruck Marker in das Overlay `overlays.innsbruck` geschrieben

        ```javascript
        let marker = L.marker([47.267222, 11.392778]).addTo(overlays.innsbruck);
        ```

## Ergebnis

[Layer Control für Overlays](https://webmapping.github.io/cookbook/control_layers_overlays_example.html)

___
[Inhaltsverzeichnis](https://webmapping.github.io/cookbook/index)
