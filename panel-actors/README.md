Panel Actors make it trivially easy to write User Interface Actors. Each UI is just an actor. When you need to communicate between your UIs, you just send it actor framework messages. All of the business to do with showing and hiding your front panel is handled by the [MGI Panel Manager Framework](https://gpackage.io/packages/@mgi/panel-manager)

## Creating a Panel Actor

1. Inherit from Panel Actor.lvclass
1. Implement your UI in your actor's `Actor core.vi`
1. Launch your actor using `Launch Root Panel`or `Launch Nested Panel`�

That's it! When you launch a Panel Actor, you need to specify the panel type. When the actor is launched Actor core's front panel is inserted into the specified panel.

## Panel Actor Features

Panel Actors provide an extremely versatile interface for creating modular, professional user interfaces. Here are some of the features.

### UI Initialization

Writing professional code is very important. Something that always looks amateur is when the UI is displayed before its contents are populated. Panel Actors help provide an easy way to prevent this. The Panel UI is not shown until your Panel Actor calls the parent implementation of `Actor core.vi`. This means that if you need to pre-populate you UI with any data you just need to do it before the `Call Parent Method` node. This could mean simple things like populating a control or more complex things like launching nested panels.

### Initialization Waiting

When Panel Actors are launched the node waits for the UI to be initialized. Use this to pre-populate the UI (including all nested subpanels) before showing the front panel.

### Panel Actor Events

Panel Actors throw a few events. Since most of the time your panel actors will have an Event Handler helper loop, these events can be registered for. These events will tell you when the actor has been initialized and stopped, as well as when the Panel itself changes state. The most important of these events is the `Actor.Stopped` event. This event is thrown when the actor is stopped. This event is helpful for terminating your event handler Helper loop. See the examples included in the package for more information about Panel and Panel Actor events.

### Panel Helper

The Panel Helper class is designed to give developers an easy way to interface with the panel, no matter what type of panel it is. This helps with deferring updates, setting the mouse busy, and other panel specific tasks. The Panel Helper is valid even if the panel type changes.

### Tiered Panels

The Panel Actor assumes that the most specific implementation of Actor Core contains the UI to be shown. This means that if you have an inheritance tree, in which all levels contain a UI, by default the framework would only show the most specific.

Tiered Panels allow you to assemble your UI using each layer of inheritance. Each level just needs to call `Add Panel Tier.vi` add the previous layer to the main UI. This allows developers to implement the relevant UI in the proper inheritance level.

## Panel Actor Messages

A Panel Actor has a few extra messages.

- Show Panel Message - Shows the Panel. What this does will depend on the specific panel type.
- Hide Panel Message - Hides the Panel. What this does will depend on the specific panel type.
- Change Panel Message - Changes the type of panel to display the Panel Actor in. This lets you easily implement something like Docking and Undocking into a subpanel.

Additionally, a Panel Actor can send a message to itself to launch a Nested Panel using the `Send Launch Nested Panel.vi` method.

## Contributing

See [Contributing.md](CONTRIBUTING.md) for information on how to submit pull requests. Bugs can be reported using the repositories issue tracker.

#### _This package is implemented with LabVIEW 2017_
