These are some tips and tricks, I've seen or read before enrollment. All examples are either from the resource utilized or from WGU screenshots.

### D427 Data Management - Applications 4CUs

I watched a YouTube video about this course, and the presenter shared some valuable advice. The key takeaways include following the instructions precisely and ensuring correct capitalization in the SQL query section. However, based on his demonstration in ZyBooks, it appears that case sensitivity doesn't matter. Therefore, I suggest using all capital letters for <ins>clauses</ins>, <ins>keywords</ins>, <ins>data types</ins>, and <ins>operators</ins> ( :capital_abcd: ), and for the names of columns and tables, employing camelcase or title case for each word. For instance:<br>

### <p style="color:#FF975A">Creating tables</p>

The __Member__ table will have the following columns:<br>

* __ID__ - positive integer
* __FirstName__ -  variable lenght string, up to 100 characters
* __MiddleInitial__ - fixed length string, 1 character
* __LastName__ - variable string, up to 100 characters
* __DateOfBirth__ - date
* __AnnualPledge__ - positive decimal representing a cost of up to *$999,999,* with 2 digits for cents.<br>

Write a SQL statement to create the __Member__ table.<br>

Do not add any additional constraints to any column beyond what is selected.
<pre>
    <code>
        CREATE TABLE Member (
            ID INT UNSIGNED,
            FirstName VARCHAR(100),
            MiddleInitital CHAR(1),
            LastName VARCHAR(100),
            DateOfBirth DATE,
            AnnualPledge DECIMAL(8,2) UNSIGNED
        );
    </code>
</pre>
> :thought_balloon: There are eight digits in total, including six 9s and the two necessary decimal places.
<br>

Add a way to test or check your code before submitting with `DESCRIBE`
<pre>
    <code>
        CREATE TABLE Member (
            ID INT UNSIGNED,
            FirstName VARCHAR(100),
            MiddleInitital CHAR(1),
            LastName VARCHAR(100),
            DateOfBirth DATE,
            AnnualPledge DECIMAL(8,2) UNSIGNED
        );

        DESCRIBE TABLE Member;
    </code>
</pre>
<br>
<br>
<hr>

### Inserting values

You can insert values or records into a table, like this:

The following data needs to be added to the __Movie__ table:
> |Title               | Genre   | RatingCode | Year |
> |--------------------|---------|------------|------|
> |Pride and Prejudice | Romance | G          | 2005 |
> <br>

<pre>
    <code>
        INSERT INTO Movie (
            Title,
            Genre,
            RatingCode,
            Year
        )
        VALUES (
            'Pride and Prejudice',
            'Romance',
            'G',
            '2005'
        );
    </code>
</pre>
<br>

You can check if you inserted the values successfully with the `SELECT` statement.

<pre>
    <code>
        INSERT INTO Movie (
            Title,
            Genre,
            RatingCode,
            Year
        )
        VALUES (
            'Pride and Prejudice',
            'Romance',
            'G',
            '2005'
        );

        SELECT * FROM Movie;
    </code>
</pre>
<br>
<br>
<hr>

### Foreign keys

Referencing a created table column to different table's coulmn. For example:

__Rating__ table:<br>
* __RatingCode__ - variable length string, primary key <br>
* __RatingDescription__ - variable length string

__Movie__ table:<br>
* __Title__ - variable length string, maximum 30 characters<br> 
* __RatingCode__ - variable length string, maximum 5 characters

Write a SQL statement to create the Movie table. Designating the RatingCode col in the Movie table as a foreign key to the RatingCode col in the Rating table.
<pre>
    <code>
        CREATE TABLE Movie (
            Title VARCHAR(30),
            RatingCode VARCHAR(5),
            FOREIGN KEY (RatingCode) <strong>REFERENCES</strong> Rating(RatingCode)
        );

        DESCRIBE TABLE Movie;
    </code>
</pre>
> :spiral_notepad: Remeber to remove the check staement before submitting