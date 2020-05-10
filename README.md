# Panel Manager

This package helps you quickly and easily build complex, multi-panel user interfaces. You no longer have to worry about passing around VI references, the simple framework lets you worry about writing your business logic, not debugging panel errors.

There are two libraries included:
Panel
This library contains all of the classes to manage the different types of panels. There are three built in types of panels:

1. Window: This is a typical window
2. Dialog: This is a window that is also modal.
3. Subpanel: This is a panel that will be inserted into a subpanel in another VI.

New panel types can be added by overriding Panel.lvclass.

Panel Actor
This is an Actor that uses the Panel framework. This allows you to write the Actor's user interface once, then use it wil multiple types of panels, all without changing your UI code.

Checkout the examples and our website for more info!

---

MGI currently works with the GPM Package Manager and decided to stop the support for VIPM. This package is based on the GPM packages of the MGI Panel. It also add the support of the previously published examples.

https://gpackage.io/packages/@mgi/panel-manager  
https://gitlab.com/mgi/gpm-packages/panel-manager  

https://gpackage.io/packages/@mgi/panel-actors  
https://gitlab.com/mgi/gpm-packages/panel-actors  

Installation notes:
The original MGI Panel Manager package isn't set as incompatible package. Please consider to remove the original MGI Panel Manager package before installing this package.

Legacy Software:
Be sure to change the inheritance of your classes to the provided classes within this package.