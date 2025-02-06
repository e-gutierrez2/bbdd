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