# SQL-скрипт шаблон для добавления данных в БД

1. Добавляем новый сезон

```
INSERT INTO Seasons (start_season, end_season) VALUES (
	'{startSeason}',
	'{endSeason}'
);
```

2. Добавляем новое время и дату игры:

```
INSERT INTO Dates (season_id, date_of_game) VALUES (
	(SELECT id_season FROM Seasons WHERE ‘{dateOfGame}' BETWEEN start_season AND end_season),
	'{dateOfGames}'
);
```

3. Добавляем новую команду:

```
INSERT INTO Teams (team_name) VALUES ('{teamName}');
```

4. Добавляем новых игроков:

```
INSERT INTO Players (first_name, middle_name, last_name, current_team) VALUES (
	'{firstName}',
	'{middleName}',
	'{lastName}',
	(SELECT id_team FROM Teams WHERE team_name = '{currentTeam}')
);
```

5. Перевод игрока в другую команду:

```
UPDATE Players
	SET current_team = (SELECT id_team FROM Teams WHERE team_name = ‘{newTeam}’)
	WHERE first_name = ’{firstName}’ AND middle_name = '{middleName}' AND last_name = '{lastName}'
;
```

6. Добавляем количество шайб игрока за игру:

```
UPDATE Scores
	SET score='{newScore}'
	WHERE date_of_game='{dateOfGame}'
	AND team_id=(SELECT id_team FROM Teams WHERE team_name='{team}')
	AND player_id=(SELECT id_player FROM players
		WHERE first_name='{firstName}'
		AND middle_name='{middleName}'
		AND last_name='{lastName}'
	)
;
```

**Примечание:** ‘{newScore}', ‘{dateOfGame}, ‘{team}', '{newTeam}', '{currentTeam}', ‘{firstName}, '{lastName}’, '{middleName}’, '{startSeason}', '{endSeason}' - входные данные, подробнее об этом в спецификации.
