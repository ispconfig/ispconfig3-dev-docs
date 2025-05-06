# Class: ispcmail

Handles the construction and sending of email messages within ISPConfig, supporting plain text, HTML, attachments, custom headers, and SMTP authentication.

## Methods
- **setSender($from, $from_name = '')**
  - Sets the sender address and optional name for the email.
- **setSubject($subject)**
  - Sets the subject line for the email.
- **setMailText($text)**
  - Sets the plain text body of the email.
- **setMailHtml($html)**
  - Sets the HTML body of the email.
- **setHeader($header, $value)**
  - Adds a custom header to the email.
- **readAttachFile($filepath, $filetype = '', $filename = '')**
  - Attaches a file to the email, with optional MIME type and filename.
- **setOptions($options)**
  - Sets SMTP and mailer options, such as authentication and server.
- **send($to, $cc = '', $bcc = '')**
  - Sends the email to the specified recipients, with optional CC and BCC.

## Properties
- **html_part, text_part**: Stores HTML and plain text body content.
- **headers**: Array of custom headers.
- **_smtp_conn**: SMTP connection resource.
- **attach_type, attachments, mime_boundary**: Used for handling attachments.
- **body**: The complete email body.
- **user_agent**: User agent string for the mailer.
