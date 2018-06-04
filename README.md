# Week-8-Assignment
Pentesting Report

    XSS

    Summary: A XSS vulnerability found in the Green URL.
    GIF Walkthrough:
    Steps to recreate: 
    1. In the Green url, click the Contact tab.
    2. Fill in the Name and Email, and get a XSS script from a search. 
    3. For Feedback the XSS script used was <body onload=alert('test1')> with replacing test1 with anything you want. 
    4. Click the Login tab, and log in.
    5. Click on Feeback 
    
    When clicked on, the XSS error will come up with whatever is inside the input which in the script is test1
   
   
   
   
   
   

    User Enumeration

    Summary: A User Enumeration found in the Green URL.
        
    Steps to recreate: 
    1. In the Green url, click the Login tab.
    2. Knowing the valid usernames, type the valid username and an INCORRECT password and press Submit, an error will appear in BOLD.
    3. Use an INCORRECT/RANDOM username and password, an error will appear but NOT in  BOLD
    
    This reveals that valid usernames are verified by the system, bolding the valid usernames. 

    
    
    
    
    
    
    IDOR Insecure Direct Object Reference
    Summary: IDOR vulnerability found in the Red url.
    Steps to recreate: 
    1. On the Red url click the Find a SalesPerson tab.
    2. Click on the first Salesperson.
    3. Check the url and near the end will be id= which will have a number following number 1.
    4. Change the 1 at the end of the URL from 1 all the way to 10 and 11.
    
    The url with 10 will reveal "NOT PUBLIC UNTIL SEPT. 1" and 11 will reveal "FIRED FOR STEALING".
    These are things that people visiting the website should not have access to.
    
    
    
    
    
    
    CSRF Cross-site Request Forgery
    Summary: CSRF vulnerabiliy found in the Red url.
    Steps to recreate:
    1. Click the Login tab, and login with valid username and password.
    2. Click on Countries, States, and Territories.
    3. Click on the US Show button.
    4. Click any state, then click Edit.
    5. Right-click and click Inspect Element and right-click to Edit HMTL and copy the form starting with <form action="edit.php?id=15" method="post">. #the form action value may be different.
    6. Open a text editor like Notepad or Leafpad and paste the form action you copied.
    7. Copy the URL from the same page that the form action was copied from.
    8. In the pasted form action in the txt file, paste the url in the <form action="edit.php?id=15" method="post"> which would look like this <form action="insert url here" method="post"> and save and name the file as an HTML file.
    
    9. Log out of the url.
    10. Click the file you saved.
    
    When you click the file you created, it'll open up the Edit page for the US States. Only logged in users should have access to do to this.
    You'll be able to make changes to the US States without having to be logged in.
    
    
    
    
    
    Session Hijacking
    Summary: Session Hijacking Vulnerability in the Blue url.
    Steps to recreate:
    1. Have the Blue url open and Burpsuite running, meaning that its not intercepting.
    2. Login with a valid username and password, Burpsuite will capture the POST request.
    3. Click on the POST request and view the username and password in plaintext. #For the password, hover your mouse over the password to show actual password. 
    
    This shows how the username and password are in plaintext and if someone  malicious were to capture this traffic, they could effectively login with someones credentials.
    
    
    
    
    
    SQLI SQL Injection
    Summary: SQLI vulnerability in the Blue url.
    Steps to recreate:
    1. In the Blue url, click on Find a Salesperson.
    2. Click on any Salesperson.
    3. Insert ' OR SLEEP(5)=0--' at the end of the url and press enter. #This will cause the url to freeze for a certain amount of time, which is 5 seconds for that SQLI. 
    
    If a user is on the Find a Salesperson tab, a malicious user could insert that same SQLI with a higher amount of seconds like 100. ' OR SLEEP(100)=0--'
    

