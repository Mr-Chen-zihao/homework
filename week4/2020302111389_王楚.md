# homework4

##### p15

> What is the difference between MAIL FROM: in SMTP and From: in the  mail message itself？

 In SMTP is a message from the SMTP client that identified the sender of the mail message to the SMTP server. 

On the mail message itself is not an SMTP message, but is  a line in the body of the mail message.

##### p20

> Suppose you can access the caches in the local DNS server for all computers in the department. Can you propose a way to roughly determine the Web servers (outside your department) that are most popular among the users in your department?

Sample the cache multiple times at different points in time to see which Web servers are more likely to be in the cache.  