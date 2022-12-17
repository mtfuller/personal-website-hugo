---
title: "Systems Thinking: Part 1 - What is a system?"
summary: "..."
keywords: []
date: 2023-01-02
featured_image: "images/splash.jpg"
draft: true
---

# What is Systems Thinking?

As a software developer, I'm well acquainted with complex software with numerous interconnected parts. In our industry, it's quite common to stumble across a code base that isn't just complicated, but is confusing and thrown together. Deadlines, pushes, and the need to get features and fixes out to customers pressure devs to find something that's working and go.

I wondered if this was just our industry. Sometimes we are handed poorly, hacked-together projects, and the business expects us to move tickets across the board. We don't really have a choice, but to do our best with our constraints.

As a new developer, any time I tried to ask questions about how it worked or what the architecture looked like, I was met with vague box diagrams and responses like, "you don't need to know every part of the system, just debug to fix the issue".

I feel lost and wondered if it was just me. Were we just sentenced to a career of bouncing from job to job, understanding a software system just enough to complete a ticket. It's disheartening when you see seniors with decades more experience than you become terrified at the thought of modifying anything in a particular class. It makes you wonder if anyone really understands anything, or is it really just all for show.

## Everything is a System

I came across terms that made me curious: "systems thinking", "general systems theory", etc. I remember a year or so ago stumbling in the term, “general systems theory”. What I found was a school of thought around the idea that one can break anything that exists into a collection of components, each interacting with each other to provide a function or purpose.

As I explored more, I discovered there were several academics from MIT and beyond that have outlined and identified principles of life that exist in multiple disciplines and industries: ecology, economics, physics, business, supply chain, etc.

In Donella's book, *Thinking in Systems*, she offers a glimpse into a framework for breaking the complexities of life into models. Models that can be understood and applied. As I started reading, I began asking the question, "can this be applied to the software industry?" After all, the economics and supply chain of a paper mill seem more involved then your average ToDo app on your phone.

Everything can be modeled as a system: a human cell, a car dealership, a football team, a tree in a forest. In abstract terms, a system is nothing more than a context of components that work together to accomplish some function.

### What is a System?

Donella explores the abstract definition of a system, and breaks down three major constructs:

- **Components**: The individual elements of a system.
- **Interactions**: The ways components communicate and respond to each other.
- **Function**: The goal or purpose that all the elements are working towards.

She notes one major principle. We can change any construct of the system. It’s easy to change components, for example subbing a player out on the football team. That change will be the lease invasive change and will do little to break the system.

As we go up the chain, if we change the way the components interact, we will disrupt the system even more.

Finally, changing the function of the system will result in the…

### How does this relate to Software?

This general systems framework for thinking can easily be applied to software, as well. Let’s take a look at a simple team messaging app.

What are the components of the system? Well, simply put it is all the services and the database it’s connecting to. Each it a unique part of the system, that accomplishes a part of the function.

Next, what are the interactions. Obviously, the dependencies between the services, in which services will communicate to read or write data.

What’s the function of the system? The goal of the application is to allow users to send messages to other users. In the software industry, we typically call the function of a software system a “use case”.

### Final Words

In the next post, we’ll be taking a look at Donella’s framework for modeling systems, as well as some common types of systems.