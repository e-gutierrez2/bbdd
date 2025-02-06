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
3.Mostra el nom de les diferents competicions per ordre de celebració  (de més antigues a més noves)
```sql
SELECT nom
	FROM competicions
ORDER BY data_inici;
```
4. Quin/s són els noms complerts dels jugadors que tenim el seu pes entrat a la BD. Ordena el resultat per el seu nom complet de forma ascendent.
```sql
SELECT nom_complet
	FROM jugadors
WHERE pes IS NOT NULL
ORDER BY nom_complet ASC;
```
5.Quin/s són els noms complerts dels jugadors que no tenim el seu pes entrat a la BD. Ordena el resultat per el seu nom complet de forma ascendent
```sql
SELECT nom_complet
	FROM jugadors
WHERE pes IS NULL
ORDER BY nom_complet ASC;
```
6.Si sabem que l'extensió d'un domini són les últimes dos o tres lletres després del caràcter punt '.' situades al final de la URL d'un lloc web o d'un email. Per exemple '.com', '.net', '.cat', '.org', '.es',....
Quins clubs no utilitzen la mateixa extensió de domini per l'email que per la seva web?
```sql
SELECT nom, email, web
	FROM clubs
WHERE REGEXP_SUBSTR(email,'[.][a-z]{2,3}$') <> REGEXP_SUBSTR(web,'[.][a-z]{2,3}$')
ORDER BY club_id;
```
7.Digues el nom complet d'un dels jugadors que tenen el cognom més llarg.
```sql
SELECT nom_complet
	FROM jugadors
ORDER BY CHAR_LENGTH(SUBSTRING_INDEX(nom_complet,',',1)) DESC
LIMIT 1;
```
8.Quina és la quanitat de partits que es van disputar l'any 2019?
```sql
SELECT COUNT(YEAR(data_hora)) AS quantitat
	FROM partits
WHERE YEAR(data_hora) = '2019';
```
9.En bàsquet els partits no poden acabar en empat i els volem detectar. Digues quins partits (mostrant només el partit_id) han acabat en empat.
Ordena el resultat per partit_id
```sql

```

