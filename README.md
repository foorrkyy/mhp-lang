The Mallow Programming Language

Note: Mallow is currently an early-stage concept and experimental language design. Things are actively evolving, syntax might change, and the compiler is still being pieced together. Keep an eye on the docs for the latest ideas!

No Magic, Only Logic.

Mallow is a general-purpose, compiled programming language heavily focused on server-side and web development. It originally started out as MHP (Marshmallow Hypertext Preprocessor)—an attempt to build a "sweeter," cleaner version of PHP—before evolving into its own thing.

Inspired by PHP, Rust, and JavaScript, Mallow aims to give you the easy web-embedding ergonomics of PHP with the memory safety, performance, and logical predictability of a low-level compiled language.

Core Ideas & Philosophy

Everything is a Container: No traditional OOP, no classes, no bloated boilerplate. Data, scopes, functions, and even data types are built around unified, immutable-by-default containers.

No Magic, Only Logic: Hidden runtime behaviors and opaque abstractions are avoided. Functions are pure by default (side effects require an explicit impure marker), and mutability must be explicitly opted into with mut.

Ownership & Borrowing: Inspired by Rust, Mallow prevents unnecessary memory copying and accidental mutations by enforcing strict ownership and read-only reference rules at compile time.

Right-to-Left "Bubble" Evaluation: Operators and keywords act as functions (called Qualifiers) that take parameters from both sides and evaluate linearly from right to left.

First-Class Web Embedding: Write standalone CLI tools or embed Mallow directly into HTML using <# ... #> tags, served natively through the Campfire runtime.

Zero-Cost Options (some / none): No heavy try/catch stack unwinding. Mallow uses built-in opt handling (some and none) to propagate missing values cleanly.

What Does It Look Like?

Hello World (CLI)

default impure fn main {
    print "Hello, terminal!";
}


Embedded Web (MHP / Campfire)

<!DOCTYPE html>
<html>
  <head>
    <title>Mallow on the Web</title>
  </head>
  <body>
    <# 
      name = "World";
      echo "Hello, " + name + "!"; 
    #>

    <!-- Or using the shorthand tag -->
    <p><#= "Sweet and simple." #></p>
  </body>
</html>


Containers & Pure Functions

-- Variables (containers) are immutable by default
user = {
    name = "Clara";
    mut age = 24;
};

-- Functions are pure by default; whitespace separates arguments
fn greet personName {
    print "Hey there, " + personName + "!";
}

default impure fn main {
    greet user.name;
}


Arrays & Zero-Cost Preloading

mut items = ["apple", "banana", "cherry"];

-- Preload adds elements to negative indices without shifting the whole array in memory
items.preload ["first", "second"];

print items[-1]; -- "second"
print items[0];  -- "apple"


The Mallow Ecosystem (Planned & In-Progress)

Zagros Engine: The core compiler architecture, designed around modular assembly primitives and in-memory instruction threading for portability and speed.

Campfire: The official web server runtime written in Mallow itself, built to parse .mhp files and handle routing out of the box.

Ember: The official package manager and build tool (ember.mon configuration).

sugarPack: An optional framework that relaxes some of Mallow's stricter rules (like mandatory main functions and strict purity) for rapid prototyping and beginner-friendly scripting.

SUIT & hawkTUI: Built-in toolkits for native GUI and terminal user interfaces.

Project Status & Roadmap

Right now, Mallow is primarily a language specification and architectural sandbox.

[x] Core syntax and container model design

[x] Ownership, borrowing, and some/none option semantics

[x] Campfire & MHP web embedding specs

[ ] Zagros Engine compiler implementation (bootstrapping phase)

[ ] Standard library core containers (Math, SGML, OS, Neuron)

[ ] Ember package manager CLI

(Note: Installation commands and CLI tools mentioned in the design docs are part of the target specification and aren't live on package registries yet!)

Contributing & Feedback

Since this is an early-stage project, feedback, critiques, and weird ideas are more than welcome. Feel free to open an issue to discuss language design, point out edge cases, or share thoughts on the docs.

License

Mallow is released under the Marshmallow License (MML-1.0) — Soft by nature, sweet by spirit, free by design.

See the LICENSE file for the full details (and don't forget to listen to phonk while coding).
