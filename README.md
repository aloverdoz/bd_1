CREATE TABLE IF NOT EXISTS Genre (
	id SERIAL PRIMARY KEY,
	genre_name VARCHAR(80) NOT NULL
);

CREATE TABLE IF NOT EXISTS Actor (
	id SERIAL PRIMARY KEY,
	name VARCHAR(80) NOT NULL,
	age INT NOT null,
	birthday DATE
);

CREATE TABLE IF noT EXISTS Genre_Actor (
	id SERIAL PRIMARY KEY,
	actor_id INT NOT NULL REFERENCES Actor(id),
	genre_id INT NOT NULL REFERENCES Genre(id)
);

CREATE TABLE IF NOT EXISTS Albom (
	id SERIAL PRIMARY KEY,
	name VARCHAR(80) NOT null,
	age INT NOT null
);

CREATE TABLE IF NOT EXISTS Track (
	id SERIAL PRIMARY KEY,
	name VARCHAR(80) NOT null,
	time_line INT NOT null,
	id_albom SERIAL,
	FOREIGN key (id_albom) REFERENCES Albom(id)
);

CREATE TABLE IF NOT EXISTS Actor_Albom (
	id SERIAL PRIMARY KEY,
	actor_id INT NOT NULL REFERENCES Actor(id),
	albom_id INT NOT NULL REFERENCES Albom(id)
);

CREATE TABLE IF NOT EXISTS Play_list (
	id SERIAL PRIMARY KEY,
	name VARCHAR(80) NOT NULL,
	age INT NOT NULL
);

CREATE TABLE IF NOT EXISTS Play_list_Track (
	id SERIAL PRIMARY KEY,
	track_id INT NOT NULL REFERENCES Track(id),
	play_list_id INT NOT NULL REFERENCES Play_list(id)
);

insert into actor (name, age, birthday)
values ('Михаил Круг', 40, '1962-04-01'),
	('Владимир Путин', 70, '1952-10-17'),
	('Миша H1gh', 29, '1993-01-26'),
	('Zivert', 32, '1990-11-28');

insert into genre (genre_name)
values ('Шансонн'),
	('Патриотичная'),
	('Rap'),
	('Pop');

insert into albom (name, age)
values ('Жиган-лимон', 1994),
	('Военные', 1991),
	('Человек', 2022),
	('Сияй', 2021),
	('Совместный', 2024);

insert into track (name, time_line, id_albom)
values ('А сечку жрите сами', 146, 1),
	('Девочка — пай', 256, 1),
	('Жиган-лимон', 172, 1),
	('Гимн России', 212, 2),
	('Заря', 168, 2),
	('Прощание славянки', 466, 2),
	('Возьмите мою листовку', 114, 3),
	('Что-то на богатом', 140, 3),
	('Сегодня ты никто, завтра мир у ног', 130, 3),
	('Зелёные волны', 261, 4),
	('Сияй', 204, 4),
	('Мой океан', 204, 4),
	('Ещё хочу', 215, 4),
	('Скрещивание', 118, 5);

insert into play_list (name, age)
values ('Воспоминания с зоны', 2019),
	('Для армии', 2020),
	('Для души', 2022),
	('Для бега', 2021),
	('Разное', 2018);

insert into actor_albom (actor_id, albom_id)
values (1, 1),
	(1, 5),
	(2, 2),
	(2, 5),
	(3, 3),
	(3, 5),
	(4, 4),
	(4, 5);

insert into genre_actor (actor_id, genre_id)
values (1, 1),
	(2, 2),
	(3, 3),
	(4, 4);

insert into play_list_track (track_id, play_list_id)
values (1, 1),
	(2, 1),
	(3, 1),
	(4, 2),
	(5, 2),
	(6, 2),
	(7, 3),
	(8, 3),
	(9, 3),
	(10, 4),
	(11, 4),
	(12, 4),
	(13, 4),
	(14, 5);
