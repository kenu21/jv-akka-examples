# jv-akka-examples

About firstexample:
Main create actor RoomCommand and actor SessionEvent. Main watch on actor SessionEvent. When Main get signal Terminate,
then Main stopped. Main tell actor RoomCommand message GetSession with screenName = ol' gabbler and with
replyTo = link on actor SessionEvent.
In response to message GetSession actor RoomCommand create nested actor SessionCommand. Actor RoomCommand give
actor SessionCommand link on itself, name of actor SessionEvent and link on actor SessionEvent. Actor RoomCommand add
in list of links on SessionCommand new link on actor SessionCommand. Actor RoomCommand tell message SessionGranted to
actor SessionEvent. Actor RoomCommand give link on actor SessionCommand (PostMassage) to actor SessionEvent
by method narrow() in actor SessionCommand.
In response to message SessionGranted actor SessionEvent tell message PostMessage ("Hello world) to
actor SessionCommand.
In response to message PostMessage actor SessionCommand tell message PublishSessionMessage to actor SessionCommand.
In response to message PublishSessionMessage actor SessionCommand tell all actors SessionCommand
message NotifyClient that has MessagePosted with screenName and message.
In response to message NotifyAll actor SessionCommand tell its actor SessionEvent message MessagePosted with sreenName
and message.
In response to message MessagePosted actor SessionEvent prints this message and screenName.
