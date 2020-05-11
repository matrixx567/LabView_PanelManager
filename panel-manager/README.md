Non-trivial applications require complex user interfaces. The goal is to keep them as simple as possible but the fact fact of the matter is that if software needs to do a lot of stuff then there are going to be a lot of controls and indicators. User interfaces can always be split up conceptually (these controls are for loading while those controls are for previewing data, for example) but splitting them up in LabVIEW can often be daunting. We must make compromises.

The MGI Panel Manager toolkit abstracts away these complexities. This makes it trivially simple to build an application with UIs with multiple layers of subpanels, nice dialogs, or any other presentation format.

## Panel Types

The Panel class is the base interface for the library. Every UI that will eventually be shown uses the panel interface. The base framework supports two different panel types: **[Window](#windows)** and **[Subpanel](#subpanls)**. Since the framework is extendable, other panel types can be added at any time.

The frontpanel that uses the Panel interface doesn't have to know anything about the type of panel it will be inserted in. That makes it really do things like:

- Use the same UI in a window in some instances, but a subpanel in others.
- Debug a UI in a window, but insert it in a subpanel in the real application.
- Implement a docking/undocking system.

### Subpanels

The Subpanel type manages inserting and removing front panels from subpanels. Subpanels are the key to splitting up large, complex UIs into small, maintainable chunks of code.

### Windows

Windows are the base panel type for every application. When a panel with a window type is initialized the VI's front panel is shown.

#### Positioning Windows

Windows need to be placed in a logical spot on the display. There are several ways to tell the framework where to place the new window:

- **Maximized:** The window will be opened with a maximized state.
- **Referenced Type:** The window will positioned based on a referenced location. Referenced position can also specify an offset and alignment option.
  - _Display:_ The specified display is used as a reference.
  - _Top Level VI:_ The top level VI's front panel is used as a reference.
  - _VI:_ Any VI's front panel is used as a reference.
  - _Control:_ The specified control is used as a reference.

##### Window Alignment

Alignment is simple. You can specify Top, Center, or Bottom for vertical alignment and Left, Center or Right for horizontal alignment.

##### Window Offsets

There are 3 built in types of offset. Again, this is a extendable interface.

- No Offset
- Absolute Offset – Absolute increments are used for the offset
- Cascade Offset – Offsets are dynamically calculated based on the number of windows show as well as their current positions

#### Window Sizes

When docking and undocking into subpanels, or when launching windows in different contexts it is often useful to manually specify the size of the window to be shown. There are 4 built in types of window size

- Unchanged – The window size will be unchanged. Note: when using subpanels and windows with re-entrant shared clones VIs (such as with panel actors) leaving the window size unchanged can often lead to unexpected window sizes.
- Absolute – Manually sets the window size. If the specified values are smaller than the Panel’s minimum panel size it will be coerced up to the minimum panel size.
- Min Panel – Sets the panel size to the panel’s configured minimum size.
- Reference – Sets the panel size based on the referenced item. This is useful for making a window take up half of the screen, or 75% of the top level VI. The referenced item will depend on the reference type.

## Contributing

See [Contributing.md](CONTRIBUTING.md) for information on how to submit pull requests. Bugs can be reported using the repositories issue tracker.

#### _This package is implemented with LabVIEW 2017_
