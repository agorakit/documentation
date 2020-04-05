# Setup inbound emails

!!! note
    Inbound email support is experimental. You might experience bugs, please report them if it happens to your installation.

This additional step allows you to have one mailbox for each group so members can post by email.

You need an email address on server with imap. It must either be a catch all on a subdomain (or even on a domain) or a server supporting "+" addressing (gmail for example allows this).

Let's say you installed Agorakit on agora.example.org :

Create a catchall mailbox on * .@agora.example.org

Then go to admin settings and fill the form there (end of the page).

You need to fill server & login & password

Then you need to fill prefix and suffix. Two cases there :


For a catch all there is no prefix. The suffix in the above example would be @agora.example.org . This will create emails like group-slug@agora.example.storing

On the other hand if you use "+" addressing (a gmail box for instance, let's call it agorakit@gmail.com),

- prefix will be agorakit+
- suffix will be @gmail.com

Wich create emails like agorakit+group-slug@gmail.com

If you enable inbound email, the mailbox will be automatically checked and processed email will be put in a  "processed" folder under INBOX. Failed emails will be similarly put a "Failed" folder under INBOX for inspection.
