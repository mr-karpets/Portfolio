# SQL-скрипт создания таблиц в БД

```
CREATE TABLE Seasons (
	id_season SERIAL,
	start_season DATE NOT NULL,
	end_season DATE NOT NULL,
	PRIMARY KEY(id_season)
);
CREATE TABLE Dates (
	id_date SERIAL,
	date_of_game TIMESTAMP NOT NULL,
	season_id INT,
	PRIMARY KEY (id_date),
	FOREIGN KEY (season_id) REFERENCES Seasons (id_season)
	ON DELETE RESTRICT ON UPDATE CASCADE
);
CREATE TABLE Teams (
	id_team SERIAL,
	team_name CHAR(50) NOT NULL,
	PRIMARY KEY(id_team)
);
CREATE TABLE Players (
	id_player SERIAL,
	first_name CHAR(50) NOT NULL,
	middle_name CHAR(50),
	last_name CHAR(50) NOT NULL,
	team_id INT,
	PRIMARY KEY (id_player),
	FOREIGN KEY (team_id) REFERENCES Teams (id_team)
	ON DELETE RESTRICT ON UPDATE CASCADE
);
CREATE TABLE Scores (
	id_score SERIAL,
	date_id INT,
	player_id INT,
	team_id INT,
	score INT NOT NULL DEFAULT 0,
	PRIMARY KEY (id_score),
	FOREIGN KEY (date_id) REFERENCES Dates (id_date)
	ON DELETE RESTRICT ON UPDATE CASCADE,
	FOREIGN KEY (player_id) REFERENCES Players (id_player)
	ON DELETE RESTRICT ON UPDATE CASCADE,
	FOREIGN KEY (team_id) REFERENCES Teams (id_team)
	ON DELETE RESTRICT ON UPDATE CASCADE
);
```
