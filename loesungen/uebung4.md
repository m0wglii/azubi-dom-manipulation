# Lösung – Übung 4 (Mehrfachauswahl & Manipulation)

<details>
  <summary>🔒 Lösung anzeigen</summary>

```js
// TODO: Selektiere alle <p>-Elemente des Containers .paragraphs
// Tipp: document.querySelectorAll(".paragraphs p")
const paragraphs = document.querySelectorAll(".paragraphs p");

// TODO: Selektiere die Buttons #colorAllBtn, #altColorBtn, #resetBtn
const colorAllBtn = document.getElementById("colorAllBtn");
const altColorBtn = document.getElementById("altColorBtn");
const resetBtn = document.getElementById("resetBtn");

// BONUS: Hilfsfunktion clearColors(paragraphs), die "blue" und "red" überall entfernt
function clearColors(nodes) {
    nodes.forEach(p => p.classList.remove("blue", "red"));
}

// TODO: "Alle blau färben":
// - Entferne zuvor evtl. vorhandene Farb-Klassen von allen Absätzen
// - Füge allen Absätzen die Klasse "blue" hinzu
colorAllBtn.addEventListener("click", () => {
    clearColors(paragraphs);
    paragraphs.forEach(p => p.classList.add("blue"));
});

// TODO: "Jeden zweiten rot färben":
// - Entferne zuvor evtl. vorhandene Farb-Klassen von allen Absätzen
// - Füge bei geradem Index (2., 4., ...) die Klasse "red" hinzu
altColorBtn.addEventListener("click", () => {
    clearColors(paragraphs);
    paragraphs.forEach((p, index) => {
        if ((index % 2) === 1) {
            p.classList.add("red");
        }
    });
});

// TODO: "Zurücksetzen":
// - Entferne Farb-Klassen von allen Absätzen
resetBtn.addEventListener("click", () => {
    clearColors(paragraphs);
});

// BONUS (optional):
// - Lasse beim Klick auf einen Absatz dessen Farbe togglen (classList.toggle("blue"))
paragraphs.forEach(p => p.addEventListener("click", () => p.classList.toggle("blue")));
```

</details>

---

## Erklärung

- `querySelectorAll` liefert eine NodeList, die wir per `forEach` iterieren.
- Farbsetzung geschieht **nur** über Klassen (`.blue`, `.red`) – kein Inline-Style.
- `clearColors` räumt vor jeder Aktion auf → eindeutiger Zustand.
- Der „jeden zweiten“-Effekt nutzt den **Index** (beginnend bei 0).
