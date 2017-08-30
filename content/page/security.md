---
author: itools
date: 2016-09-21 15:44:05+00:00
draft: false
title: Email security is very important at Mail-List.com.
url: /security/
---

# Email security is very important at Mail-List.com.

We have two items of value in our system. The emails that have been sent to your list, and the email addresses of your subscribers. We do not have any other information about your subscribers other than their email address.

We do not have any credit card information stored in our computers. We use [Stripe](https://stripe.com) to accept payments via credit card.

This web page details where the emails and email addresses are stored, so that people with sensitive emails can make appropriate decisions about what options to use.

# ​Mailing List Reflector

​Our system is a mailing list reflector. Emails come in, and are sent to the email address of all members of that mailing list.

There is no mailbox to login to on our system. None of the subscribers have a password, as the email is sent to their regular email account.

The list moderators do have a password to customize the list settings, add and remove people from the list, and see the list of subscribers. However, that access does not show any of the emails sent to the list.

All reports, including the list of subscribers are not shown on the screen, but rather are sent to the email address of the moderator.

# ​Searchable Web Archive

​We do have a [Searchable Web Archive](http://help.mail-list.com/m/59124/l/558478) option, that stores the emails on a web page. Typically that web page is password protected. All emails sent to the mailing list are permanently stored in this web archive.

The Searchable Web Archive option is off by default, and it does increase the cost of your mailing list if you turn it on.

# Bounce Redelivery System

We have a [Bounce Redelivery](http://help.mail-list.com/m/59114/l/558250) option that is a temporary web archive of all emails for the past two weeks. The purpose is to provide a place to read the emails, for those subscribers who had a message blocked by their ISP's spam filters.

The Bounce Redelivery option is on by default, and can be turned off.

Make Use Bounce Re-Delivery System = No in the Reports Section

# Inbox Monitoring System

<div class="thrv_paste_content thrv_wrapper tve_empty_dropzone" style="">

We can [monitor the delivery](http://help.mail-list.com/m/59124/l/558342) of your emails into the inbox at the large ISP’s. To accomplish this, we send your emails to our special accounts at these ISP’s, so turn this option off to stop your emails from going there.

The Monitor ISPs If Your Message Is In Their Inbox option is on by default and can be turned off.

Make Monitor ISPs If Your Message Is In Their Inbox = No

</div>

# Clickable Attachments

When this option is turned on, any attachments are removed from the emails and stored in our S3 bucket on Amazon. A link to that attachment is inserted into the outgoing emails so that people can download the attachment if they want.

​The attachments will be removed from S3 automatically after 30 days. There is an option (Delete Attachments From Server) to change the time delay to 1 year or forever.

​In addition, there is an option (Make Attachment Filename Unguessable) to make the URL of these attachments a long random string, that is unguessable.

<span class="screen-reader-text">About WordPress</span>

# Disappearing Ink

We have the Disappearing Ink option, for people concerned with privacy. This option will replace the body of the message with a link to the temporary web page. The subscriber will get the Subject Line of the message, and must already know the user name and password to see the contents of that email on the web page. The message on the web page expires after one day, three days, or 7 days, depending on the option selected by the list owner.

# Mailing List Servers

Our servers are in the Amazon Cloud and run Ubuntu Long Term Support Linux for maximum stability and security. Our Mail Transport Agent is the Ubuntu version of Exim.  The Mailing List software is written in Perl and Python.

The mailing list server is accessible for troubleshooting purposes via Secure Shell from designated IP addresses with the matching private key. Should an attacker get access this way, they would be able to see the list of subscribers and all emails sent in the past 30 days.

# Backups

Subscriber lists are backed up to several private S3 Buckets in Amazon. S3 is designed for durability of 99.999999999% of objects. The data is redundantly stored across multiple facilities and multiple devices in each facility.

The first S3 bucket is versioned and contains the past 7 days of subscriber email addresses. The second S3 bucket contains a weekly snapshot starting from the inception of the mailing list. So we are able to recover a mailing list from almost any point in time.

The list settings database (containing the custom options of each mailing list) is also a private S3 bucket.

We do not have any backups of emails sent to the mailing lists. The Searchable Web Archive and Bounce Redelivery System are exceptions, assuming those options are turned on.

Emails are stored on the listserv server for 30 days to assist in troubleshooting and debugging. We do take image copies of the servers on a continual basis, and some of those backups are available for up to 90 days.​

# Message Queues

​Outgoing emails are stored in Amazon SQS while awaiting delivery. SQS is a queueing service that allows independent delivery machines to pull in an outgoing message and a handful of subscriber addresses. So delivery of each message is spread across multiple machines for quick and efficient delivery.

# Encryption Of Emails In Transit

Incoming and outgoing emails are encrypted, assuming the sending or receiving mail server also supports encryption. That means nobody can see the contents of your emails as they are pushed through the tubes of the Internet.

# Summary

Emails to a mailing list are semi public, in that all members will receive the email. What they do with their copy of the email is out of our control.

In summary, if you are concerned about people seeing the contents of your emails, do not turn on the Searchable Web Archive option. Turn off the Bounce Redelivery and the Inbox Monitor options. And consider turning on the Disappearing Ink option.
