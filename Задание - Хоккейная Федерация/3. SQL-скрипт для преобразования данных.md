# SQL-скрипт для преобразования данных

### SQL-скрипт для представления, чтобы в последствии извлекать из него следующие запросы:

- Лучший бомбардир;
- Количество игр игрока за сезон.

```
CREATE VIEW view_players AS (
	SELECT start_season, end_season, id_player AS id, first_name, middle_name, last_name, SUM(score) AS score, COUNT(Scores.date_id) AS Games
	FROM Players
	LEFT JOIN Scores
	ON Players.id_player = Scores.player_id 
	LEFT JOIN dates
	ON Scores.date_id = Dates.id_date 
	GROUP BY start_season, id
);
```
