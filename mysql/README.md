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
