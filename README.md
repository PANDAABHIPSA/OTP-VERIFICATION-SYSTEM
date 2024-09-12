# OTP-VERIFICATION-SYSTEM
import random
import smtplib

from email.mime.text import MIMEText

from email.mime.multipart import MIMEMultipart

# Generate a 6-digit OTP

otp = str(random.randint(100000, 999999))

# Set up email parameters

sender_email = "pandaabhipsa.33@gmail.com"

sender_password ="lkwu sjpu ejyx cpsb"

recipient_email =input("Enter your email address: ")

subject ="Your OTP"

message= otp

#Create the email

msg = MIMEMultipart()

msg["From"] = sender_email

msg["To"] = recipient_email

msg["Subject"] = subject

msg.attach(MIMEText (message, "plain"))

#Send the email

server =smtplib.SMTP("smtp.gmail.com", 587)

server.starttls()

server.login(sender_email, sender_password)
text = msg.as_string()

server.sendmail(sender_email, recipient_email, text)

server.quit()

#Prompt the user to enter the received OTP

entered_otp = input("Enter the OTP received in your email: ")

#Check if the entered OTP matches the generated OTP

if entered_otp == otp: print("OTP verified!")
else:
 print("Invalid OTP. Please try again.")
