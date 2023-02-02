<!-- HEADER -->
<div align="center">
  <h1 align="center">4. Normalization</h1>
</div>

# What is normalization?
* Processes of reducing the redundancy of data
* Improves the data integrity

# Types
* 1NF
* 2NF
* 3NF
* BCNF

## 1NF
* Removes repeating groups from the table
* Create a seperate table for each set of related data
* Identify each set of related data with a primary key

### 1NF example
```shell
employee ID     Phone number
000001          123456788
                218347192
000002          138975871
000003          189758728
000004          918375592
                982371784

==>

000001          123456788 
000001          218347192
000002          138975871
000003          189758728
000004          918375592
000004          982371784
```

## 2NF
* It has to be in 1st Normal Form
* Table also should not contain partial dependency

### 2NF example
```shell
Employee Id   Department Id   Office Location
1EDU001       ED-S1           Seoul
1EDU002       ED-C1           Incheon
1EDU003       ED-H1           Daejeon
1EDU004       ED-T3           Jeju

==>

Employee Id   Department Id
1EDU001       ED-S1 
1EDU002       ED-C1 
1EDU003       ED-H1           
1EDU004       ED-T3           

+

Department Id   Office Location
ED-S1           Seoul
ED-C1           Incheon
ED-H1           Daejeon
ED-T3           Jeju
```

## 3NF
* It has to be in 2nd Normal Form
* There should be no transitive dependency for non-prime attributes

### 3NF example
```shell
Student Id    Student Name    Subject Id    Subject   Address
1             Alvin           A             Java      Seoul
2             Blvin           B             Python    Incheon
3             Clvin           C             C++       Daejeon
4             Dlvin           A             Java      Jeju

==>

Student Id    Student Name    Subject Id    Address
1             Alvin           A             Seoul
2             Blvin           B             Incheon
3             Clvin           C             Daejeon
4             Dlvin           A             Jeju

+

Subject Id    Subject
A             Java  
B             Python
C             C
A             Java      
```

## Boyce Codd Normal Form (BCNF)
* It has to be in 3rd Normal Form
* Every functional dependency A -> B, then A has to be the Super Key of that particular table

### BCNF example
```shell
Student ID    Subject   Professor
1             Java      Prof.A
2             SQL       Prof.B
3             Java      Prof.A
4             C++       Prof.C
5             DBMS      Prof.D

==>

Student ID    Professor ID
1             1A
2             2A
3             3A
4             4A
5             5A

+

Professor ID  Subject   Professor
1A            Java      Prof.A
2A            SQL       Prof.B
3A            Java      Prof.A
4A            C++       Prof.C
5A            DBMS      Prof.D
```