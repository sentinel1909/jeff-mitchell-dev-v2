+++
title = "Projects"
template = "projects.html"
+++

Here are some projects I'm working on or have worked on.

### Backend Development

[Crusty Rustacean Newsletter](https://github.com/sentinel1909/crusty-rustacean-newsletter)

This project is my completed take on [Zero to Production in Rust](https://www.zero2prod.com) by [Luca Palmieri](https://www.lpalmieri.com). I did it using the Axum web framework, instead of Actix Web. I deployed this project, for a time, on Railway, but took it down as I became increasingly nervous about having something less than amateurish exposed to the internet. I'm thinking about getting it going again...on Shuttle.

[Shuttle Template - Axum](https://github.com/sentinel1909/shuttle-template-axum.git)

I'm a fan of using Shuttle's Service trait. It's more flexible and, in my opinion, makes a Shuttle project easier to reason about. I've created an opinionated template and am slowly evolving it as I think of more pieces that are useful to me. Using `cargo-generate` I can spin up a fresh project in no time and be on my way adding the good stuff.

[Shuttle Template - Hyper](https://github.com/sentinel1909/shuttle-hyper-template.git)

I mess about with stuff so that you don't have to. Anyone in their right mind would build their API with Axum (or the other framework of your choice) and call it a day, but not me! I'm going nap-of-earth with Hyper and Tokio, just in case you want to see for yourself what not to do. I've managed to create a skeleton API and have turned it into a template of sorts. It's a mainly a learning ground for me, as I need to get my hands dirty.

[dev-blog-api](https://github.com/sentinel1909/dev-blog-api)

I'm currently exploring [Apache OpenDAL](https://opendal.apache.org/) and it's ability to allow me to leverage Cloudflare R2 storage. I'm building an API for my developer blog, which will eventually serve to power a revised version of my blog. OpenDAL is excellent, and despite an initial learning curve hump, is turning out to be pretty straightforward to use. I have to admit I've bit off a little too much with this project, and it's sort of stalled here as 2024 closes. Will hopefully resume it in a few weeks.

### Frontend Development

[Shuttle Template - Yew](https://github.com/sentinel1909/shuttle-template-yew)

I don't want to be the billionth person learning React. I enjoy front end development with Rust and have been steadily picking up how to do things with [Yew](https://yew.rs). I think, unfortunately, Yew is kinda dead and not being actively developed. Don't let that stop you though, it's mature enough for production and is a viable choice for front end development using Rust and WebAssembly. I've created a template which uses Axum to serve up a Yew frontend site.

### Doing Things with Community Crates

[Fun with Nom](https://github.com/sentinel1909/fun-with-nom.git)

Early in 2024, I developed a wierd obsession with the Nom crate. I tried to using late in 2023 while working through Shuttle's Christas Code Hunt. In typical fashion for me, I was way over my head, running before even crawling. I figured I'd start building out an API that returned the word count of a sentence handed to it. The project is not deployed, but I may yet return to it. There are precious few resources out there for mere mortals on how to use this crate.

### Events and Challenges

[Advent of Code 2024](https://github.com/sentinel1909/aoc2024)

I _tried_ to do Advent of Code this year, in Rust. Didn't make it past Day 2 though.

[Shuttle Christmas Code Hunt 2024](https://github.com/sentinel1909/shuttlings-cch24)

Shuttle's Christmas Code Hunt was loaded with highs and lows. A couple of the challenges I had to look at other people's work, which I'm not exactly proud of. However, on the positive side, I have something to unpack and learn from. I hope this event becomes an annual staple!
