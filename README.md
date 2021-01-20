# Music_database

## Konfiguracja programu
  - postgres 13.1
  - pgcrypto
  
  
  ## Dokumentacja
  
  ### Cel
  
  Zarzadzanie muzyką
  
  
  ### Encje
  
- User – Tabela zawierająca informacje o użytkowniku, w tym:
	
		
- Follow – Tabela zawierająca informacje o tym, który użytkownik obserwuje którego na podstawie numerów id, zawiera:
	
		
- Playlista – Tabela zawierająca informacje o playlistach, w tym:

		
- Album – Tabela zawierająca informacje o albumach muzycznych, w tym:
	
		
- Producer – Tabela zawierająca informacje o producentach:
	
		
- Iterested – Tabela zawierająca informację o wydarzeniach, którymi zainteresowani są użytkownicy:
	
		
- Events – Tabela zawierająca informację o wydarzeniach:
	
	

|  User            |  Follow     		    |  Playlista        |  Album       | Producer          |  Iterested     |  Events              	     |
|------------------|--------------------------------|-------------------|--------------|-------------------|----------------|---------------------------------|
| adres email      | id użytkownika obserwującego   | numery id         | id albumu    | id producenta     | id użytkownika | id wydarzenia    		     |
|	 wiek      |  id użytkownika obserowanego   |  nazwy            | nazwę albumu |  nazwę producenta |   id eventu    | datę wydarzenia  		 |
|  kraj zamieszkania|  				    |  datę utworzenia  | datę wydania | gatunek	   |   		   | lokalizację wydarzenia  	   |
| nazwę użytkownika|   				    | id autora         |id producenta  | datę             |                | id artysty występującego w evencie|
| hasło 	|   		  	  	    |  playlisty         | id playlisty |                  |                |         				 |
|  	   |  		   			    |                    | 	        |                  |                |					|


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
