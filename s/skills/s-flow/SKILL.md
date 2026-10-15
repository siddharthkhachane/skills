---
name: s-flow
description: Trace how a specific piece of data flows through the system - entry, transforms, storage, reads - and flag duplication.
argument-hint: <data, e.g. a user's email address>
disable-model-invocation: true
---

Trace how this data flows through this entire system: $ARGUMENTS

Start from every point it can be created or entered, signup form, API import, admin panel, and follow it through every transformation, validation, storage location, and place it gets read or displayed again. Present this as an ordered sequence of steps with file and function references at each step, not just a list of files that mention it. Flag any place the data is duplicated, cached, or stored in more than one location, since that is where inconsistency bugs usually live.
