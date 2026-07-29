# diagrams — UML model views (activity, sequence, component)

Editable sources for the three diagrams featured in the
[Model diagrams](../index.html#diagrams) section of the website. Each diagram is provided in two
identical formats:

| Diagram | Source (draw.io) | Source (XML) | Rendered PNG |
|---|---|---|---|
| Activity (control flow of one run) | `model_activity.drawio` | `model_activity.xml` | `../assets/model_activity.png` |
| Sequence (one monthly coupling cycle) | `model_sequence.drawio` | `model_sequence.xml` | `../assets/model_sequence.png` |
| Component (static code structure) | `model_component.drawio` | `model_component.xml` | `../assets/model_component.png` |

The `.drawio` and `.xml` files have identical content; both open in
[diagrams.net](https://app.diagrams.net) (File > Open) or the draw.io desktop app.

## Re-render the PNGs

The PNGs were produced headlessly with the draw.io desktop CLI (scale 2):

```powershell
$drawio = "C:\Program Files\draw.io\draw.io.exe"
foreach ($n in "model_activity","model_sequence","model_component") {
  & $drawio --no-sandbox -x -f png -s 2 -o "..\assets\$n.png" "$n.drawio"
}
```

## Layer color key (shared with the model figures)

- Blue `#dae8fc` — ABM (patient) layer
- Green `#d5e8d4` — network (support) layer
- Orange `#ffe6cc` — system-dynamics (services) layer

Each cross-layer message in the sequence diagram is one of the six switchable
interfaces (SW_AS, SW_SA, SW_AN, SW_NA, SW_SN, SW_NS), matching
`../../model/coupling_mvp/coupling_switches.m`.
