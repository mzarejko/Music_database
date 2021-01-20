# Music_database

## Konfiguracja programu
  - postgres 13.1
  
  
  ## Dokumentacja
  
  ### Cel
  
  
  ### Encje
 - User – Tabela zawierająca informacje o użytkowniku, w tym:
		- adres email
		- wiek	
		- kraj zamieszkania 
		-nazwę użytkownika
		-hasło
-Follow – Tabela zawierająca informacje o tym, który użytkownik obserwuje którego na podstawie numerów id, zawiera:
		- id użytkownika obserwującego
		- id użytkownika obserowanego
- Playlista – Tabela zawierająca informacje o playlistach, w tym:
		- ich numery id
		- nazwy
		- datę utworzenia
		- id autora playlisty
Album – Tabela zawierająca informacje o albumach muzycznych, w tym:
		- id albumu
		- nazwę albumu
		-datę wydania
		-id producenta
		-id playlisty
Producer – Tabela zawierająca informacje o producentach:
		-id producenta
		-nazwę producenta
		-gatunek
		-datę
Iterested – Tabela zawierająca informację o wydarzeniach, którymi zainteresowani są użytkownicy:
		-id użytkownika
		-id eventu
Events – Tabela zawierająca informację o wydarzeniach:
		-id wydarzenia
		-datę wydarzenia
		-lokalizację wydarzenia
		-id artysty występującego w evencie
		-nazwa wydarzenia
