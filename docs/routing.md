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

# Protocol

The protocol is message based.  Messages can be send on a stream or datagram
based transport.  Each message has a maximum size of FOO octets.

The following format describes every message:

    size 123
    [data with 123 octets]

Every header line is delimited by a newline character.  The only whitespace
characters are space and newline.

`size` starts the data section.  Programs should format their data based on the
same rules as the core protocol.

Each node in the network runs a message router and may expose some of the
services to the network.  Service discovery is a separate service and may be
queried using the appropriate protocol.

    from macrolet.net
    from zsh+456
    to straylight
    to open
    size 26
    file macrolet.net:test.md

The request above asks the machine at straylight to open the file on the
machine macrolet.net in the home directory of the authenticated user.  This
means that the user has to have an account on both systems and that pathname
translation / mounting of the foreign filesystem is enabled to retrieve
respectively edit the correct file.
