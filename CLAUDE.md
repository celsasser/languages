# Language Notes Project

## Project Purpose

This is a Quarto-based textbook/reference notebook project covering the history, design, and practical use of computer languages. The notebooks are written for readers with systems programming background (C/C++), explaining each language through the lens of design decisions and tradeoffs rather than just syntax.

## My Role

I am an expert in computer language history, design, and theory. I understand why languages make the design decisions they do: the tradeoffs, the constraints, the influences. I write textbook-quality notes that are accurate, clear, and honest about both strengths and weaknesses. When explaining a concept, I connect it to what the reader already knows rather than teaching in a vacuum.

## Notebooks

### `index.qmd` — Introduction: A History of Computer Languages (180 lines)
The framing document. Covers the mathematical and theoretical roots (Leibniz, Boole, Babbage/Lovelace, Church, Turing, von Neumann), the generations of languages (machine code through high-level), the great schisms (structured programming, OOP, functional), the safety problem, and why Rust represents a synthesis. Sets the intellectual context for all the other notebooks.

### `rust.qmd` — Rust for C/C++ Programmers (5,425 lines)
**Subtitle:** "A practical bridge to Rust's fundamentals"
**Audience:** Experienced C/C++ programmers. Explanations anchor to C/C++ equivalents (ownership vs. RAII, `&str` vs. `std::string_view`, modules vs. namespaces, etc.).

Topics covered:
- Why Rust exists; core design decisions (ownership, borrowing, fearless concurrency, zero-cost abstractions, explicit-over-implicit)
- Project anatomy: packages, crates, modules, visibility, `pub use`, external dependencies
- The Basics: operators (full precedence table), variables, types (scalar, tuples, fixed arrays, strings/`&str`, slices, conversions), functions, control flow
- `Option<T>`: extraction, combinators (`.map`, `.and_then`, `.filter`, `.ok_or`), `if let`, `?`
- Macros: declarative (`macro_rules!`), procedural (derive/attribute/function-like), conditional compilation, formatting (`println!`/`format!` specifiers)
- Memory management: stack vs. heap, ownership rules, borrowing, lifetime annotations, common lifetime patterns
- Structs, enums, traits (including `Display`/`Debug`)
- Generics and trait bounds; `impl Trait` vs `dyn Trait`
- Pattern matching: `match`, destructuring, guards, `@` bindings, `if let`, `while let`
- Error handling: `Result<T, E>`, the `?` operator, the `Error` trait, error formatting
- Collections: `Vec<T>`, `HashMap<K, V>`, `HashSet<T>`
- Closures and iterators: `Fn`/`FnMut`/`FnOnce`, adapter chains, terminal operations
- Smart pointers: `Box<T>`, `Rc<T>`, `Arc<T>`
- File I/O: buffered/unbuffered, binary I/O and byte order, error handling
- Concurrency: threads, `Mutex<T>`, `Arc<Mutex<T>>`, message-passing channels
- Cargo: `Cargo.toml` in full, editions, dependency version constraints, feature flags, build profiles, environment variables
- External crates: `clap` (full derive API: `Parser`, `command`, `arg`, subcommands, multiple values)
- Key differences from C/C++; where to go next

### `c.qmd` — The C Language (1,651 lines)
Focused heavily on embedded/DSP contexts (dsPIC, real-time systems). Topics covered:
- The 32 keywords, standard library overview
- Compiler and linker stages: preprocessing (conditional compilation, stringification, token pasting, variadic macros, include guards), compilation (compiler attributes), linking
- Language features: pointers, arrays vs. pointers (the fundamental truth), pointer arithmetic for DSP, structures, unions, `const`/`static`, function pointers, memory management, bitwise operations
- The build system: Make, compiler optimization levels, `volatile`
- DSP features: fixed-point arithmetic, DSP extensions/intrinsics, circular buffers, DSP library
- Common pitfalls: integer promotion, operator precedence, uninitialized variables, buffer overruns, off-by-one errors, macro side effects, undefined behavior
- Interrupts: ISR anatomy, `volatile` for shared state, flag-based patterns, atomic operations, common interrupt patterns (timer RTC, ADC acquisition), common pitfalls
- Embedded C idioms: state machines, ring buffers, bit fields for hardware registers

### `assembly.qmd` — The Assembly Language (1,057 lines)
**Subtitle:** "Direct Hardware Control for DSP Applications"
Targets the dsPIC33F architecture. Topics covered:
- dsPIC33F architecture: register file, DSP accumulators, program counter, status register
- Instruction format and operands
- Assembly directives
- Data movement: `MOV`, `PUSH`/`POP`
- Arithmetic and logical: basic arithmetic, bitwise operations, comparison
- Control flow: unconditional/conditional branches, subroutine calls, labels
- Loops: manual counter, hardware loop, `REPEAT`
- Addressing modes: immediate, register direct, register indirect (with post/pre-increment, displacement), bit-reversed, modulo
- DSP-specific: `MAC`, extended precision, accumulator instructions
- Complete example: FIR filter in C vs. assembly with performance comparison and breakdown
- C vs. assembly comparison; calling convention (dsPIC C ABI)
- Common assembly patterns: delay loop, table lookup, clear memory block
- Reading disassembly; debugging tips; the assembly toolchain

### `python.qmd` — Python (2,132 lines)
**Subtitle:** "A practical introduction for systems programmers"
**Audience:** Readers coming from C/Rust; explanations lean on that background.

Topics covered:
- Why Python exists; core design decisions (readability, batteries included, duck typing, GIL tradeoffs)
- Project structure: modules, packages, virtual environments
- The Basics: variables and types, type hints (annotations, containers, Optional, Union, Any, Callable, TypeVar, Protocol, Final/Literal), functions, control flow, comprehensions (list/dict/set/generator, nested), unpacking/destructuring, walrus operator
- Reference semantics and memory: heap objects, reference vs. value copy, mutable vs. immutable, shallow/deep copy, identity vs. equality, interning, list memory allocation, dict/set internals, reference counting and GC, the GIL, memory-efficient patterns
- Data structures: `list`, `tuple`, `dict`, `set`, `str`
- Functions and closures: first-class functions, closures, decorators
- Classes and objects: dunder methods (string repr, operator overloading, container/iteration protocols, `__call__`, `__bool__`, context managers), `@property`/`@classmethod`/`@staticmethod`, inheritance, `super()` and MRO, no access control, dataclasses
- Error handling; context managers
- Concurrency: `async`/`await` (gather, tasks, `async with`/`async for`, propagation), threads, processes, choosing a model
- Performance: dynamic dispatch cost, what helps vs. hurts, interfacing with C and Rust, efficient iteration
- Standard library: `pathlib`, `collections` (Counter, defaultdict, namedtuple, deque), `functools` (lru_cache, partial, reduce, total_ordering, wraps)
- The ecosystem; key differences from C and Rust; where to go next

### `b-pyperf.qmd` — Python Performance Analysis (163 lines)
An academic-style paper. Covers CPython internals, bytecode/PVM, dynamic typing overhead, the GIL (design rationale, performance implications, workarounds), memory management (reference counting, allocation strategies), C extensions (C API, ctypes/cffi, Cython, pybind11), optimization strategies, comparative performance vs. compiled languages, alternative Python implementations.

### `css.qmd` — CSS (1,001 lines)
Topics covered:
- The design of CSS; the cascade; inheritance
- Selectors: type, universal, class, ID, attribute; combinators (descendant, child, adjacent sibling, general sibling); pseudo-classes (user action, link states, structural, form/input, logical, other); pseudo-elements; specificity
- Element types and the box model: display model (block, inline, inline-block, replaced elements, `display` property), box model, `box-sizing`, margin collapse
- Positioning: relative, absolute, fixed, sticky, `z-index`/stacking order
- Layout: Flexbox (concepts, container properties, item properties), CSS Grid (defining the grid, placing items, named areas, auto-placement)
- Drawing: borders, border radius, outline, backgrounds (color, image), gradients (linear, radial, conic, repeating, multiple), box shadow

### `glossary.qmd` — Glossary (669 lines)
Hardware and DSP terms with detailed explanations: BSS segment, circular buffer, comparator, fixed-point numbers, floating-point numbers, MAC (multiply-accumulate), multiplexer, parallel interface, register, saturate, serial interface, UART.

## Writing Style

- Explanations are direct and grounded. No hand-waving.
- Code examples are idiomatic for the language in question, with inline comments only where a non-obvious subtlety needs calling out.
- Cross-language comparisons are used freely to build intuition (e.g., Rust `match` vs. C `switch`, Python GC vs. Rust ownership).
- Callouts (`.callout-note`, `.callout-warning`) are used for important caveats, not decoration.
- `.exploration` divs are used for longer excerpts or deep dives.
- `.subheading` divs provide a brief orienting phrase below a heading.
- `.see-more` divs link out to authoritative references.
- Sections use `##` for major topics, `###` for subtopics, `####` for details.
- Tables are used for quick references, type comparisons, and analogy maps.

## Quarto / Document Conventions

- Diagrams: use Mermaid for structural/conceptual diagrams, image placeholders for complex visuals, Python/matplotlib only for data-driven plots.
- Internal cross-references use `[text](#anchor)` style.
- External links open in a new tab: `{target="_blank" rel="noopener noreferrer"}`.
- Images live in the `images/` directory with kebab-case filenames.

## What to Do When Adding Content

1. Match the existing tone: authoritative but approachable, grounded in first principles.
2. Always explain the *why* behind a design decision, not just the *what*.
3. Anchor concepts to what the reader already knows from C/C++ or whatever language is most analogous.
4. Include a working code example for every non-trivial concept.
5. Add a quick-reference table when a concept has many variants (e.g., trait bounds, formatting specifiers, CSS selectors).
6. Use callouts for gotchas that would bite a programmer coming from a different language.
