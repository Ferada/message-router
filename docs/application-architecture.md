# -*- mode: markdown; -*-
# vim: set ft=markdown:tw=72:

# (G)UI and application architecture

Since "the perfect" environment won't exist, let's be pragmatic with the
current situation.  Reinventing all of Unix or BSD userspace isn't
feasible, so even though Plan9 has the right ideas, Lisp Machines won't
happen.  Which is to say, it's a better use of resources to integrate
with the current model instead of a strong case of NIH.

That said, most of current GUI driven programs don't integrate very well
even in the Unix kind of way.  The number of programs which work well
with external tools is rather limited, so every desktop environment
replicates the same kind of tools instead of reducing the amount of
duplication.  Users are then at the mercy of library and framework
writers since interfaces can change rather rapidly *and* are tightly
integrated with the application itself.

This trend includes basics such as file choosers, file associations, the
window manager, the favourite IPC and RPC library, configuration
locations.  The list goes on and on.

Unfortunately the `plumber` functionality from Plan9 hasn't (yet) found
its way into the hearts of power users let alone mainstream computing.
Given such a generalized and very fitting tool to mediate between a
number of applications it seems strange that every community has their
own way of doing essentially the same thing.

## Manifest

- Expose data to the outside environment.
- Let outside actors invoke functionality.
- Simplistic API, UTF-8 encoded text in files, callable scripts.
- Develop towards interfaces.
- Factor common functionality.
- File system as database (even using FUSE).

A protocol to connect multiple applications should be so simple that no
FFI is necessary to interact with it and an implementation is ideally
possible just by reading and writing from, say, a (named) pipe.
Creation of control files etc. could then be handled by a separate
daemon, similar to how a inetd works, or DBus, modulo the more complex
protocol.

## Characteristics of programs

1. Filter, processes some input (file) and outputs some results (sed,
   wc).
2. Daemon, non-interactive long-term process.
3. Interactive UI program, most complex and in many cases highly
   specific to the task at hand (Firefox, GIMP, Open Office, but also
   vim, emacs, irssi, slrn).

## Examples

- Calendar, email, typical PIM stuff.
- Cookie storage, let multiple browsers share cookies.
- Browser tabs as files.
