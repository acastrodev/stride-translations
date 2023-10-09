# UI Basics

This first C# intermediate tutorial covers the basics of creating UI with Stride.

## Explanation

We will learn about the UI editor, accessing UI page elements and even how to setup UI entirely by code. The Stride editor comes with a UI editor which we can utilize to create UI pages. We can then add UI elements to these pages, like buttons and textfields.

Those UI elements can be referenced in code, so that can set up events like `button-clicked` or `text-changed`.

> [!Video https://www.youtube.com/embed/rB5duwfs1mU]

> [!Video https://www.youtube.com/embed/NnnbHn9LQUU]

## Stride editor UI pages
The code below will look for a Page component that has been added to the current entity. On that page we search for UI elements like buttons and textfields. We than tell those UI elements what happens when we click on them, or that something needs to be done when a text value changes.
[!code-csharp[editorpages](../../../../stride/samples/Tutorials/CSharpIntermediate/CSharpIntermediate/CSharpIntermediate.Game/01_UI-Basics/UIByEditor.cs)]

## UI pages made entirely by code
This script will create everything from scratch: a UI page, a stackpanel, a button, a textfield and the interactive logic behind it.
[!code-csharp[uibycode](../../../../stride/samples/Tutorials/CSharpIntermediate/CSharpIntermediate/CSharpIntermediate.Game/01_UI-Basics/UIByCode.cs)]
