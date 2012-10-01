Maaail - The command line emailer.
==================================

### Purpose

Easy sending of email on the command line (through gmail or otherwise).

Use Cases
---------

### Example Usage (send basic email)

    maaail --to=tom@example.com \
            --cc=joe@example.com \
            --cc=ted@example.com \
            --subject="Test Email"

causes an editor session to start, when finished asks if you really want to send
the email, if yes sends it. It automatically assumes (unless otherwise
configured) that you want to send a markdown email.  Otherwise, prompts to

1. edit
1. save draft
1. discard

it uses the cascading config files (install/path/maaailrc, ~/.maaailrc,
`pwd`/maaailrc) to configure stmp, from, replyto, drafts folder, formatting
(eg. plain, markdown, rst, etc...), etc...

### Example Usage (send email with 2 attachments)

    maaail --to=tom@example.com \
           --cc=joe@example.com \
           --cc=ted@example.com \
           --attach=./path/image.png \
           --attach=./path/audio.mp3 \
           --subject="Test Email"

causes an editor session to start. It includes a pre-written example for
including the images inline with whatever syntax you are using (markdown,
restructured text, etc...).

### Example Usage (override config file options)

    maaail --to=tom@example.com \
           --cc=joe@example.com \
           --cc=ted@example.com \
           --format=plain \
           --from=ed@example.com \
           --reply-to=ed@home.com \
           --body=./path/to/body.txt \
           --subject="Test Email"

would ask for confirmation to send the email contained in body.txt

Features
--------

1. Connect to smtp (possibly with TLS to support Gmail and similar services)
1. Send email with attachments.
1. Use multi-part mime to support HTML + plain text email
1. Support multiple composition formats (possibly using pandoc [allows use of
   subprocess])
1. Support to, cc, bcc, reply-to, etc smtp-headers ...
1. Support using configuration files (in .ini format for easy of writing or
   .json format)
1. Support cascading configuration files (pretty easy, I already have the code
   for this)
1. Allow piping of the message body on the standard in (eg. using a special
   value to the body flag --body=-)

### Bonus

1. Store drafts in a git repo
1. Allow referencing of drafts with

      --draft=name
      --draft=name@[git-commit-spec]

1. Make the git repo human understandable

### Double Bonus Features

1. Support the unix mail format to allow the users to write up there own headers
   (for to, cc, bcc, etc...)

