These are some tips and tricks, I've seen or read before enrollment. All examples are either from the resource utilized or from WGU screenshots.

### D427 Data Management - Applications 4CUs

I watched a YouTube video about this course, and the presenter shared some valuable advice. The key takeaways include following the instructions precisely and ensuring correct capitalization in the SQL query section. However, based on his demonstration in ZyBooks, it appears that case sensitivity doesn't matter. Therefore, I suggest using all capital letters for <span style="color: #5075A1;">clauses</span>, <span style="color: #5075A1;">keywords</span>, <span style="color: #49A08A;">data types</span>, and <span style="color: #5075A1;">operators</span> ( :capital_abcd: ), and for the <span style="color: #F6A270;">names</span> of <span style="color: #F6A270;">columns</span> and <span style="color: #F6A270;">tables</span>, employing camelcase or title case for each word. For instance:<br>

### <span style="color: #D28000;">Creating tables</span>

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
        CREATE TABLE <span style="color: #F6A270;">M</span>ember (
            <span style="color: #F6A270;">ID</span> <span style="color: #49A08A;">INT</span> UNSIGNED,
            <span style="color: #F6A270;">F</span>irst<span style="color: #F6A270;">N</span>ame <span style="color: #49A08A;">VARCHAR(100)</span>,
            <span style="color: #F6A270;">M</span>iddle<span style="color: #F6A270;">I</span>nitital <span style="color: #49A08A;">CHAR(1)</span>,
            <span style="color: #F6A270;">L</span>ast<span style="color: #F6A270;">N</span>ame <span style="color: #49A08A;">VARCHAR(100)</span>,
            <span style="color: #F6A270;">D</span>ate<span style="color: #F6A270;">O</span>f<span style="color: #F6A270;">B</span>irth <span style="color: #49A08A;">DATE</span>,
            <span style="color: #F6A270;">A</span>nnual<span style="color: #F6A270;">P</span>ledge <span style="color: #49A08A;">DECIMAL(8,2)</span> UNSIGNED
        );
    </code>
</pre>
> :thought_balloon: There are eight digits in total, including six 9s and the two necessary decimal places.
<br>

Add a way to test or check your code before submitting with `DESCRIBE`
<pre>
    <code>
        <span style="color: #7C7F82;">CREATE TABLE Member (
            ID INT UNSIGNED,
            FirstName VARCHAR(100),
            MiddleInitital CHAR(1),
            LastName VARCHAR(100),
            DateOfBirth DATE,
            AnnualPledge DECIMAL(8,2) UNSIGNED
        );</span>

        DESCRIBE <span style="color: #5075A1;">TABLE</span> <span style="color: #F6A270;">M</span>ember;
    </code>
</pre>
<br>
<br>
<hr>

### <span style="color: #D28000;">Inserting values</span>

You can insert values or records into a table, like this:

The following data needs to be added to the __Movie__ table:
> |Title               | Genre   | RatingCode | Year |
> |--------------------|---------|------------|------|
> |Pride and Prejudice | Romance | G          | 2005 |
> <br>

<pre>
    <code>
        <span style="color: #5075A1;">INSERT</span> INTO Movie (
            Title,
            Genre,
            RatingCode,
            Year
        )
        VALUES (
            <span style="color: #FFC6A5;">'Pride and Prejudice'</span>,
            <span style="color: #FFC6A5;">'Romance'</span>,
            <span style="color: #FFC6A5;">'G'</span>,
            <span style="color: #FFC6A5;">'2005'</span>
        );
    </code>
</pre>
<br>

You can check if you inserted the values successfully with the `SELECT` statement.

<pre>
    <code>
        <span style="color: #7C7F82;">INSERT INTO Movie (
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
        );</span>

        <span style="color: #5075A1;">SELECT</span> * FROM <span style="color: #F6A270;">M</span>ovie;
    </code>
</pre>
<br>
<br>
<hr>

### <span style="color: #D28000;">Foreign keys</span>

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
        <span style="color: #7C7F82;">CREATE TABLE Movie (
            Title VARCHAR(30),
            RatingCode VARCHAR(5),</span>
            <span style="color: #5075A1;">FOREIGN KEY</span> (<span style="color: #F6A270;">R</span>ating<span style="color: #F6A270;">C</span>ode) <span style="color: #5075A1;"><strong>REFERENCES</strong></span> Rating(<span style="color: #F6A270;">R</span>ating<span style="color: #F6A270;">C</span>ode)
        <span style="color: #7C7F82;">);</span>

        DESCRIBE <span style="color: #5075A1;">TABLE</span> Movie;
    </code>
</pre>
> :spiral_notepad: Remeber to remove the check staement before submitting