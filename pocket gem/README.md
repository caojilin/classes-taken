Episode Analytics: Homework Instructions

Overview

The majority of our users never generate any revenue (i.e., ‘convert’, in marketing parlance). We want to offer a promotion to some of these ‘non-payers’, in hopes of generating incremental revenue. Unfortunately, it’s not easy to identify true non-payers because many payers don’t convert until several weeks after installing the game. If you simply set a cutoff date and offer sales to everyone who hasn’t yet converted, you might find that revenue actually falls. This can occur if large numbers of not-yet-converted future payers take advantage of the sale instead of paying full price. If you’re not lucky, you might fail to convert a sufficient number of true non-payers, while ‘cannibalizing’ future payers by providing more value than they actually require.

The goal of this assignment is to devise a scheme to maximize incremental revenue. We’ll actually specify the promotion to be offered, namely, a two-for-one sale. What we want you to do is to specify a target group and prescribe a test protocol that can be used to evaluate the results.

We’ve provided sample data for a group of users who installed during the first quarter of 2016. The data includes:

User data, including user ID and install date
Session history, including date and session number
Purchase history, including date and amount
Spending history, including date, currency, and amount
‘Spending’ takes place when a user exchanges game currency (usually ‘gems’) for something of perceived value, such as a new outfit. Game currency can be earned during gameplay, but the bulk of it is obtained by making cash purchases, which are recorded in the ‘iaps’ (in-app-purchases) table.

The data is contained in a MySQL database. Connection details are provided below.

Assignment

Specify a target group of users. Justify your choice using the sample data.
Specify a test and evaluation protocol. How long should the test run? How will you know if you have successfully increased revenue?
Build a model in R or Python to help us identify users who are likely to convert on their own. This part can be done independently -- it’s not necessary to combine the output of this model with your other analyses. Please assume, however, that we would eventually do this.
There are no right answers to these questions. Please use your judgment and explain your reasoning clearly -- that’s what we’re most interested in. The answers might be more subtle than you think.

Important: We expect this assignment to require several hours of effort. (We would spend at least that much time preparing for a real test.) Feel free to submit as much of your work as you like, in any form that suits you. To be considered for the position, however, you must summarize everything on two pages or less.

Data Access Instructions

MySQL Host:

Host: 34.217.198.153
Port: 3306
Database: homework
Username: jilin
Password: pg_Passw0rd
Please note that your username should be all lower-case.

SQL Clients:

Sequel Pro (Macs only)
DBeaver
Sequel Pro is a great option if you have a Mac. If you’re using a Windows machine, you can use any compatible SQL client. We suggest DBeaver.

Connection Instructions:

Sequel Pro
DBeaver
Connect from R
Connect from Python    (...not as easy as connecting from R!)
Tables

users: udid, install_date, lang, country, hw_ver, os_ver
sessions: udid, ts, date, session_num, last_session_termination_type
iaps: udid, ts, date, prod_name, prod_type, rev
spendevents: udid, ts, date, story, chapter, spendtype, currency, amount
Note: Revenue is recorded in the ‘rev’ field and is measured in cents.

Note regarding spendevents table:

When a user purchases gems, the revenue is recorded in the iaps table and a corresponding entry is made in spendevents. The spendtype field in spendevents is recorded as IAP. To understand the spendevents table, please run the following query:

select ts, spendtype, amount 
from spendevents 
where udid = 'd99969a86fda43cda815e5870d76aed2' 
order by ts;

You'll see three types of spendtype:

earnGemsCounter records where the user earns gems. The amount field is negative, indicating that gems are flowing out of our bank account.
IAP records where the user purchases gems. The amount field  is negative, indicating that gems are flowing out of our bank account.
PremiumChoice records where the user spends gems. The amount field  is positive, indicating that gems are flowing into our bank account.