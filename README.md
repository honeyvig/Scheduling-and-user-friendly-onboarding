# Scheduling-and-user-friendly-onboarding
Working for several years on an awesome AI-powered photo editing app. We recently launched the web version of our service and would like to talk to specialists about how user-friendly and intuitive our website is for someone seeing it for the first time.
================
Here's a Python script for handling the scheduling and user-friendly onboarding of an interview for your AI-powered photo editing app:

import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

def send_email(to_email, subject, body):
    # Set up the email server
    smtp_server = 'smtp.gmail.com'
    smtp_port = 587
    sender_email = 'your_email@example.com'
    sender_password = 'your_email_password'

    # Create the email message
    msg = MIMEMultipart()
    msg['From'] = sender_email
    msg['To'] = to_email
    msg['Subject'] = subject

    # Attach the body to the email
    msg.attach(MIMEText(body, 'plain'))

    # Send the email
    try:
        with smtplib.SMTP(smtp_server, smtp_port) as server:
            server.starttls()  # Secure the connection
            server.login(sender_email, sender_password)
            server.sendmail(sender_email, to_email, msg.as_string())
            print(f"Email sent to {to_email}")
    except Exception as e:
        print(f"Failed to send email: {e}")

def schedule_interview():
    # Sample interview details
    subject = "Invitation for AI-Powered Photo Editing App Interview"
    body = """
    Hello,

    Thank you for showing interest in providing feedback on our new AI-powered photo editing app! We would love to hear your thoughts on the user-friendliness and intuitiveness of our website.

    The interview will be held on Google Meet at a time that works best for you. The interview will last up to 1 hour and will be conducted in either Russian or English.

    Please let us know your preferred time, and we'll send you the calendar invite.

    Looking forward to your insights!

    Best regards,
    The AI Photo Editing App Team
    """

    # List of recipients (emails of the specialists)
    recipients = ["specialist1@example.com", "specialist2@example.com"]

    for recipient in recipients:
        send_email(recipient, subject, body)

if __name__ == "__main__":
    schedule_interview()

How this works:

    Email Setup: The script uses smtplib to send personalized interview invitations.
    Scheduling Interviews: The body of the email invites the recipient to schedule a Google Meet interview, providing flexibility on the timing and confirming language preference (Russian or English).
    Figma Integration: If Figma is involved, consider attaching a link to the Figma design or embedding it in the email body.

This approach allows for easy scaling and scheduling for multiple specialists while ensuring a personal touch in communication.
