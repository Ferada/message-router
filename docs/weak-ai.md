# -*- mode: markdown; -*-
# vim: set ft=markdown:tw=72:

# Weak AI and the disconnectness of current computer environments

Todays computing environments are very discrete in terms of how programs
work together.  With the exception of e.g. (command line) tools in the
Unix environment, or VST plugins, typical applications are firstly
monolithic language-wise and secondly monolithic platform-wise.  Even
though architecture-wise it is no problem to let different programs
communicate with another it is still extremely difficult for developers
to let applications interact e.g. on the Windows platform.  This may
very well be a conscious decision to integrate all functionality into a
single product.  The highpoint of this trend are web browsers which
today redevelop every single concept on the basis of web technologies.

See also the file `routing.md` on how to integrate N + 1 environments.

For users this means to choose between products.  The premise is here
that you have to do a significant amount of work to become proficient in
a new nontrivial environment.  Whether this is a word processor, web
browser, or an email client is irrelevant.

## Have a minion

Working with computer environments is currently the use of tools.  The
user has to direct their effect to the intended use, otherwise they
won't do any work at all.

Whether you call it minion, daemon, or personal assistant:  Having a
dedicated application manage the boring (read: repeating) parts of the
users activities is beneficial to the overall happiness.

In particular this means handling of typical PIM tasks, i.e.
appointments, contacts and in general emails.  In general this means
handling workflows, keeping track of events and state.

Customizable applications are halfway there.  If users can customize the
application to their liking, integrating different tools, they are some
of the best out there.

Still, most applications are UI driven.  Converting e.g. a mail client,
which typically includes filtering and scoring mechanisms, into a daemon
would be one of the first steps to get minion-like behaviour.

## Requirements

Interoperatiblity, obviously.  Data files, if necessary, have a standard
format.  Best if a standard database can be used.  Multiuser (in terms
of operating system users) capabilities for accessing data files.

Clear distinction between UI and daemon code.  The choice of GUI toolkit
should be up to the user, so different clients can be used.

Details in `routing.md`.

## Interaction

I'm guessing that for wide adoption and adoption beyond the circle of
technically skilled users an at least partially conversational interface
is necessary.

Of course a plain shell to enter direct commands instead is a good
addition.

## Features

Users should be able to select different services.

My personal list would be:

- Access to email facilities including address book, indexing and
  subscribed mailing lists (direct Maildir, mail server).
- Calendar including appointments (CalDAV, CardDAV).
- Status detection including geolocation and tracking of current
  projects.
- Encryption and identity handling.  Depending on settings emails and
  other messages should be encrypted and signed.  Since the minion
  operates on a trusted system, either messages can be directly
  de-/encrypted on the minion system, or this operation is deferred to
  the user machine, if available and otherwise buffered until one
  becomes available.  Deferring to the user machine with a similar
  solution to `ssh-agent` (not `gpg-agent`, because that one doesn't
  forward any connections).
