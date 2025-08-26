# Lösung – Übung 5 (Mini-Projekt: Dashboard)

<details>
  <summary>🔒 Lösung anzeigen</summary>

```js
// TODO: Selektiere #grid sowie die Buttons #addCardBtn, #removeCardBtn, #colorAllBtn, #resetBtn
const grid = document.getElementById("grid");
const addCardBtn = document.getElementById("addCardBtn");
const removeCardBtn = document.getElementById("removeCardBtn");
const colorAllBtn = document.getElementById("colorAllBtn");
const resetBtn = document.getElementById("resetBtn");

// BONUS: Zähle die erstellten Karten und nummeriere den Titel ("Karte 1", "Karte 2", ...)
let count = 0;

// (Hilfsfunktion) Button-Zustand aktualisieren: Löschen deaktivieren, wenn keine Karten existieren
function updateRemoveState() {
    removeCardBtn.disabled = grid.children.length === 0;
}

// (Hilfsfunktion) Eine neue Karte erstellen (nur DOM-Manipulation, kein Inline-Style)
function createCard(titleText, bodyText) {
    const card = document.createElement("div");
    card.classList.add("card");

    const title = document.createElement("div");
    title.classList.add("card-title");
    title.innerText = titleText;

    const text = document.createElement("div");
    text.classList.add("card-text");
    text.innerText = bodyText;

    card.appendChild(title);
    card.appendChild(text);
    return card;
}

// TODO: Klick auf "Karte hinzufügen":
// - Erzeuge ein <div class="card"> mit Unterelementen (z. B. Titel + Text)
// - Hänge es an #grid an (appendChild)
addCardBtn.addEventListener("click", () => {
    count++;
    const card = createCard(`Karte ${count}`, "Dies ist eine dynamisch erzeugte Karte.");
    grid.appendChild(card);
    updateRemoveState();
});

// TODO: Klick auf "Letzte Karte löschen":
// - Entferne das letzte Kindelement von #grid, falls vorhanden
removeCardBtn.addEventListener("click", () => {
    const last = grid.lastElementChild;
    if (last) {
        grid.removeChild(last);
    }
    updateRemoveState();
});

// TODO: Klick auf "Alle einfärben":
// - Füge allen .card-Elementen die Klasse "colored" hinzu
colorAllBtn.addEventListener("click", () => {
    const cards = grid.querySelectorAll(".card");
    cards.forEach(c => c.classList.add("colored"));
});

// TODO: Klick auf "Zurücksetzen":
// - Entferne die Klasse "colored" wieder von allen .card-Elementen
resetBtn.addEventListener("click", () => {
    const cards = grid.querySelectorAll(".card");
    cards.forEach(c => c.classList.remove("colored"));
});

// Initialer Zustand
updateRemoveState();
```

</details>

---

## Erklärung

- **Erstellen/Löschen:** `createElement`/`appendChild`/`removeChild` bauen das Grid dynamisch auf bzw. räumen es auf.
- **Zustandsklassen:** Einfärben erfolgt nur über die CSS-Klasse `.colored` (keine Inline-Styles).
- **UX-Detail:** Der Löschen-Button wird deaktiviert, wenn keine Karten vorhanden sind.
