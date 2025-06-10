write a read script to read a DB from 4 PLCs

there will be only one table and ideally all PLCs should have the same data in their datablocks

the PLC creates 4 different tables for each PLC 

the operator sees only one table. and the operator only needs to know the one line where there is a fault

if there's a PLC with different data on row n, on the table shown to the operator, another row gets added below the row which is red in colour and shows the different data and the PLC in which it's present (like github)