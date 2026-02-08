# Weekly-Vuln-Explanations
Repository for my weekly explanations/summaries of well known web vulnerabilities 

Week 1 - SQL Injections
A SQL injection is when a user puts a malicious input in a field on a webpage that changes how the backend database queries data. The attacker could input something like "fakeuser' OR '1==1' --" into a password field which the database will interpret as a command.
The important concept to understand is how values like passwords and usernames are stored in data. When a user logs into a website their input may be used by the database as a query like: 
SELECT * FROM users WHERE username = 'fakeuser' AND password = 'fakepassword' 

Adding a SQLi into a field can change the query to:
SELECT * FROM users WHERE username = 'fakeuser' OR '1==1' -- AND password = 'fakepassword'
The "--" serves as a comment in SQL syntax so all other parameters that follow are not excecuted. Notice the additional OR statement added to the command as well. Adding OR 1==1 will always make the query return true resulting in the database returning the user at the top of its list (typically admin or root) 

Most SQL injection vulnerabilities occur within the WHERE clause of a SELECT query. Most experienced testers are familiar with this type of SQL injection.
