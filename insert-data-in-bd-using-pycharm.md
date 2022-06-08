How to create table and  insert data from excel to db using Pycharm
========================================

## First we need to include the required library - _Psycopg2_ and _xlrd_

 ### **<p align="center"> Psycopg and  xlrd descriptions </p>**

 **Psycopg** is the most popular PostgreSQL database adapter for the Python programming language. Its main features are the complete implementation of the Python DB API 2.0 specification and the thread safety (several threads can share the same connection). It was designed for heavily multi-threaded applications that create and destroy lots of cursors and make a large number of concurrent “INSERT”s or “UPDATE”s.
 
 **The xlrd** is a library for reading data and formatting information from Excel files in the historical . xls format.

 ### **<p align="center"> How to add a library  </p>**
 
 1. Go to Pycharm itself
 2. Open in the upper corner on the left side - _File_
 3. _File_ -> _Settings_
 4. Open _PythonProject1_ _(If this is your first project)_
 5. _PythonProject1_ ->  _Python Interpreter_
 6. Click '**+**' on the top left side 
 7. Choose _Psycopg2_ , _xlrd_ and  download

 What to do if Pycharm doesn't see the library? 
   [Watch this](https://www.youtube.com/watch?v=3SvmrzqVmXo) 
 
 ### **<p align="center"> Database connection  </p>**

 Importing Libraries
 ```
 import xlrd
 import psycopg2
 ```
 Connecting to the DB
 ```
 DB_HOST = '********'
 DB_NAME = 'name'
 DB_USER = 'user'
 DB_PASSWORD = '*********'
 ```
 ```
conn = psycopg2.connect(database=DB_NAME, user=DB_USER, host=DB_HOST, password=DB_PASSWORD, port=DB_PORT)
print("Database connected successfully")
 ```
 ### **<p align="center"> Create table  </p>**

 Create table into DB
 ```
cur=conn.cursor()
cur.execute("""
CREATE TABLE fortemobi.f_mb_beeline_partner(
    partner_phn_num varchar(20) ,
	seller_fio character varying (255),
	filial character varying (255),
	urp_cbo_urpz character varying (255),
	position character varying (255)
	
)
""")
conn.commit()
print("Table created successfully")
```

If everything is correct, the console will display :
```
 "Table created successfully" 
```

### **<p align="center"> Insert data from excel to db </p>** 

After creating the table, will load data from excel files to db, but for this you also need to connect to the database, as shown above, you can create a new python file or continue without **conn.commit**
```
xfile = r'C:\Users\Пользователь\Desktop\test\Beeline partner'
workbook = xlrd.open_workbook(xfile)
sheet = workbook.sheet_by_index(0)
```
 *to avoid errors it's better to create a folder and inside create an excel file
* `r` - to read an excel file
* `sheet` - data on the first page of excel ,using the index define sheets 


After reading the excel file, insert the data to the database

```
for r in range(1, sheet.nrows):
phn_num = int(sheet.cell(r, 0).value)
fio = sheet.cell(r, 1).value
filial = sheet.cell(r, 2).value
urp = sheet.cell(r, 3).value
position = sheet.cell(r, 4).value
values = (phn_num,fio, filial, urp, position)
cur.execute("INSERT INTO fortemobi.f_mb_beeline_partner VALUES (%s, %s, %s, %s, %s)", values)
```
And in the end, you need to close all processes
```
conn.commit()
cur.close()
conn.close()
```
* `conn.commit()` - this method sends a COMMIT statement to the MySQL\PostgreSQL  server, committing the current transaction. Since by default Connector/Python does not autocommit, it is important to call this method after every transaction that modifies data for tables that use transactional storage engines.
* `conn` - connection lives as long as you need for your operations, if you have operations with the database in a row - the connection does not need to be closed and reopened; but if you have worked with the database, and then you have a break - for example, you are grinding some data and while you are not writing or reading the database, then it is better to close the connection so that it goes to the pool and other processes working with the database have enough these same connections; and yes - it is better to close the connection at the end of working with it and do it for sure (through try / finally) in order to release the resources associated with it exactly
