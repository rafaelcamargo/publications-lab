# Avoiding traps in javascript event-driven programming.

Every developer knows or, at least, should know, the importance of keeping the
code as much decoupled as possible. Decoupling drives your code to smaller
responsibilities and, consequently, granular objects which bring us fast
understanding and easy maintenance. Sometimes, one of the strategies which can
aid you to achieve this is to use events to make those granular objects
communicate each other without necessarily know each other directly.

However, bad implementation of some points of event-driven programming may lead
you to a terrible nightmare when you need to revisit any part of those flows.
Yes, event-driven programming has some traps and into three of them, I have
already fallen.

The first trap could be set when you are naming the event. It should say *what
happened*, not *what must happen*. The component that is publishing some event
should never know anything outside it. The reason is obvious. Decoupling.
Though it might be so clear now, it can be easily get messy. So, always ensure
the event is publishing what happened, not what other part of your code needs
to do.

Some implementations of pub/sub pattern could offer the possibility to target
your event. In other words, you can avoid some parts of your application to
listen an event in favor of other parts. In AngularJS you have the *emit* and
*broadcast* methods to publish some event. Basically, emit will notify all *parent*
scopes from the point where the event was published and broadcast will notify
all the *child* ones. Taking this approach, you will certainly get confused about
who is and who isn’t listening some event. Since an event is still the same
event from wherever you listen it, I definitely see no sense in this kind of
implementation. When publishing some event it should reach your whole
application and every part interested in listening it should be notified. Yes,
it should be *omnidirectional* and the fact it gets broadcasted to all directions
should not produce any side effect. Remembering, an event just says what happened,
not what must happen. So, the fact the event to be published globally should not
be an issue for any other part of your application.

Event names are *constants*. The name of any event will not change in the
runtime. So, write them in constants. Currently, I use to write a dedicated
module to store a hash containing event names. Doing so, you even take the
benefit of having all your events listed in just one place. That can aid you
understand which are all the events your application is making use of. It can
also prevent name collision and make naming conventions explicit for everyone.

From now on, you can avoid three traps that event-driven programming might set
to you. Do you know a couple more traps? Please, don’t hesitate in use the
comments section to share them with me.