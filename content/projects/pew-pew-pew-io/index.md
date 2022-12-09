---
title: "Pew-Pew-Pew.io Game"
summary: "About a year ago, I was just starting to learn Node.js. During that..."
date: 2018-04-29
featured_image: "images/demo.gif"
draft: false
---

## **Overview**

About a year ago, I was just starting to learn Node.js. During that time, I heard about Socket.io, a Node.js package used for real-time, client/server messaging. After experimenting with it for a bit, I was curious to see if it could be used to create an online multiplayer game.

With the hype surrounding many .io games at the time, such as sither.io and agar.io, I wanted to see if I could create a multiplayer game with similar gameplay, using socket.io.

All code for this project can be found on my [GitHub repo](https://github.com/mtfuller/pew-pew-pew.io).

## **Architecture and Design**

Before jumping into coding, I took a good amount of time to experiment and research different approaches I could take. The game server uses both socket.io and express.js to communicate with clients. I used socket.io to continuously send game data to each client.

![https://raw.githubusercontent.com/mtfuller/pew-pew-pew.io/master/docs/img/architecture.png](https://raw.githubusercontent.com/mtfuller/pew-pew-pew.io/master/docs/img/architecture.png)

Each client, once connected to the socket.io server, sends the player's input to the server, in order change the direction of the ship or trigger the ship’s weapon.

## **Entity Component System**

The first major design hurdle I encountered was to figure out the best way to structure the game logic. I was familiar with a few basic game design patterns, such as a game loop. However, I was lost on how to effectively manage things like updating game object positions, detect collisions, keep track of scores, remove dead players, etc.

I started researching different game design architecture styles. I eventually came across one pattern, known as an Entity Component System (ECS). This design approach allows properties of a game object to be decoupled from each other. Allowing more flexibility, but by adding more complexity.

Robert Nystrom, the author of “Game Programming Patterns” (2014), wrote [a very interesting blog post](http://gameprogrammingpatterns.com/component.html) that outlines this approach.

## **Spatial Hashing**

Another big question that I had during my design phase was: “what's the best way to check if two ships are colliding with each other?” It seems like a straight-forward problem. To check if two ships are colliding, you would just calculate the Euclidean distance between two ships (using each ship's x-y pair).

If the distance falls under a certain threashold, like the sum of the ships' radii, then the ships have collided. If we wanted to find all collisions for a given set of ships, then we might approach it like this:

![https://raw.githubusercontent.com/mtfuller/pew-pew-pew.io/master/docs/img/brute_force.png](https://raw.githubusercontent.com/mtfuller/pew-pew-pew.io/master/docs/img/brute_force.png)

In a brute force approach, we take one ship, and then perform a collision check on every other ship in the game. Next, we move on to the next ship, and so on. As you might imagine, there’s a lot of collision checking going on.

This may not be a problem with a small number of ships, but as the number of players increases, collision checking can become expensive. But, what can we do? How could we be more conservative with our collision checking? I wasn’t really sure myself at the time. Intuitively, I knew I needed to partition the board, but I wasn’t sure how.

One common approach to efficiently perform collision checking is to use something called, "spatial hashing". Spatial hashing is the process of partitioning the whole board into many “buckets”. Next, each entity’s x-y coordinates are hashed to get a key. This key then determines which bucket the entity belongs to.

![https://raw.githubusercontent.com/mtfuller/pew-pew-pew.io/master/docs/img/spatial_hashing.png](https://raw.githubusercontent.com/mtfuller/pew-pew-pew.io/master/docs/img/spatial_hashing.png)

By placing each entity into a bucket, now we only perform collision detection on entities in nearby buckets. If two buckets are far away from each other, there is no need to if their entities have collided. So, by only checking entities in nearby buckets, we can avoid a lot of pointless collision checking.

## **Final Words**

Overall, I was pleased by the final product. Socket.io was surprisingly easy to work with, and I feel that this project presents a good proof of concept for a simple, browser-based multiplayer game. I feel like I gained a broader understanding and appreciation of the different design and optimization styles used in game engines.
