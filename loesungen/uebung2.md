# Lösung – Übung 2 (Eventlistener Basics)

<details>
  <summary>🔒 Lösung anzeigen</summary>

```js
// TODO: Selektiere den Button #clickBtn und das Absatz-Element #output
const button = document.getElementById("clickBtn");
const output = document.getElementById("output");

// TODO: Füge dem Button einen Klick-Eventlistener hinzu
// - Bei Klick soll im Absatz "Button wurde geklickt!" stehen
// - Außerdem soll der Button eine CSS-Klasse "clicked" erhalten
let count = 0;

button.addEventListener("click", () => {
    count++;
    output.innerText = `Button wurde ${count}-mal geklickt!`;
    button.classList.toggle("clicked");
});
```

</details>

---

## Erklärung

- `getElementById` selektiert Button und Ausgabefeld.
- `addEventListener("click", ...)` registriert die Reaktion auf Klicks.
- `count` wird hochgezählt, damit die Azubis die Wiederholbarkeit sehen.
- `classList.toggle("clicked")` schaltet die Klasse bei jedem Klick um (ein/aus).
