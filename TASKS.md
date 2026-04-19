# Language Tasks
The project works towards milestones. Milestones have a scope, though it isn't always formally declared. Once a milestone is completed:

1. All tasks are completed for a milestone
2. PR has been created for merge to main.
3. PR has been approved.
4. PR has been squashed and merged to main both remotely and locally.
5. Delete and create a new "working" branch.
6. Archive the merged milestone and activate the next one.

## Milestones

### Milestone 1.2: More revisions to rust.qmd

- [ ] Move `## Macros` — currently sits between The Basics and Memory Management; consider folding the common-macros table into The Basics or moving it near Cargo/tooling
- [ ] Merge `## Generics and Trait Bounds` into `## Structs, Enums, and Traits` — traits without generics are only half the story
- [ ] Add `use` keyword and namespacing — `use`, `use as`, glob imports, `pub use` re-exports
- [ ] Add `impl` blocks — associated functions vs methods (`new`, factory methods, `self`/`&self`/`&mut self`) with explicit treatment
- [ ] Expand `HashMap` — add `.contains_key()`, `.remove()`, iteration, and working methods
- [ ] Add `BTreeMap` and `BTreeSet` — sorted alternatives to `HashMap`/`HashSet`
- [ ] Add `regex` crate to `## crates`

## Archive

### Milestone 1.1: Revisions to rust.qmd.
- [x] Merge "Errors as Values" and "Error Handling" into one section
- [x] Add Tuples to The Basics > Types
- [x] Add a Concurrency section (`std::thread`, `Mutex<T>`, `Arc<Mutex<T>>`)
- [x] Expand Iterators with adapter chain (`map`, `filter`, `flat_map`, `fold`, `enumerate`, `zip`, `chain`, `take`, `skip`)
- [x] Add `HashSet` to Collections
- [x] Add `Display` and `Debug` trait impl coverage
- [x] ~~Add key `String` and `Vec` methods~~ — completed
- [x] Add `Fn`, `FnMut`, `FnOnce` closure trait coverage
