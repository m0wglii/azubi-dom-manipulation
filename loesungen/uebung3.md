# Lösung – Übung 3 (Elemente erstellen & löschen)

<details>
  <summary>🔒 Lösung anzeigen</summary>

```js
// TODO: Selektiere #list, #addBtn und #removeBtn
const list = document.getElementById("list");
const addBtn = document.getElementById("addBtn");
const removeBtn = document.getElementById("removeBtn");

// BONUS: Zähler für fortlaufende Nummern
let count = 0;

// Hilfsfunktionen für Platzhalter-Hinweis
function showEmptyHint() {
    if (list.children.length === 0) {
        count = 0;
        const li = document.createElement("li");
        li.innerText = "Keine Einträge";
        li.classList.add("empty-hint");
        list.appendChild(li);
    }
}

function removeEmptyHint() {
    const hint = list.querySelector(".empty-hint");
    if (hint) {
        list.removeChild(hint);
    }
}

// Initial: Liste leer → Hinweis anzeigen
showEmptyHint();

// TODO: Klicke auf "addBtn" → neues <li> mit Text "Neues Item" zur Liste hinzufügen
// Tipp: document.createElement("li"), innerText, appendChild
addBtn.addEventListener("click", () => {
    removeEmptyHint();
    count++;
    const li = document.createElement("li");
    li.innerText = `Item ${count}`; // BONUS: fortlaufende Nummer
    list.appendChild(li);
});
// BONUS++ Lösung: In Zeile 20, die <ul> (unordered List) in eine <ol> (ordered List) switchen.  
// TODO: Klicke auf "removeBtn" → letztes <li> entfernen (falls vorhanden)
// Tipp: list.lastElementChild prüfen und removeChild nutzen
removeBtn.addEventListener("click", () => {
    const last = list.lastElementChild;
    if (last && !last.classList.contains("empty-hint")) {
        list.removeChild(last);
    }
    if (list.children.length === 0) {
        showEmptyHint(); // BONUS: Platzhalter-Text, wenn Liste leer
    }
});
```

</details>

---

## Erklärung

- `createElement`/`appendChild` erzeugen und hängen neue Listeneinträge an.
- `lastElementChild` + `removeChild` entfernen den letzten Eintrag sicher.
- Der **Platzhalter „Keine Einträge“** verhindert ein „leeres“ UI und trainiert einfache Zustandslogik.
- Die **orderedList** Component in HTML gibt den Listeneinträgen automatisch Nummern. Somit ist <br> eine JavaScript Logik, hierfür gar nicht nötig.