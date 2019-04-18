### A design system can help establish a common vocabulary between everyone in an organization. Vue DS consists of 4 layers:

- **Design Tokens** are the atoms of the system. In Vue Design System they are used instead of hard coded values to ensure a better consistency across any platform.

- **Elements** utilize decisions made on the token level. A simple example of an element would be a button, a link, or an input. Anything that cannot be broken down further.

- **Patterns** are UI Patterns that fall on the more complex side of the spectrum. So for example things like a date picker, a data table, or a visualization. Patterns utilize both elements and tokens. If you wonder whether something should be called an element or a pattern, ask yourself this question: “Can this be broken down into smaller pieces?” If the answer is yes, it should most likely be a pattern in Vue Design System.

- **Templates** exist to document the layout and structure of a section. I am not calling these pages since semantically that would be incorrect. While they can be pages, that’s not their only functionality. Templates consist of the three things mentioned above: tokens, elements, and patterns.
