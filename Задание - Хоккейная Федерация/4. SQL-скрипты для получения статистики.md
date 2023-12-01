# SQL-скрипты для получения статистики

### 1. Счёт команды в определённой игре

```
SELECT SUM(score) AS result FROM Scores
	WHERE date_of_game='{dateOfGame}'
	AND team_name='{team}'
;
```

### 2. Количество игр игрока за сезон

```
SELECT Games AS result FROM view_players
	WHERE start_season='{startSeason}'
	AND end_season='{endSeason}'
	AND first_name=’{firstName}’
	AND middle_name=’{middleName}’
	AND last_name=’{lastName}’
;
```

### 3. Лучший бомбардир сезона

```
SELECT CONCAT(first_name, last_name) AS reault FROM view_players
	WHERE score = (SELECT MAX(score) FROM view_players WHERE start_season=’{startSeason}’ AND end_season=’{endSeason}’)
	AND start_season=’{startSeason}’
	AND end_season=’{endSeason}’
;
```

Примечание: ‘{dateOfGame}, ‘{team}', ‘{firstName}, '{lastName}’, '{middleName}’, '{startSeason}', '{endSeason}' - входные данные, подробнее об этом в спецификации. view_players - это представление, которое подробно расписано в третьем SQL-скрипте.
