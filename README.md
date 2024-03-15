# Personalized-Email-Sender-Script
from email.message import EmailMessage

import ssl
import smtplib

email_sender = "sender@gmail.com"
email_password =  "password"


email_reciver = "reciver@gmail.com"

subject="coders cave project"
body = """
 Develop a straightforward and user-friendly Simple Clock Web Application
that displays the current time in a clear and visually appealing manner. The
application aims to provide users with a minimalistic yet functional clock
interface that is accessible from web browsers.
"""
em = EmailMessage()
em['From'] = email_sender
em['TO'] = email_reciver
em['subject'] = subject
em.set_content(body)

context = ssl.create_default_context()

with smtplib.SMTP_SSL('smpt.gmail.com', 465, context=context) as smpt:
    smpt.login(email_sender,email_password)
    smpt.sendmail(email_sender,email_reciver, em.as_string())