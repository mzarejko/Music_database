# Music_database

## Konfiguracja programu
  - postgres 13.1
  
  
  ## Dokumentacja
  
  ### Cel
  
  Zarzadzanie muzyką
  
  
  ### Encje
  
- User – Tabela zawierająca informacje o użytkowniku, w tym:
	- adres email
	- wiek	
	- kraj zamieszkania 
	- nazwę użytkownika
	- hasło
		
- Follow – Tabela zawierająca informacje o tym, który użytkownik obserwuje którego na podstawie numerów id, zawiera:
	- id użytkownika obserwującego
	- id użytkownika obserowanego
		
- Playlista – Tabela zawierająca informacje o playlistach, w tym:
	- ich numery id
	- nazwy
	- datę utworzenia
	- id autora playlisty
		
- Album – Tabela zawierająca informacje o albumach muzycznych, w tym:
	- id albumu
	- nazwę albumu
	- datę wydania
	- id producenta
	- id playlisty
		
- Producer – Tabela zawierająca informacje o producentach:
	- id producenta
	- nazwę producenta
	- gatunek
	- datę
		
- Iterested – Tabela zawierająca informację o wydarzeniach, którymi zainteresowani są użytkownicy:
	- id użytkownika
	- id eventu
		
- Events – Tabela zawierająca informację o wydarzeniach:
	- id wydarzenia
	- datę wydarzenia
	- lokalizację wydarzenia
	- id artysty występującego w evencie
	- nazwa wydarzenia
	


![alt text](../main/127189281_400856931109321_7668519763450585592_n.png?raw=true)


### Komendy testowe
```SQL

1.
SELECT music.music_id, music.music_URL, score.score FROM music NATURAL JOIN score;

2.
SELECT music.music_id, music.music_URL, genre.genre FROM music NATURAL JOIN genre;

3.
SELECT music_id, music_URL, awards, FROM music;

4.
SELECT artist.firstname, artist.lastname, events.title FROM artist NATURAL JOIN events;

5.
SELECT user.user_id, user.username, score.score, music.music_id, music.music_URL FROM 
((user INNER JOIN score ON user.user_id = score.user_id)
INNER JOIN music ON music.music_id = score.music_id);
```
