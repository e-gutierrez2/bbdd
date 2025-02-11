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
SELECT partit_id
	FROM partits
WHERE equip_local_punts = equip_visitant_punts AND partit_id IS NOT NULL
ORDER BY partit_id;
```
10.Quin és el nom complert i l'IMC(Índex de Massa Corporal)  dels jugadors amb identificadors 101 i 135 si sabem que:  
- IMC (Relació pes/alçada) = Es calcula dividint el pes (Kg) pel quadrat de l'alçada (m) => pes/alçada.  
- Quan no existeixi alguna de les dues variables, aquesta ha de prendre el valor 70 Kg pel que fa al pes i 1m amb 90cm pel que fa a l'alçada.  
- Arrodoneix el resultat a 2 decimals.
```sql
SELECT nom_complet, ROUND(IFNULL(pes,70) / (IFNULL(alcada,1.9) * IFNULL(alcada,1.9)) , 2) AS IMC
	FROM jugadors
WHERE jugador_id = 101 OR jugador_id = 135;
```
11.Digues quants jugadors tenen tres vocals seguides en el seu nom complet.
```sql
SELECT COUNT(*) AS quants
	FROM jugadors
WHERE nom_complet REGEXP '[aeiouAEIOU]{3}';
```
12.Quins són els clubs que utilitzen el domini '.cat' a la seva web?  
- Mostra el nom del club, i la seva web  
- Ordena el resultat per club_id  
```sql
SELECT nom, web
	FROM clubs
WHERE REGEXP_LIKE(web,'.cat$');
```
13.Quin/s són els noms complerts dels jugadors que no tenim compte de twitter entrat a la BD. Ordena el resultat per el seu nom complet de forma ascendent
```sql
SELECT nom_complet
	FROM jugadors
WHERE twitter IS NULL OR ''
ORDER BY nom_complet ASC;
```
14.Quina és la quanitat de partits que es van disputar l'any 2017?
```
SELECT COUNT(YEAR(data_hora)) AS quantitat
	FROM partits
WHERE YEAR(TRIM(data_hora)) = '2017';
```
15.Diques quins partits han acabat amb una diferència de punts superior a 10.  
- Mostra el partit_id, la diferència de punts.  
- Ordena el resultat per la diferència de punts de major a menor
```sql
SELECT partit_id , ABS(CAST(equip_local_punts AS SIGNED) - CAST(equip_visitant_punts AS SIGNED)) AS diferencia
	FROM partits
WHERE  ABS(CAST(equip_local_punts AS SIGNED) - CAST(equip_visitant_punts AS SIGNED)) > 10
ORDER BY diferencia DESC;
```
16.Quants jugadors han nascut al mes de desembre
```sql
SELECT COUNT(MONTH(data_naixement)) AS qt_desembre
	FROM jugadors
WHERE MONTH(data_naixement) = 12;
```
17.Quin/s són els noms dels clubs que no tenim la seva web entrada a la BD? Ordena el resultat per el seu nom de forma ascendent.
```sql
SELECT nom
	FROM clubs
WHERE web IS NULL OR '';
```
18.Quines són les ciutats que alguna vegada s'hi ha celebrat la competició de la Copa del Rei de Bàsquet?  
- Ordena el resultat per nom de ciutat.
```
SELECT ciutat
	FROM competicions
WHERE nom REGEXP 'Copa del Rei'
ORDER BY ciutat ASC;
```
19.Al llarg de les diferents competicions. Quants partits s'han jugat al mes de març?
```sql
SELECT COUNT(*) AS quantitat
	FROM partits
WHERE MONTH(data_hora) = 3;
```
20.Digues el nom complet d'un dels jugadors que tenen el cognom més llarg.
```sql
SELECT nom_complet
	FROM jugadors
ORDER BY CHAR_LENGTH(SUBSTRING_INDEX(nom_complet,',',1)) DESC
LIMIT 1;
```
