# BBDD Copa del Rey
-[Ejercicios de Nivel 1 Moodle](#ejercicios-nivel-1)

## Ejercicios Nivel 1
1.Quins són els noms dels diferents llocs de naixement que tenim la BD que comencin per la lletra 'B'. Ordena-les per ordre alfabètic.
```sql
SELECT DISTINCT(lloc_naixement)
	FROM jugadors
WHERE LEFT(lloc_naixement, 1) = 'B'
ORDER BY lloc_naixement;
```
2.Volem el nom complet d’algun jugador que tingui el cognom més llarg. Cal considerar el cognom com l'string fins el càracter ','
```sql
SELECT nom_complet
	FROM jugadors
ORDER BY CHAR_LENGTH(SUBSTRING_INDEX(nom_complet,',',1)) DESC
LIMIT 1;
```
