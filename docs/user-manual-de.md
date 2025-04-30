# Benutzerhandbuch (User Manual)

Mit ChatGpt übersetzt und keine grammatikalische Fehler festgestellt.

Dieses Dokument erklärt einige Funktionen und Designprinzipien von NextChat.

## Maske (Mask)

### Was ist eine Maske? Worin unterscheidet sie sich von einem Prompt?

Eine Maske = mehrere vordefinierte Prompts + Modelleinstellungen + Gesprächseinstellungen.

Die vordefinierten Prompts (Contextual Prompts) werden im In-Context Learning verwendet, um ChatGPT dazu zu bringen, Ausgaben zu erzeugen, die besser den Anforderungen entsprechen. Sie können auch Systemrestriktionen oder begrenztes zusätzliches Wissen enthalten.

Die Modelleinstellungen legen fest, welches Modell standardmäßig für Gespräche mit dieser Maske genutzt wird.

Die Gesprächseinstellungen umfassen eine Reihe von Einstellungen, die das Gesprächserlebnis betreffen und weiter unten erklärt werden.

### Wie fügt man eine vordefinierte Maske hinzu?

Derzeit können vordefinierte Masken nur durch Editieren des Quellcodes hinzugefügt werden. Bitte bearbeite die entsprechende Sprachdatei im Verzeichnis [mask](../app/masks/).

Die Bearbeitung erfolgt so:

1. Konfiguriere eine Maske in NextChat.
2. Nutze die Download-Schaltfläche auf der Masken-Editierseite, um die Maske als JSON zu speichern.
3. Lass ChatGPT dir helfen, die JSON-Datei in entsprechenden TypeScript-Code umzuwandeln.
4. Füge den Code in die entsprechende `.ts`-Datei ein.

In Zukunft wird es möglich sein, Masken per Side-Loading zu laden.

---

## Gespräch (Chat)

### Bedeutung der Buttons oberhalb des Chatfensters

Im Standardmodus zeigt ein Mouseover auf die Buttons ihre Beschriftung an. Hier die Erklärung der Buttons:

- **Gesprächseinstellungen:** Einstellungen für das aktuelle Gespräch. Ihre Beziehung zu den globalen Einstellungen wird im nächsten Abschnitt erläutert.
- **Farbschema:** Klick wechselt zwischen Automatisch, Dunkel und Hell.
- **Schnellbefehle:** Vorgefertigte Prompts, die schnell eingefügt werden können; auch über Eingabe von `/` im Chat suchbar.
- **Alle Masken:** Öffnet die Masken-Seite. 
- **Chat löschen:** Fügt ein Lösch-Tag ein, so dass alle darüber liegenden Nachrichten nicht an GPT gesendet werden – entspricht einem Löschen des Chats. Erneutes Klicken hebt die Löschung wieder auf. 
- **Modelleinstellungen:** Ändert das Modell für das aktuelle Gespräch. Beachtet, dass nur das aktuelle Gespräch betroffen ist, nicht die globalen Standardeinstellungen.

---

### Beziehung zwischen Gesprächs- und globalen Einstellungen

Es gibt zwei Einstiegsstellen:

1. Links unten auf der Seite der Button für globale Einstellungen.
2. Über den Button oberhalb des Chatfensters für die Einstellungen des aktuellen Gesprächs.

Nach Erstellung eines neuen Gesprächs sind dessen Einstellungen standardmäßig mit den globalen Einstellungen synchronisiert. Ändert man die globalen Einstellungen, werden neue Gespräche entsprechend angepasst.

Wird das Gespräch manuell angepasst, trennt sich die Synchronisation. Änderungen an globalen Einstellungen wirken dann nicht mehr auf dieses Gespräch.

Die Synchronisation lässt sich über die Option „Gesprächseinstellungen -> Globale Einstellungen verwenden“ wiederherstellen.

---

### Bedeutung der Gesprächseinstellungen

Im Einstellungsmenü oberhalb des Chatfensters findest du von oben nach unten:

- Liste der vordefinierten Prompts: hinzufügen, löschen, sortieren.
- Avatar der Rolle.
- Rollenname.
- Vordefinierte Prompts ausblenden: Wenn aktiviert, erscheinen diese nicht im Chatfenster.
- Globale Einstellungen verwenden: ob das Gespräch die globalen Einstellungen nutzt.
- Modelleinstellungen: dieselben Optionen wie in den globalen Einstellungen.

---

### Bedeutung der globalen Einstellungen

- model / temperature / top_p / max_tokens / presence_penalty / frequency_penalty sind ChatGPT-Parameter. Details siehe OpenAI Dokumentation. 
- System-Level Prompt Injection und Nutzereingabe-Vorverarbeitung siehe: [GitHub Issue #2144](https://github.com/Yidadaa/ChatGPT-Next-Web/issues/2144);  
- Anzahl der mitgesendeten letzten Nachrichten: wie viele der letzten n Nachrichten bei jeder Eingabe mitgesendet werden.
- Schwelle für die Komprimierung der Verlaufsnachrichten: ab einer bestimmten Länge wird eine Zusammenfassung der Historie erzeugt. 
- Historienzusammenfassung aktivieren/deaktivieren.

---

### Was ist eine Historienzusammenfassung?

Die Funktion der Historienzusammenfassung (auch Verlaufs-Komprimierung genannt) ist entscheidend, um in langen Gesprächen den Kontext zu behalten und dabei Token zu sparen.

Beispiel: Das ChatGPT 3.5 Modell kann nur bis zu 4096 Tokens verarbeiten. Überschreitet der Verlauf diese Länge, tritt ein Fehler auf.

Um das zu umgehen, wird bei Überschreiten eines Schwellenwerts (z.B. 1000 Zeichen) eine Zusammenfassung der älteren Nachrichten erzeugt, die etwa 100 Zeichen umfasst.

So wird der Verlauf auf eine kleinere Token-Anzahl komprimiert, ohne den Kontext komplett zu verlieren.

---

### Wann sollte man die Historienzusammenfassung ausschalten?

Da die Zusammenfassung die Gesprächsqualität beeinflussen kann, sollte sie bei einmaligen Gesprächen wie Übersetzungen oder Informationsabfragen deaktiviert werden. Dann auch die Anzahl der mitgesendeten Verlaufsnachrichten auf 0 setzen.

---

### Welche Informationen werden beim Senden einer Nachricht übertragen?

Wenn du eine Nachricht absendest, werden folgende Teile an ChatGPT geschickt:

1. Systemlevel-Prompt: soll die Nutzungserfahrung ähnlich der offiziellen WebUI machen, kann in den Einstellungen deaktiviert werden.
2. Historienzusammenfassung: liefert langfristiges, aber ungenaues Kontextwissen.
3. Vordefinierte Prompts: für In-Context Learning oder Systemrestriktionen.
4. Die letzten n Nachrichten als kurzzeitiges Gedächtnis für präzisen Kontext.
5. Deine aktuelle Eingabe.
