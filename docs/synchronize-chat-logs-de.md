# Synchronisation der Chat-Logs mit UpStash

## Voraussetzungen

- GitHub-Konto  
- Eigener ChatGPT-Next-Web Server  
- [UpStash](https://upstash.com)

## Erste Schritte

1. Registriere dich für ein UpStash-Konto.  
2. Erstelle eine Datenbank.

    ![Registrieren und Anmelden](./images/upstash-1.png)

    ![Datenbank erstellen](./images/upstash-2.png)

    ![Server auswählen](./images/upstash-3.png)

3. Finde die REST-API und kopiere die Werte für UPSTASH_REDIS_REST_URL und UPSTASH_REDIS_REST_TOKEN (⚠Wichtig⚠: Teile den Token nicht!)

   ![Kopieren](./images/upstash-4.png)

4. Füge UPSTASH_REDIS_REST_URL und UPSTASH_REDIS_REST_TOKEN in die Synchronisations-Konfiguration ein und klicke dann auf **Verfügbarkeit prüfen**.

    ![Synchronisation 1](./images/upstash-5.png)

    Wenn alles in Ordnung ist, hast du diesen Schritt erfolgreich abgeschlossen.

    ![Verfügbarkeit der Synchronisation bestätigt](./images/upstash-6.png)

5. Erfolg!

   ![Gut gemacht~!](./images/upstash-7.png)
