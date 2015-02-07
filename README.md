# DBGEN-CNSSB
Un générateur de données pour l'entrepôt de données en étoile NoSQL orienté colonnes
Built by Khaled Dehdouh

DBGEN-CNSSB readme:

CNSSB is based on SSB dbgen source. The coding style and architecture
follows the SSB dbgen. The original SSB dbgen code stays untouched and
all new code related to SSB dbgen follow the "#ifdef SSB" statements.

For original detailed TPC-H documentation, please refer TPCH_README 
document under the same directory. Here we just list few things that 
are specific to CNSSB.

  
1. How is CNSSB DBGEN built?

Same idea as SSB dbgen setup, which requires user to create an 
appropriate makefile, using makefile.suite as a basis. Make sure to
use "CNSSB" for the workload variable. 

Type "make" to compile and to generate the SSBM dbgen executable. 
Please refer to Porting.Notes for more details and for
suggested compile time options.

Note: If you want to generate the data files to a diffent directory, you should
copy the dbgen executable as well as the dists.dss file to that directory.
 
2. How to generate CNSSB data files?
To generate the dimension tables:


For SSB according the relational approach implementation 

(customer.tbl)
dbgen -s 1 -T c

(part.tbl)
dbgen -s 1 -T p

(supplier.tbl)
dbgen -s 1 -T s

(date.tbl)
dbgen -s 1 -T d

(fact table lineorder.tbl)
dbgen -s 1 -T l

(for all SSBM tables)
dbgen -s 1 -T a


For SSB according the Columnar NoSQL approach implementation
(fact table nlineorder.csv)
dbgen -s 1 -T n

3. What are the changes upon SSB dbgen

changes made upon original SSB dbgen

1. removed star tables
2. renamed the fact table as nLineorder and added/removed many fields
2. integrated and encapsulated all columns (dimension) in one table called nlineorder
3. removed the customer, supplier, part and date. 

The command line option keeps the same as SSB dbgen (The -T options
are changed to reflect different set of tables)

===================== End of README ========================================
