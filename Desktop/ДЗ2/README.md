## Схема базы данных SQL 

![](https://github.com/Redhead80/SQL2/blob/22fc4a35a253cbf928d7a99acaacd399d6a9a848/database_diagram.png) 

## Код SQL для создания базы данных

```sql
CREATE TABLE IF NOT EXISTS Genres (
	genre_id SERIAL PRIMARY KEY,
	gengre_name VARCHAR(40) NOT NULL
	);

CREATE TABLE IF NOT EXISTS Singers (
	singer_id SERIAL PRIMARY KEY,
	singer_name VARCHAR(40) NOT NULL
	);

CREATE TABLE IF NOT EXISTS SingersGenres (
	singer_id INTEGER REFERENCES Singers(singer_id),
	genre_id INTEGER REFERENCES Genres(genre_id),
	CONSTRAINT pk_sg PRIMARY KEY (genre_id, singer_id)
);

CREATE TABLE IF NOT EXISTS Albums (
	album_id SERIAL PRIMARY KEY,
	album_name VARCHAR(40) NOT NULL,
	album_year_of_issue DATE NOT NULL
	);

CREATE TABLE IF NOT EXISTS SingersAlbums (
	singer_id INTEGER REFERENCES Singers(singer_id),
	album_id INTEGER REFERENCES Albums(album_id),
	CONSTRAINT pk_sa PRIMARY KEY (album_id, singer_id)
);

CREATE TABLE IF NOT EXISTS Songs (
	song_id SERIAL PRIMARY KEY,
	song_name VARCHAR(40) NOT NULL,
	song_duration INTERVAL NOT NULL,
	album INTEGER NOT NULL REFERENCES Albums(album_id)
	);

CREATE TABLE IF NOT EXISTS Collections (
	collection_id SERIAL PRIMARY KEY,
	collection_name VARCHAR(40) NOT NULL,
	collection_year DATE NOT NULL
	);

CREATE TABLE IF NOT EXISTS CollectionsSongs (
	song_id INTEGER REFERENCES Songs(song_id),
	collection_id INTEGER REFERENCES Collections(collection_id),
	CONSTRAINT pk_cs PRIMARY KEY (collection_id, song_id)
);


```
