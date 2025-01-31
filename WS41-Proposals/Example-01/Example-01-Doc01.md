# Client #1: HAS 

Client Info: 
- Saudi Arabia
- $36 to $100
 
# Documents

1. Word document pasted below. 
2. [Excel Document - Data](02-Clean.xlsx)
3. Excel Document #3 (displayed in screen shots at the bottom of this page)

--- 

hi Darren,
can you help create a team workload and tasks tracking platform with dashboards and KPI for the team. Please go through the attached project requirements and details and let me know your thoughts and if this project is within your services.
Attached: 1. Sample workload and task dashboard. 2. Project requirements. 3. Sample weekly tasks to be entered and assigned on a weekly bases and updated daily.
Suggestions but not limited to for the platform interface: PowerApp for data entry and updating tasks, Power Automate for automation, SharePoint for database and storing data, Power BI for Dashboards and data visualization.
If you have any other suggestions or inquires, please feel free to contact me. thank you.


1.	Create Tasks and workload planning / Tracking platform.
2.	Weekly tasks will be entered through data entry page and stored into a database with the following parameters:
    - S. Notification: number  
    - Project (Type): Asset, Maintenance, Project, Other
    - DRSS/DTH: number
    - SO: number
    - Description: text
    - Equipment Type (always in caps?): ABCD, EFGH, IJKL, MNOP, OTHER
    - Serial Number: text 
    - SOW (Statement of Work): 
        - Dismantle & Inspect
        - Inspect & Pressure Test
        - Modification
        - Refurbish
        - Repair
    - Owner:
        - A&T
        - Engineering
        - Production
        - QC
        - REMS
        - WH
    - START DATE: Date
    - ETC: Date
    - REMARK:	Text
    - Stage	
        - 1st
        - 2nd
        - 3rd
    - Priority	
        - Low
        - Medium
        - High
        - Urgent
    - Status	
        - Canceled
        - Completed
        - In Progress
        - On Hold
        - Open
        - Review
3.	Automatic status "Open" will be assigned to the new tasks entered into the system.
4.	No Duplicate tasks shall be entered. The task will be identified with the "S. Notification" Number assigned to the task.
5.	Same Task can be duplicated only if the stage is different. (e.g. If a task is already added and marked completed, the Same task with the same S. Notification number can be entered again with different stage "2nd, or 3rd and so on.)
6.	If Task is being entered with existing "S. Notification", the form will automatically pull the task's data from the database and allow for updates only.
7.	The "Assign Task" page which will display the "opened" tasks only and allow to assign an Engineer & a Reviewer from the Team's list.
8.	"Assign Task" page should show some analysis to help assigning tasks to employees (e.g. each employee workload, currently in progress tasks. capacity of the week, meetings reserved time, days off or leave for each employee within the upcoming week).
9.	The "Assign Task" Page should include the following parameters:
    - Assigned Engineer	Select From the List (7 Team Members)
    - Estimated Time	Numbers, e.g.( 1, 2, 0.5 0.25)
    - Actual Time worked	Numbers, e.g.( 1, 2, 0.5 0.- 25)
    - Assigned Reviewer	Select From the List (7 Team Members)
    - Estimated Review Time	Numbers, e.g.( 1, 2, 0.5 0.25)
    - Actual Review Time	Numbers, e.g.( 1, 2, 0.5 0.25)
    - Status	
        - Canceled
        - Completed
        - In Progress
        - On Hold
        - Open
        - Review
    - Engineer Comments	text
10.	Once a task is assigned to an Engineer, the Engineer should be automatically notified through email or by clicking a button. The time will start clocking for the assigned employee.
11.	Once the Engineer complete the tasks, he/she should update the tasks status to "Review" and the time will automatically stop clocking for the assigned engineer. 
12.	Once status has changed to "Review" The reviewer will be automatically notified or by clicking a button and the time will automatically start clocking for the reviewer.
13.	Once the reviewer finishes a task, he/she should update the task status to "Complete". Once status has changed the time will automatically stop clocking for the reviewer and the Completion Date will be automatically assigned to the task.
14.	The Assigned Engineer/ Reviewer can change the tasks status to any of the above list and write comments for the tasks.
15.	The system should automatically generate a daily Report for all tasks progress that are due for next week.
16.	Dashboard should visualize all Tasks data for analysis with the ability to filter data.
17.	Team utilization KPI Dashboard should show the total hours spent per tasks for each employee.
18.	Capture Meetings occurrence (e.g., every Thursday 1 hour for 2 employees and every Sunday & Wednesday for other 3 employees) create a list to capture the total meetings hours per month to be projected for each employee in the dashboard.
19.	Team utilization Dashboard should compare the capacity with the assigned tasks for each employee (e.g., Emplyee1 capacity = 8hr/day x 5 days/week = 40hr /week).
20.	Team utilization should record the Days off/Leave Days in a separate table to be projected in the dashboard for capacity analysis and sorted by monthly/ quarterly/ yearly.
21.	Forecast dashboard should take average last year's tasks vs. capacity to estimate the next year capacity. 
22.	The Actual Task time spent is the total time spent on the task = the engineer actual time + reviewer actual time.
23.	The estimated Time to complete a task is the Time from assigning the task to the Time the task is marked "complete".  

---

# Excel Document #3

## Sheet 1

![01.png](./images/01.png)
![01b.png](./images/01b.png)
![01c.png](./images/01c.png)

# Sheet 2

This is simply a listing of fields at the top of the 2nd sheet. 

- S. Notification	
- Project	DRSS/DTH	
- SO	
- Description	
- Equipment Type	
- Serial No.	
- SOW	
- OWNER	
- START DATE	
- ETC	
- REMARK	
- Assigned Engineer	
- Estemated Time	
- Assigned Reviewer	
- Estemated Review Time	
- Actual Review Time	
- Priority	
- Status	
- Engineer Comments

![02.png](./images/02.png)

# Sheet 3

