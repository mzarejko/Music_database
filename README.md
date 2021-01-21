# Music_database

## Konfiguracja bazy danych
  - postgres 13.1
  -  pgcrypto 
  
  
  ## Dokumentacja
  
  ### Cel
  
  Przygotowanie rozbudowanej bazy danych pod aplikację z muzyką. 
  
  
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


### Zapytania testowe
```SQL

SELECT artist.firstname, artist.lastname, events.title FROM artist NATURAL JOIN events;
--wyswietla na jaki artysta bedzie na jakim koncercie

SELECT name FROM ALBUM ORDER BY name;
--wyswietla i sortuje wszystkie albumy

SELECT * FROM events WHERE event_id IN (SELECT event_id FROM interested WHERE user_id=1);
--wyswietla eventy, ktorymi interesuje sie user 1

SELECT username, country FROM user_account WHERE user_id IN (SELECT user_id FROM interested WHERE event_id=1);
--wyswietla z jakiego kraju pochodza zainteresowani eventem 1

SELECT * FROM user_account WHERE country = 'Poland';
--wyswietla userow z Polski

SELECT music.music_id, music.music_URL, score.score FROM music NATURAL JOIN score;
--wyswietla id utworu, url oraz punkty utworu

SELECT * FROM user_account WHERE password = crypt('passwd', password);
--wyswietla 

SELECT music.music_id, music.music_URL, genre.genre FROM music NATURAL JOIN genre;
--wyswietla id utworu, url oraz gatunek utworu

SELECT * FROM playlist JOIN user_account ON playlist.user_id = user_account.user_id;
--wyswietla polaczenie playlisty i usera, ktore playlisty kto obserwuje

SELECT music_id, music_URL, awards FROM music;
--wyswietla jaki utwor ma jakie nagrody

SELECT follower_id FROM follow JOIN user_account ON follow.user_id = user_account.user_id WHERE user_account.user_id = 5;
--wyswietla id followerow, ktorzy obserwuja usera o id 5

SELECT * FROM playlist where playlist.name = 'techno';
--wyswietla dane na temat playlisty "techno"

SELECT * FROM user_account WHERE user_account.age > 20;
--wyswietla dane userow, ktorzy maja wiecej niz 20 lat

SELECT user_account.user_id, user_account.username, score.score, music.music_id, music.music_URL FROM 
((user_account INNER JOIN score ON user_account.user_id = score.user_id)INNER JOIN music ON music.music_id = score.user_id);
--wyswietla jaki user jaka ocene dal jakiemu utworowi

```
