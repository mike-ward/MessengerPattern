# MessengerPattern
Improved from answer of Dalstroem in stackOverflow!

The question: http://stackoverflow.com/questions/23798425/wpf-mvvm-communication-between-view-model

Dalstroem profile: http://stackoverflow.com/users/3683189/dalstroem

My profile: http://stackoverflow.com/users/4871837/yeah69

Improvement: I made the the MessageKey sensitive to the message type. Thus, several different message types with no context object can be registered to the same receiver object.

Problem:

Before my improvement the MessageKey was not dependend of the message type, but "only" the recipient and the context.
So when you try to register two different message types to the same recipient and same context, then only the first registration succeeds.


Solution:

Introduce the type to the MessageKey.
Basically I did not do anything else. The Messenger class itself is almost untouched, except that now the Unregister method needs the type now, which leads to a consequence.

Consequence:

Now the recipients have to be Unregistered not only for each context, but also for each context and message type.
