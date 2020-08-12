# Week 3 Notes

## Bounded contexts

Bounded context parts:
- **Data**. Bounded context is an owner of data. It changes it and exposes.
- **Code**. Code in one bounded context _should not_ directly read data from other bounded context.

Comunication between bounded contexts should be formalized.

## Domain events

Domain event is an interface to communicate between bounded contexts. When something happens in one bounded context there is domain event emitted. If there is other bounded context insterested in particular event it consumes it and whatever it needs it stores in its own data.

## Event sourcing

Restore the current state from changes rather than storing the current state. Read model used for reading.

## CQRS

Separate read and write models. Write model - domain model (?).

## www.railseventstore.org/new
```
rails new -m www.railseventstore.org/new app_name
```
