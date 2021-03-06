# Scala database interface with postgresql platform

###### developed by Shiva

## Documentation

#### Usecase
Provide basic foundation for postgresql database interface with Scala

The interface is built to work with postgresql JDBC and provide common database functionality to the users.
Users can extend the funtionality from the DatabaseManager.scala where the basics of database communication is provided.


#### DBConnections.scala

Contains connection settings for Postgresql, however users can add diffrent database type connection settings by implementing 
BasicDatabaseConnection interface. Please check the DBTraits.scala for more information.

#### DBManager.scala

Provides basic funtionality to communicate with the database.

###### getSchema(tablename:String):DBTableDef
table definition schema of any table from the database by passing the table name in lowercase NOT uppercase
for example : t_users not T_USERS > postgresql jdbc is case sensitive and it only tends to take it only in lowercase format

returns tablename:String, schema:Map[String,(String,Int)]
where schema -> Map of ColumnName(String), ( dataType(String), columnPosInTable(Int) )

###### fetch(query:String):DBFetchedData
fetches data from database

returns columnsCount and rowSet of type ResultSet Iterator (RsIterator)

###### execute(statement:String):Boolean
executes sql statements

returns a Boolean, true or false for sucess or non-sucess results

###### executeBatch(data:Map[String,String],tableDef:DBTableDef):Boolean
executes batches of data at once. 

takes parameters, data:Map[String,String] to represent an Object with fields and its values in hash map format

returns a Boolean, true or false for sucess or non-sucess results

#### Settings

provided a postgresql jar file version 9.4

documentation - http://www.postgresql.org/docs/9.4/static/index.html



