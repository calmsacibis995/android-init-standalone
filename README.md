# Android Init Language

The Android Init Language consists of four broad classes of statements,
which are Actions, Commands, Services, and Options.

All of these are line-oriented, consisting of tokens separated by
whitespace.  The c-style backslash escapes may be used to insert
whitespace into a token.  Double quotes may also be used to prevent
whitespace from breaking text into multiple tokens.  The backslash,
when it is the last character on a line, may be used for line-folding.

Lines which start with a # (leading whitespace allowed) are comments.

Actions and Services implicitly declare a new section.  All commands
or options belong to the section most recently declared.  Commands
or options before the first section are ignored.

Actions and Services have unique names.  If a second Action or Service
is declared with the same name as an existing one, it is ignored as

## Actions
Actions are named sequences of commands.  Actions have a trigger which
is used to determine when the action should occur.  When an event
occurs which matches an action's trigger, that action is added to
the tail of a to-be-executed queue (unless it is already on the
queue).

Each action in the queue is dequeued in sequence and each command in
that action is executed in sequence.  Init handles other activities
(device creation/destruction, property setting, process restarting)
"between" the execution of the commands in activities.

Actions take the form of:

`on <trigger>
	<command>
	<command>
	<command>`

## Services
Services are programs which init launches and (optionally) restarts
when they exit.  Services take the form of:

`service <name> <pathname> [ <argument> ]*
	<option>
	<option>
	...`


