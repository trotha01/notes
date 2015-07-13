# Mysql Notes

This is just for self reference,
so I don't have to keep looking throughout the internet
for the infrequent times I use mysql directly.

http://www.tutorialspoint.com/mysql/mysql-data-types.htm

# Creating a Table
create table bar (
	id UNSIGNED INT NOT NULL AUTO_INCREMENT,,
	name VARCHAR(255),
	PRIMARY KEY (ID)
)

create table table_name (
	column_name TYPE,
	id UNSIGNED INT NOT NULL AUTO_INCREMENT,,
	foo UNSIGNED INT,
	PRIMARY KEY (id),
	FOREIGN KEY (foo) REFERENCES BAR(id)
);


# Data Types

## Numeric

TINYINT: -128 to 127

UNSIGNED TINYINT: 0 to 255

SMALLINT: -32768 to 32767

UNSIGNED SMALLINT: 0 to 65535

MEDIUMINT: -8388608 to 8388607

UNSIGNED MEDIUMINT: 0 to 16777215

INT: -2147483648 to 2147483647

UNSIGNED INT: 0 to 4294967295

BIGINT: -9223372036854775808 to 9223372036854775807

UNSIGNED BIGINT: 0 to 18446744073709551615

FLOAT(M,D):
- cannot be unsigned
- M: display length
- D: number of decimals
- default to 10,2. 2 is number of decimals, 10 is total number of digits, including decimals.
- max decimal precision = 24 places

DOUBLE(M,D):
- default to 16,4
- synonyms: REAL
- max decimal precision = 53 places

DECIMAL(M,D):
- default
- each decimal is one byte
- synonyms: NUMERIC

## Date and Time
DATE:
- A date in YYYY-MM-DD format
- Between 1000-01-01 and 9999-12-31.
- Example, December 30th, 1973 would be stored as 1973-12-30.

DATETIME:
- A date and time combination in YYYY-MM-DD HH:MM:SS format
- Between 1000-01-01 00:00:00 and 9999-12-31 23:59:59.
- Example, 3:30 in the afternoon on December 30th, 1973 would be stored as 1973-12-30 15:30:00.

TIMESTAMP:
- This looks like the previous DATETIME format, only without the hyphens between numbers
- A timestamp between midnight, January 1, 1970 and sometime in 2037.
- Example: 3:30 in the afternoon on December 30th, 1973 would be stored as 19731230153000 ( YYYYMMDDHHMMSS ).

TIME:
- Stores the time in HH:MM:SS format.

YEAR(M):
- Stores a year in 2-digit or 4-digit format.
- If the length is specified as 2 (for example YEAR(2)), YEAR can be 1970 to 2069 (70 to 69).
- If the length is specified as 4, YEAR can be 1901 to 2155. The default length is 4.

## String Types:

CHAR(M):
- A fixed-length string between 1 and 255 characters in length
- Example CHAR(5)
- right-padded with spaces to the specified length when stored.
- default is 1.

VARCHAR(M):
- A variable-length string between 1 and 255 characters in length
- Example VARCHAR(25).
- You must define a length when creating a VARCHAR field.

BLOB or TEXT:
- A field with a maximum length of 65535 characters.
- BLOBs are "Binary Large Objects" and are used to store large amounts of binary data, such as images or other types of files.
- Fields defined as TEXT also hold large amounts of data; the difference between the two is that sorts and comparisons on stored data are case sensitive on BLOBs and are not case sensitive in TEXT fields.
- You do not specify a length with BLOB or TEXT.

TINYBLOB or TINYTEXT:
- A BLOB or TEXT column with a maximum length of 255 characters.
- You do not specify a length with TINYBLOB or TINYTEXT.

MEDIUMBLOB or MEDIUMTEXT:
- A BLOB or TEXT column with a maximum length of 16777215 characters.
- You do not specify a length with MEDIUMBLOB or MEDIUMTEXT.

LONGBLOB or LONGTEXT:
- A BLOB or TEXT column with a maximum length of 4294967295 characters.
- You do not specify a length with LONGBLOB or LONGTEXT.

ENUM:
- An enumeration, which is a fancy term for list.
- When defining an ENUM, you are creating a list of items from which the value must be selected (or it can be NULL).
- For example, if you wanted your field to contain "A" or "B" or "C", you would define your ENUM as ENUM ('A', 'B', 'C') and only those values (or NULL) could ever populate that field.
