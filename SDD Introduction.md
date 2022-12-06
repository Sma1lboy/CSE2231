# SDD Introduction

Software design documents should include:

- A description of the product.
- The scope of the work required for the project to be completed.
- And a list of milestones.

### A. User Interface

The user interface component of a project is by far the most challenging section of the design document.

Even if the product owner sends clear illustrations created by a graphic designer, the graphic designer almost always is not also a strong programmer. Naturally, this will lead to communication issues.

So yes, do create those illustrations, but keep in mind that you’ll need to provide some additional context, which I’ll get to in a moment. The problem here is that the illustrations likely say little regarding…

- Animations
- Control states.
- What happens with a button when it needs to be unusable?
- How do you know if the button should be visible to the end user or not?
- Or how do you ideally want the end-user to navigate the application?

And this is a key example of how software design documents, like [software test cases](https://blog.tara.ai/how-to-write-software-test-cases-template/), are a valuable time saver. Prior to a developer writing any code behind the illustrations, you need to have all such questions answered.

But first, you need to create those illustrations…

### Wireframing Tools

You might be asking, “Okay, but what if I don’t have a graphic designer?”

Not to worry…

You can create some clean illustrations using one of many different [wireframing tools](https://www.creativebloq.com/wireframes/top-wireframing-tools-11121302), and put together a complete set of screen layouts. This should include any variations that the views display in different application states. Just for the record, our favorite wireframing tool is [Invision](https://www.invisionapp.com/). They’re awesome 

And if you’re working on a dual application that needs to be compatible across different devices and screen sizes, be sure to create separate wireframes for each device.

Yes, this is a pain in the _______. 

But weigh the cost of having to rewrite hours worth of code and constantly changing the UI, with how long it’ll take one of you to create these screen layouts.

So, to avoid miscommunication that could turn a three week project into a three month project…

**Take the time in the beginning stages to get the UI design right!**

Don’t presume anything, and ask each other lots of questions.

## B. Requirements / System Overview

In the requirements section of your application design document, you’ll provide a general description of the functionality, context and design of the project.

To help your developer(s) better understand your application, you’ll answer questions such as:

- “What’s the main purpose of the application?” And,
- “What are the possible failure scenarios and conditions?”

The point here is for the product owner to answer these open ended questions as well as they can, and then for the developer to ask follow up questions once they receive the answers. As a result, you will dramatically reduce the risk of miscommunication and the need to write additional code.

## C. Milestones

Setting clear milestones for your design document template is key to fully understanding the [scope of your project](https://blog.tara.ai/project-scope/).

Whether it’s the developer or the product owner that sets these milestones, they should be as unambiguous as possible, and agreed upon one-by-one by both parties.

Milestones can be in the form of functionalities and / or components, or possibly in the form of independent applications should the job description include a full suite of deliverables. At a minimum, milestones should provide a clear metric toward completion.