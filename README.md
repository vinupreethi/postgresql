# postgresql

import psycopg2

conn = psycopg2.connect(database = "postgres", user = "postgres", password =
 "1234", host = "localhost", port = "5432")

cur = conn.cursor();

cur.execute('''CREATE TABLE EMPLOYEES( YEAR INT NOT NULL, SALARY REAL);''')

conn.commit();

cur.execute("INSERT INTO EMPLOYEES(YEAR,SALARY) \
   VALUES (1980, 2000 )");

cur.execute("INSERT INTO EMPLOYEES(YEAR,SALARY) \
    VALUES (1990, 3500 )");

cur.execute("INSERT INTO EMPLOYEES(YEAR,SALARY) \
   VALUES (2000, 4800 )"); 

cur.execute("INSERT INTO EMPLOYEES(YEAR,SALARY) \
     VALUES (2010, 6500 )");

cur.execute("INSERT INTO EMPLOYEES(YEAR) \
    VALUES (2020 )");

conn.commit();

cur = conn.cursor()

cur.execute("SELECT * from EMPLOYEES")

rows = cur.fetchall()

for row in rows:
    
    print "YEAR = ", row[0]
     
    print "SALARY = ", row[1], "\n"

YEAR =  1980
SALARY =  2000.0

YEAR =  1990
SALARY =  3500.0

YEAR =  2000
SALARY =  4800.0

YEAR =  2010
SALARY =  6500.0

YEAR =  2020
SALARY =  None

conn.commit();

cur = conn.cursor();

cur.execute("UPDATE EMPLOYEES set SALARY = 8800.00 where YEAR = 2020")

cur.execute("SELECT * from EMPLOYEES");

rows = cur.fetchall()

for row in rows:
   
   print "YEAR = ", row[0]
   
   print "SALARY = ", row[1], "\n"

YEAR =  1980
SALARY =  2000.0

YEAR =  1990
SALARY =  3500.0

YEAR =  2000
SALARY =  4800.0

YEAR =  2010
SALARY =  6500.0

YEAR =  2020
SALARY =  8800.0
