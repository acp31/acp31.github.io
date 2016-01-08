---
layout: post
title:  Messing with Redux
date:   2015-12-10
categories: Projects
---

So for the past few weeks I've been trying to learn Redux. I have made steady progress and I think that I am just starting to get it. Redux is a small librabry that manages the entire application state.
Even More awesome is that Redux uses an immutable object to do so. That means that the object cannot be mutated. This is helpful becuase it means that the entire application state can be traversed backwards.
In redux the entire application state is held in a container called a store. The store can dispatch
functions called actions which get sent from the store to a large reducer which reduces the state 
down. That was kinda jumbled so i'll try to explain it in another way. 
  Think of Redux as a contractor for your application. You call up Redux becuase you need 
help managing things and Redux tells you it can manage the state of your application and 
will make it easy to scale you application. So Redux statrs by looking through your code and 
figuring out how it works. It then documents everyaction that your application can make and 
give them all names. Redux then makes a reducer that will reduce your application state down
to the current state based on the expected changes. Redux then goes back and sets up functions to 
make all of those actions possible. Redux makes sure that the action functions are the only things 
to handle the data in your application so the state is more predictable. Finally Redux sets up a 
store which is a storage container that will hold the application state. Redux also says that only
the store call dispatch action which means only the store can tell the application what to do. 

I hopes that helped you understand what Redux does and how it does it! 

