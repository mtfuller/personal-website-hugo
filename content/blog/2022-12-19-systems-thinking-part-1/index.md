---
title: "Systems Thinking: Part 1 - What is a System?"
summary: "In my early career as a software engineer, I remember being introduced to a few"
keywords: ["systems thinking", "Donella Meadows", "software development", "architecture", "design", "components"]
date: 2022-12-19
featured_image: "images/splash.jpg"
draft: false
---

In my early career as a software engineer, I remember being introduced to a few large, complicated codebases. These codebases, as I found out, were much more complex than any class project we had to create in school. Most notably, I was surprised that it was very difficult to understand how each project worked. It appeared as just a big blob of code. Nothing seemed familiar. 

The more surprising thing I found was that mature engineers on my team had a lot of trouble explaining the low-level details of the codebase. As I tried to understand the entire flow of the application, I was met with high-level explanations and advice saying, “You don’t need to know everything, just enough to debug and complete the tickets.”

It sounded like practical advice, but I felt unsatisfied with the approach of just keeping my head down and doing my work, and I wondered if it was just me. I found it alarming that, at the same time, the more experienced engineers were terrified at the thought of changing particular parts of the codebase. It indicated the code was brittle and very costly to change. To my surprise, the folks that had spent the most time with the codebase were at the mercy of its complexity.

At the end of the day, the business wants engineers to deliver. If a team of engineers is not able to understand how the components of a codebase work together, then it makes it really difficult to make strategic decisions. In my short career, I’ve seen development slow down almost to a halt when codebases become black boxes. 

I recently came across a term that offers a solution for this rampant problem: "systems thinking." What I found was a school of thought around the idea that one could break anything in our universe into a collection of components, each interacting with each other to provide a function or purpose.

## Everything is a System

As I explored more, I discovered there were several academics from MIT and beyond who have used systems thinking, outlining principles of life that exist in multiple disciplines and industries: ecology, economics, physics, business, supply chain, etc. One environmental scientist, Donella Meadows, actually wrote an introductory book on the topic, called *Thinking in Systems*.

In Meadows's book, she offers a glimpse into a framework for breaking the complexities of life into models that can be understood and used to make real-world decisions. Meadows presents the idea that everything can be modeled as a system: a human cell, a car dealership, a tree in a forest, or even a football team. In abstract terms, a system is nothing more than a set of components that work together to accomplish some function.

## What is a System?

Meadows explores the abstract definition of a system, and outlines three major constructs:

- **Components**: The individual elements of a system.
- **Interactions**: The ways components communicate and respond to each other.
- **Function**: The goal or purpose that all the elements are working towards.

Here, she notes one major principle: while we can change any of the things listed above in a system, the **cost** of change is different for each construct. 

The components of a system are fairly easy to change. Suppose the system we are modeling is a football team. The components of the team would be the individual players. So, if we wanted to change one of the components for another, we would just substitute one player for another on the bench. To improve the team, changing players on the field has a very low cost. It’s very unlikely to break the system by only changing a component (player).

However, what if we go down the list? Suppose we change the interactions. In our football team example, the interactions would be the the plays from the playbook. The playbook details out how players will interact with each other in order to move the ball down the field. The cost of adding a new play mid-game is much higher. A play only works if all players are practiced and know how to follow the play. If players haven’t practiced a play, it has higher risk of failing. This means that a change to the interactions of a system doesn’t come without increased cost.

What if we change the function or purpose of the football game? The purpose of the football game is that both teams compete for the highest score to win the game. Suppose the commissioner announced that the winner of the game would be the team with the lowest points. That would change the very nature of the game. Teams would be performing very differently if that were the case. The game would probably end in a tie, where no team has scored. So the function proves to create the highest risk in the event of a change.

## How Does This Relate to Software?

I believe systems thinking is a great way to model software systems as well. Let’s take a look at a simple team messaging app. Let’s say we have an app that is capable of allowing teams in a company to chat and send messages over “channels” (think Slack, Microsoft Teams, etc.). 

This theoretical application would be designed using three unique elements: a frontend web client, a backend API, and a database instance. These would be the components of the system. Each is a distinct part of the system that handles part of the application’s function or purpose. Let’s say we wanted to change the frontend web client of the system. As long as the interface between the frontend and backend does not change, it would take very little cost to make the change.

What would the interactions be? The dependencies between the frontend, the backend, and the database. The frontend reads and writes data to the backend, while the backend persists state changes to the database. Suppose we wished to update the interactions between the backend and the database, by adding a new column to a table. That would require work to update the schema for both the database as well as the backend API.

Finally, what is the function of the system? The goal of the application is to allow users to send messages to their respective teams through channels. In the software industry, the function of a software system is a set of use cases or features. Suppose we wanted to create a new use case where a user can send a GIF instead of a message. That might require changing the interactions between the entire stack! A development team may need to make changes to the frontend, backend, and database to meet the requirements. The cost of changing a system’s function is much higher than the other two.

The major principle Meadows presents applies here as well. Just like in the football team example, it is much easier to swap out the components (frontend, backend, database) of the system than to change the dependencies (interactions) between the services. It’s also easier to change the dependencies than to add or change a use case (function) of the system. Suppose we considered changing the purpose of the chat app to become a social media app. That would take a lot more effort and incur a lot more risk.

## Final Words

*Thinking in Systems* brings forth a framework for identifying systems in our everyday life. As software engineers, this means the software applications we build in our jobs can be modeled as systems too. In the next post, we’ll be taking a more in-depth look at Meadows’s framework for modeling systems, as well as some common types of systems.