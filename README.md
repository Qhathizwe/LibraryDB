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

--Creating Authors Table 

CREATE TABLE IF NOT EXISTS authors(
id SERIAL PRIMARY KEY, 
name VARCHAR(100) NOT NULL,
nationality VARCHAR NOT NULL,
birth_year SMALLINT NOT NULL,
death_year SMALLINT 
)

-- Creating books table 
CREATE TABLE IF NOT EXISTS books(
 id SERIAL PRIMARY KEY,
 title VARCHAR(255) NOT NULL,
 authorID INT REFERENCES authors(id) NOT NULL,
 genres INT[] NOT NULL,
 published_year INT NOT NULL,
 is_available BOOLEAN DEFAULT TRUE
)

--Creating Patrons table

CREATE TABLE IF NOT EXISTS patrons(
id SERIAL PRIMARY KEY,
name VARCHAR(150) NOT NULL,
email VARCHAR(150) NOT NULL,
borrowed_books INT[]
)

