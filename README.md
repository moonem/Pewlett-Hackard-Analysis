# Employee Database Analysis

A large company (i.e. "PH") employee data, having 300,024 employees working in 9 departments, has been analyzed to retrieve the number of retiring-soon employees and to find the number of employees eligible to participate in a part-time mentorship program. The result of this analysis should help the management and HR to plan ahead about new recruiting if a big number of employees retire soon.

## Overview of the Analysis

  * Scope of the data analysis
  
    * This project requires *data modeling, engineering* and *analysis* of the employee data. Initially, an entity (i.e., tables) relationship diagram (ERD) is created (Fig. 1) using **QuickDBD** by identifying primary- and foreign-key(s) in each of the 6 tables as shown below,
    
           - departments,
           - dept_emp,
           - dept_manager,
           - employees,
           - salaries,
           - titles.
  
         ![ERD of EmployeeDB](/Resources/EmployeeDB.png)
    
    Fig. 1. Entity Relationship Diagram (ERD) of the PH company employees.
    
  * Software Tools Used in the Analysis
  
    *  The relational database system **PostgreSQL** is used to create and store necessary tables of employee related data, and **pgAdmin 4.0** provides the window to access, edit and query the database.

## Results

To obtain the required information (i.e. the number of retiring employees with title, and employees eligible for the mentorship program) from the data stored in the 6 tables, as shown in Fig. 1, multiple queries have been formulated to produce a few more tables with the filtered data as described below.

 Step-1:
  
  A new table **retirement_titles** is formed by joining *employees* and *titles* tables and filtering employees born between 1952 and 1955. The SQL code and the table are shown below.
  
  ![retirement_titles](/Resources/retirement_titles.png)
    
    Fig. 2. SQL code and the filtered table "retirement_titles" for employees born between 1952 and 1955.
    
  Step-2:
  
   As shown in Fig. 2, there are some employee names appearing multiple time because of their *title* of job at different times. A query is formed using DISTINCT ON and ORDER BY commands on the *emp_no* column in the previously formed *retirement_titles* table. The output of this query is stored in a new table **unique_titles* as shown below.
   
   ![unique_titles](/unique_titles.png)
    
    Fig. 3. SQL code and the table "unique_titles" for employees born between 1952 and 1955 with their latest job-title.
   
Step-3:
  
   To acquire the count of employees under each of the titles, a DISTINCT COUNT and GROUP BY query is carried out on the *title* column in the previously formed table *unique_title*. The output of this query is stored in a new table **retiring_titles** as shown below.
   
   ![retiring_titles](/retiring_titles.png)
    
    Fig. 4. SQL code and the table "retiring_titles" for retiring employees grouped under 7 different job-titles.
    
 Step-4:
  
   A query is written and executed to create a Mentorship Eligibility table for current employees who were born between January 1, 1965 and December 31, 1965. The output of this query is stored in a new table **mentorship_eligibility** as shown below. The left side of Fig. 5 shows all the 14 tables in the **PH_EmployeeDB** database including the 6 basic tables we started our analysis with.
   
   ![mentorship_eligibility](/mentorship_eligibility.png)
    
    Fig. 5. SQL code and the table "mentorship_eligibility" for retiring employees born in 1965.
    
 ## Summary
 
 Besides the the tables shown in Figs. 2 to 5, two more tables have been created to get more insight on the employee retirement status. The **emp_info** table has a comprehensive view of the current employees born between 1952 and 1955, and who were hired between 1985 to 1988.
 
  ![emp_info](/emp_info.png)
    
    Fig. 6. SQL code and the table "emp_info" for current employees born between 1952 and 1955, and got hired between 1985 and 1988.
    
 Another table named **manager_info** was formed to get the name of the managers and their respective department names as shown below.
 
  ![manager_info](/manager_info.png)
    
    Fig. 7. SQL code and the table "manager_info" for the manager and their department names.
    
 *Note* - The "INTO file_name" command in the code-block is shown as commented-out in Figs. 2 to 7. This is done to run the query and show the query result in the *Data Output* pane within the *PgAdmin* window. The INTO command is executed to store the respective output data into corresponding tables. All these tables are stored as *.csv* files in a common folder.
 
 
 
 #### Contact:
  m.a.moonem@gmail.com
   
