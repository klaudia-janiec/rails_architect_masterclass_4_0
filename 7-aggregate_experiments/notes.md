# Week 7 Notes

## Classic aggregate root
- State, business logic, events are together in one aggregate root.
- `unpublished_events` exposed to public.

## Extracted state
- State is data structure passed to aggregate initializer.
- Changes exposed.

## Functional aggregate
- Extracted more than extracted state.
- State passed to individual actions.

## Query based aggregate
- No apply method.
- No returning events.

## Polymorphic aggregate
- Map logic almost 1 to 1.
- Raise error if method not possible.

## Duck typing
- Similar to polymorphic.
- Based on `respond_to?` method.
