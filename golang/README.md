---
description: Fav
---

# Golang

If you want to know more about Golang, pelase to go the **Golang section on my notes page** [**here**](https://dev117uday.github.io/notes-md/)

The hot new server-side high-performance language.

For those of you who don’t know what Golang is, here is a quick and short intro :

* Go is a statically typed, compiled programming language designed at Google by Robert Griesemer, Rob Pike, and Ken Thompson.
* Go is syntactically similar to C.
* It has memory safety \( uses a garbage collector \), structural typing, and CSP \[communicating sequential processes\]-style concurrency.

In simple words, Golang is like Java in terms of processing but written like C

### Why Golang?

We live in a world where Java handles the majority of critical processes, but the thing is, java is old getting old, in the sense that writing concurrent programs is difficult, as more and more servers are UNIX based, shell scripts to manage servers is limit \(that’s where python came in \), poorly implemented generics and no support for unsigned data-types, has hidden relationship between code and hardware. This is where Golang comes in.

### Why I love Golang

* **Performance**: Golang is compiled to machine code by its compiler, it’s fast, hence faster than java.
* **Modern**: Just like any other modern programming language, Golang’s syntax is relatively easy to understand and write code. It keeps one’s understanding of how memory is used will abstracting out a lot of complex features.
* **It’s static and dynamic**: the concept is simple, if the type isn’t defined it will dynamically adjust, else follow the rules.
* **Safe**: Golang comes with garbage collector which is open-source \(Golang itself is open-source\), turns out to be more reliable, hence no need to worry but memory leaks as the garbage collector is smart enough to free unused memory, though you can do it explicitly but come on.
* **Concurrency**: Golang is known for its great concurrency, but why believe me, here is the explanation simple explanation :

Golang uses something called **Go-routines**, simply they are Go function. Golang implements its own scheduler that allows many Go-routines to run on the same OS thread. JVM on the other hand uses operating system threads, it relies on the operating system kernel to schedule them, which is a much slower and memory consuming process.

You can read more about this topic in detail here :

* [**Why you can have millions of Goroutines but only thousands of Java Threads**](https://rcoh.me/posts/why-you-can-have-a-million-go-routines-but-only-1000-java-threads/)
* [**Achieving concurrency in Go**](https://medium.com/rungo/achieving-concurrency-in-go-3f84cbf870ca)

## Major Other Advantages :

* Cross-compiling: The Go compiler allows you to generate executable binaries for different operating systems with simple commands, and because it is a simple executable file, this makes deploying Go applications to production servers or local machines a breeze — all it requires is moving the final executable file. No hassle that comes with JVM.

### Some concerns regarding Go

Well it’s not all perfect in Go’s world

Now, to be completely honest, I looked into a ton of resources to find drawbacks in go but could find any reasonable ones \(except for package manager\). Consider reading these comments:

`While having interfaces is great, structs implement interfaces implicitly, not explicitly. This is stated as a strength of Go, but we found that it’s difficult to tell from looking at a struct whether or not it implements an interface. You can only really know by attempting to compile the program. This is fine if the program is small, but not if it’s a medium to large size.`

One of Go’s main advantages is also one of its weaknesses. Go may be an easy language to pick up, but that brings with it a lack of versatility. Some of the hottest languages on the market pride themselves on their complexity.

Languages like Swift and Haskell may be more difficult to learn, but they manage to find their fans by packing in a wealth of smart abstractions that allow coders to achieve complex and clever results with less.

Well, the stated disadvantages of Golang are more opinion-based rather than actual setbacks that cause problems.

The Disadvantages are more like design drawbacks which people complain about but Golang says its the part of the new programming language design paradigm.

### Lack of Package Manager

* Golang doesn’t have a package manager \(as of June 2020\). Every single modern programming language has a package manager, not even modern languages, older than Golang like Python and JavaScript have a package manager, even Rust, a systems programming language has one. 

It’s not that you completely cannot use external packages, yes you can, but you have to configure them the old fashion, adding them to the path and explicitly defining, like C++ which is not cool.

Nonetheless, Golang is an amazing programming language. Golang developers are among the highest-paid developer in the industry, it’s also becoming an industry favorite language when it comes to doing real-time data analytics and data science work, deploying production-ready ML models, Yes, you heard \(or read it\) write. It’s best-suited use it to write scalable, high-performance back-end that can you heavy data lifting.

I hope you like this article !

