# Week 2 Homework

## Value objects
> **Value object** - object which keeps immutable value which is comparable. Does not have identity. For example money object (number + currency). Can protect very simple business rules (eg. number can't be negative in money).

- Money (number + currency)
- Phone (eg. area code + phone number)
- Vat rate
- Fee

## Entities
> **Entity** - domain object with unique identity and mutable state.
- Package
- Order
- Payment

## Aggregates
> **Aggregate** - composed domain objects. Root of object hierarchy is and aggregate root.
- User
- Courier
- Invoice
