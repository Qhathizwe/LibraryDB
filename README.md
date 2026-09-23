# LibraryDB
<img src="https://socialify.git.ci/Qhathizwe/LibraryDB/image?language=1&owner=1&name=1&stargazers=1&theme=Light" alt="LibraryDB" width="640" height="320" />

# Opening and Using pgAdmin 4 application
# Step 1:
-Open pgAdmin4 Launch the application: Open the pgAdmin 4 application from your operating system's application menu or desktop shortcut.

-Enter the Master Password: If prompted,enter your pgAdmin master password to unlock the application dashboard.

-Initiate server creation: Locate the Browser panel on the left side of the screen. Right-click on Servers, hover over Create, and select Server.

-Initiate database creation: Right-click on Databases, hover over Create, and select Database.

-Name your database: In the General tab of the new window, enter your preferred database name (LibraryDB) in the Database field.

-Save to finalize: Leave the other settings as default and click the Save button. Your new database will now be listed under the "Databases" dropdown and is ready for use.

-Right click on you database(LibraryDB) to open Query tool or (Alt + Shift + Q) shortcut to open Query tool.

# Step 2:
# -Creating your tables 

## Creating Authors Table 
```sql
CREATE TABLE IF NOT EXISTS authors(
id SERIAL PRIMARY KEY, 
name VARCHAR(100) NOT NULL,
nationality VARCHAR NOT NULL,
birth_year SMALLINT NOT NULL,
death_year SMALLINT 
)
```
## Creating books table 
```sql
CREATE TABLE IF NOT EXISTS books(
 id SERIAL PRIMARY KEY,
 title VARCHAR(255) NOT NULL,
 authorID INT REFERENCES authors(id) NOT NULL,
 genres TEXT[] NOT NULL,
 published_year INT NOT NULL,
 is_available BOOLEAN 
)
```
## Creating Patrons table
```sql
CREATE TABLE IF NOT EXISTS patrons(
id SERIAL PRIMARY KEY,
name VARCHAR(150) NOT NULL,
email VARCHAR(150) NOT NULL,
borrowed_books INT[]
)
```

## Inserting authors data into the table
```sql
INSERT INTO authors ( name, nationality, birth_year, death_year) 
VALUES
( 'George Orwell', 'British', 1903, 1950),

( 'Harper Lee', 'American', 1926, 2016),

( 'F. Scott Fitzgerald', 'American', 1896, 1940),

( 'Aldous Huxley', 'British', 1894, 1963),

( 'J.D. Salinger', 'American', 1919, 2010),

( 'Herman Melville', 'American', 1819, 1891),

( 'Jane Austen', 'British', 1775, 1817),

( 'Leo Tolstoy', 'Russian', 1828, 1910),

( 'Fyodor Dostoevsky', 'Russian', 1821, 1881),

( 'J.R.R. Tolkien', 'British', 1892, 1973);
```

### Inserting books into the books table
```sql
INSERT INTO books (title, authorID, genres, published_year, is_available)
VALUES 
( '1984', 1, ARRAY['Dystopian', 'Political Fiction'], 1949, TRUE),

( 'To Kill a Mockingbird', 2, ARRAY['Southern Gothic', 'Bildungsroman'], 1960, TRUE),

( 'The Great Gatsby', 3, ARRAY['Tragedy'], 1925, TRUE),

( 'Brave New World', 4, ARRAY['Dystopian', 'Science Fiction'], 1932, TRUE),

( 'The Catcher in the Rye', 5, ARRAY['Realist Novel', 'Bildungsroman'], 1951, TRUE),

( 'Moby-Dick', 6, ARRAY['Adventure Fiction'], 1851, TRUE),

( 'Pride and Prejudice', 7, ARRAY['Romantic Novel'], 1813, TRUE),

( 'War and Peace', 8, ARRAY['Historical Novel'], 1869, TRUE),

( 'Crime and Punishment', 9, ARRAY['Philosophical Novel'], 1866, TRUE),

( 'The Hobbit', 10, ARRAY['Fantasy'], 1937, TRUE);
```

## INSERTING DATA INTO THE PATRONS TABLE
```sql
INSERT INTO patrons (name, email, borrowed_books) 
VALUES
( 'Alice Johnson', 'alice@example.com', ARRAY[]::INT[]),

( 'Bob Smith', 'bob@example.com', ARRAY[1, 2]),

( 'Carol White', 'carol@example.com', ARRAY[]::INT[]),

( 'David Brown', 'david@example.com', ARRAY[3]),

( 'Eve Davis', 'eve@example.com', ARRAY[]::INT[]),

( 'Frank Moore', 'frank@example.com', ARRAY[4, 5]),

( 'Grace Miller', 'grace@example.com', ARRAY[]::INT[]),

( 'Hank Wilson', 'hank@example.com', ARRAY[6]),

( 'Ivy Taylor', 'ivy@example.com', ARRAY[]::INT[]),

( 'Jack Anderson', 'jack@example.com', ARRAY[7, 8]);
```
## Get all books
```sql
-- SELECT * FROM books
```
## Get a book by title
```sql
-- SELECT * FROM books 
-- WHERE title = 'War and Peace'
```
## Get all books by a specific author.
```sql
-- SELECT * FROM books 
-- WHERE authorID = 2
```
## Get all available books
```sql
-- SELECT * FROM books
-- WHERE is_available = TRUE
```

## Mark a book as borrowed (set available = false)
```sql
-- UPDATE books
-- SET is_available = FALSE
-- WHERE id = 1
```

## Add a new genre to an existing book.
```sql
-- UPDATE books 
-- set genres[2] = 'Comedy'
-- WHERE id = 10
```

## Add a borrowed book to a patron’s record.
```sql

-- UPDATE patrons
-- SET borrowed_books[1] = 7
-- WHERE id = 1
```

## Delete a book by title.
```sql
-- DELETE FROM books
-- WHERE title = '1984'
```

## Delete an author by ID.
```sql
-- DELETE FROM authors 
-- WHERE id = 1
```


## Find books published after 1950.
```sql
-- SELECT * FROM books
-- WHERE published_year > 1950
```

## Find all American authors.
```sql
-- SELECT * FROM authors 
-- WHERE nationality = 'America'
```

## Set all books as available.
```sql
-- UPDATE books
-- SET is_available = TRUE
```

## Find all books that are available AND published after 1950.
```sql
-- SELECT * FROM books
-- WHERE is_available = TRUE AND  published_year > 1950
```

## Find all American authors.
```sql
-- SELECT * FROM authors 
-- WHERE nationality = 'America'
```

## Set all books as available.
```sql
-- UPDATE books
-- SET is_available = TRUE
```

## Find all books that are available AND published after 1950.
```sql
-- SELECT * FROM books
-- WHERE is_available = TRUE AND  published_year > 1950
```

## Find authors whose names contain "George".
```sql
-- SELECT name FROM authors
-- WHERE name LIKE '%Herman%'
```

## Increment the published year 1869 by 1.
```sql
-- UPDATE books
-- SET published_year = published_year + 1
-- WHERE id = 8
```





