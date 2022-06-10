# MovieQueries
- Create a Movies Database with a table similar to the excel screenshot above
- INSERT INTO movietable VALUES
    -> ('Lavalantula', 83, 'Horror', 4.7, 'TV-14'),
    -> ('Starship Troopers', 129, 'Sci-Fi', 7.2, 'PG-13'),
    -> ('Waltz With Bashir', 90, 'Documentary', 8.0, 'R'),
    -> ('Spaceballs', 96, 'Comedy', 7.1, 'PG'),
    ->  ('Monsters Inc.', 92, 'Animation', 8.1, 'G');

- Add a few more movies of your choosing.
- INSERT INTO movietable VALUES
    -> ('Avatar', 162, 'Sci-Fi', 7.8, 'PG-13'),
    -> ('Avengers: Endgame', 181, 'Action', 8.4, 'PG-13');

- Create a query to find all movies in the Sci-Fi genre.
- SELECT * FROM movietable WHERE Genre = 'Sci-Fi';

- Create a query to find all films that scored at least a 6.5 on IMDB
- SELECT * FROM movietable WHERE IMDBScore >= 6.5;

- For parents who have young kids, but who don't want to sit through long children's movies, create a query to find all of the movies rated G or PG that are less than 100 minutes long.
- SELECT * FROM movietable WHERE Runtime<100 AND Rating = 'PG' OR Rating ='G';

- Create a query to show the average runtimes of movies rated below a 7.5, grouped by their respective genres.
- SELECT AVG(Runtime), Rating FROM movietable WHERE IMDBScore<7.5 GROUP BY Rating;

- There's been a data entry mistake; Starship Troopers is actually rated R, not PG-13. Create a query that finds the movie by its title and changes its rating to R.
-  UPDATE movietable SET Rating = 'R' WHERE Title = 'Starship Troopers';

- Show the ID number and rating of all of the Horror and Documentary movies in the database. Do this in only one query.
- ALTER TABLE `movietable` ADD COLUMN `id` INT AUTO_INCREMENT UNIQUE FIRST;
- SELECT id, Rating FROM movietable WHERE Genre = 'Horror' OR Genre ='Documentary';

- This time let's find the average, maximum, and minimum IMDB score for movies of each rating.
SELECT Rating, AVG(IMDBScore), MAX(IMDBScore), MIN(IMDBScore) FROM movietable GROUP BY Rating;

- That last query isn't very informative for ratings that only have 1 entry. use a HAVING COUNT(*) > 1 clause to only show ratings with multiple movies showing.
- SELECT Rating, AVG(IMDBScore), MAX(IMDBScore), MIN(IMDBScore) FROM movietable GROUP BY Rating HAVING COUNT(*) > 1;
- 
- Let's make our movie list more child-friendly. Delete all entries that have a rating of R.
-  DELETE FROM movietable WHERE Rating = 'R';
