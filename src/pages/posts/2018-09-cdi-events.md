---
layout: "../../layouts/BlogPost.astro"
title: "CDI Events"
description: "How to use CDI events in Java EE"
publishDate: "03 Sep 2018"
categories: 
  - "cdi"
---

The CDI events mechanism in Java EE is a very simple and useful approach to the Observer-Observable pattern. We **fire** an event and there's a method that **observes** and acts on it.

For example, when we get a new resource with POST in a REST endpoint, we can fire an event with the object and then the service will persist it and the logger log it. So without explicitly calling the persist and log methods, they're executed because the event is fired.

# Firing an event

To fire an event, we simply inject an **Event<T>** and then call the **fire()** method.

```
@Path("messages")
public class MessageResource implements Serializable {

    @Inject
    private Event<String> messageEvent;

    @POST
    public void create(Message message) {
        messageEvent.fire(message);
    }
}
``

# Listening for an event

The class that listens for the event, will have a method with an object argument annotated with **@Observes**.

```
@Named
@ApplicationScoped
public class MessageObserver {

    private void addToMessages(@Observes Message message) {
        createdMessages.add(message);
    }
}
```

Of course we can have many observers listening for the same event.

Events is a great way of loosely coupling an application's components, we can make whatever changes to the program without breaking the functionality.
