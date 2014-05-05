# -*- mode: markdown; -*-
# vim: set ft=markdown:tw=72:

# Message routing or how to integrate N + 1 languages

Routing of messages decouples the implementation of a service from its
interface.  The user configures the routing of general messages to their
taste, so e.g. files are opened in a specific editor, browser, etc.

Furthermore applications can expose their services via this message bus,
enabling interaction apart from their usual UI and instead focussing on
exposing their functionality to other agents.

In a sense the shell and wrapper commands line `sendmail` share the same
philosophy as the distribution, or the user, decides which program
actually carries out the function of sending an email.

## Pragmatic vs. perfect

Since the one true environment won't exist, pragmatism dictates that
reusing existing infrastructure and tools is the best choice if we truly
want to change the computing environment.

## Exposing functionality

Depending on the abstraction level of an application different ways to
expose functionality are advised:

## Network transparency

If applicable multiple systems should be able to talk to each other.
