# Discord.js Bot mit SQLite-Datenbank

![Bot Banner](https://media.discordapp.net/attachments/558723762191859712/1134796345543237715/Mitoru-Bot.js.png?width=705&height=352)

Willkommen zu meinem Discord.js-Bot! Dieser Bot wurde mit Discord.js und einer SQLite-Datenbank entwickelt und bietet eine Vielzahl von Funktionen für deinen Server.

## Funktionen

- **Ticket-System:** Erstelle und verwalte Tickets für Benutzeranfragen.
- **Level-System:** Belohne Benutzer mit XP für Aktivität und weise ihnen Rollen basierend auf ihrem Level zu.
- **JoinToCreate-System:** Ermöglicht Benutzern das Erstellen temporärer Sprachkanäle bei Betreten des Servers.
- **Log-System:** Protokolliere wichtige Ereignisse und Moderationsaktionen für eine bessere Übersicht.
- **Moderationsbefehle:** Verwalte deinen Server mit Befehlen zum Kicken, Bannen und Stummschalten von Benutzern.
- **und mehr:** Es gibt noch viele weitere Funktionen, die du entdecken kannst!

## Installation

1. Klone das Repository:

```bash
git clone https://github.com/dein-benutzername/dein-bot-repo.git
```

2. Gehe in das Projektverzeichnis:
```bash   
cd dein-bot-repo
```

3. Installiere die Abhängigkeiten:
```bash
npm install
```

4. Konfiguration:
```bash
{
  "token": "DEIN_DISCORD_BOT_TOKEN",
  "prefix": "!",
  "dbPath": "./data/database.sqlite"
}
```

## Mitwirken
Ich freue mich über Beiträge und Verbesserungsvorschläge! Wenn du einen Fehler gefunden hast oder eine neue Funktion hinzufügen möchtest, kannst du gerne einen Pull Request erstellen oder ein Issue öffnen.

## Lizenz
Dieses Projekt ist unter der MIT-Lizenz lizenziert. Weitere Informationen findest du in der Lizenzdatei.
services:
  db:
    image: mysql:latest
    environment:
      MYSQL_ROOT_PASSWORD: root
      MYSQL_DATABASE: blog
      MYSQL_USER: user
      MYSQL_PASSWORD: password
    volumes:
      - ./mysql_data:/var/lib/mysql
    ports:
      - "3306:3306"

  phpmyadmin:
    image: phpmyadmin/phpmyadmin:latest
    depends_on:
      - db
    environment:
      PMA_HOST: db
      MYSQL_ROOT_PASSWORD: root
    ports:
      - "8080:80"

  php:
    image: php:8.2-cli
    volumes:
      - ./src:/var/www/html
    depends_on:
      - db
    working_dir: /var/www/html
    command: php -S 0.0.0.0:8000 -t public
    ports:
      - "8000:8000"
    networks:
      - default







