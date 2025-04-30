# Bedienungsanleitung für Verbel

## Wie erstellt man ein neues Projekt

Wenn du dieses Projekt von GitHub forkt und ein neues Vercel-Projekt in Vercel erstellen möchtest, um es erneut zu deployen, befolge bitte die folgenden Schritte.

![vercel-create-1](./images/vercel/vercel-create-1.jpg)

1. Gehe zur Startseite der Vercel-Konsole;  
2. Klicke auf „Neu hinzufügen“;  
3. Wähle „Projekt“ aus.

![vercel-create-2](./images/vercel/vercel-create-2.jpg)

1. Suche unter „Import Git Repository“ nach chatgpt-next-web;  
2. Wähle das Projekt deiner neuen Fork aus und klicke auf „Importieren“.

![vercel-create-3](./images/vercel/vercel-create-3.jpg)

1. Klicke auf der Projektkonfigurationsseite auf „Umgebungsvariablen“, um die Variablen einzurichten;  
2. Füge die Umgebungsvariablen OPENAI_API_KEY und CODE hinzu;  
3. Trage die entsprechenden Werte für die Variablen ein;  
4. Klicke auf „Hinzufügen“, um die Variablen zu bestätigen;  
5. Stelle sicher, dass OPENAI_API_KEY hinzugefügt wurde, sonst funktioniert es nicht;  
6. Klicke auf „Bereitstellen“, erstelle das Projekt und warte geduldig ca. 5 Minuten, bis die Bereitstellung abgeschlossen ist.

## Wie man eine eigene Domain hinzufügt

\[TODO]

## Wie man Umgebungsvariablen ändert

![vercel-env-edit](./images/vercel/vercel-env-edit.jpg)

1. Gehe in der Projektkonsole von Vercel auf „Einstellungen“ oben rechts;  
2. Klicke links auf „Umgebungsvariablen“;  
3. Klicke rechts neben einem bestehenden Eintrag auf den Button;  
4. Wähle „Bearbeiten“, ändere die Werte und speichere.

⚠️ Hinweis: Nach jeder Änderung der Umgebungsvariablen musst du das Projekt [neu bereitstellen](#wie-man-neu-bereitstellt), damit die Änderungen wirksam werden!

## Wie man neu bereitstellt

![vercel-redeploy](./images/vercel/vercel-redeploy.jpg)

1. Gehe in der Projektkonsole von Vercel auf „Deployments“ oben;  
2. Klicke rechts neben dem obersten Eintrag auf den Button;  
3. Klicke auf „Neu bereitstellen“, um das Projekt neu zu deployen.
