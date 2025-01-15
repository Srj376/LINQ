Read Data Table
(
From row In Input_Empdt
Select row
).copytodatatable

Group by department and gives first value
(
From row In Input_Empdt
Group row By a=row("Department") Into grp=Group
Select grp.first                                   //gives first value from group
).copytodatatable

Order by Ascending & Descending
(
From row In Input_Empdt
Order By row("Name") Ascending,row("Department") Descending
Select row
).copytodatatable

Join
Ineer join 
(
From row1 In Input_Empdt Join row2 In Input_Deptdt
On row1("Department").tostring Equals row2("Department").tostring
Let anu_sal=CInt(row1("Salary"))*12
Let c=If(anu_sal>=900000,"Need to Fill ITR","No Need to Fill ITR")
Select op_dt.Rows.Add({row1("EmployeeID"),row1("Name"),row1("Salary"),row1("Department"),row2("DepartmentID"),row2("Location"),row2("Head"),anu_sal,c})
).copytodatatable

outer join
1.left outer
2.right outer
3.full outer

