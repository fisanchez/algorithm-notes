---
title: Rails 7 Front End Tooling
author: Noel Rappin (@noelrap)
---

## Webpack 
Pretty complicated.

## Rails 7 Strategies

Propshaft
- Get your stuff to a known directory
- Will serve it
- Deosn't do much on it's own

Bundling
- esbuild, rollbar, webpack, tailwind, sass
- thin wrappers, with watch tasks that look for changes and places it where proptask can find it

Pros
- flexbile
- simpler

Cons
- Doesn't help with complex js builds

## What if you didn't need to bundle

**Import maps**
Logical name of module -> URL of module

**Why bundle**
- One HTTP request rather than many
- Handles where to look

**In HTTP/2**
- No real penalty for many HTTP requests

## Talk
**Turboframes**
Able to change view in line. 
What it's actually doing - 
stimulus hanldes these changes through a change observer

## Idea

Give a rough presentation of his talk
- Show casing turboframe
- Using stimulus controller as a data-action



## Questions
- Which to use?
Import map is good when you have simple js

Kredis

For hotewire - the server is the source of truth
Hotwire is generic term for hotwire and stimulus

## Notes
- RailsConf_May2022 discount code
- Fork app
- nova app