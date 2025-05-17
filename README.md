# mhp-lang
Proposed general purpose minimal programming language.

# MHP — Marshmallow Hypertext Preprocessor 🍡

> A programming language with no magic — just logic.  
> Sweet like PHP, sharp like Rust, readable like Python, powerful like C.

---

## 💡 What is MHP?

**MHP (Marshmallow Hypertext Preprocessor)** is a modern programming language designed from scratch to be:

- **Minimal but expressive**  
- **Type-safe but flexible**  
- **Compiled (via LLVM)**  
- **Extensible, embeddable, and developer-friendly**

Originally inspired as a sweeter alternative to PHP for server-side development, MHP evolved into a full general-purpose language — suitable for web, backend, CLI, and even system-level programming.

You can write:
- Dynamic web apps (`Campfire`)
- UI frameworks (`SUIT`)
- Game logic, physics, and even editors (like Mim — MHP's Vim clone)

---

## 🧠 Philosophy

> 🔒 Everything is a container.  
> 🧩 Functions are executable containers.  
> 🚫 No classes. No OOP bloat.  
> 📜 Syntax is readable, logic is predictable.  
> 🧃 Code should taste good.

MHP is built around clarity and trust: you see what you get. No hidden behavior, no "it depends" operators, and no undefined weirdness like `null == false`.

---

## ✨ Killer Features

✅ **Clean syntax:**
```mhp
mut a = 5;
if a < 10 {
    print "Sweet!";
}
