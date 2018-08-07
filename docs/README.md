https://github.com/systers/powerup-scenario-builder
https://github.com/systers/powerup-story-designer
https://github.com/systers/powerup-iOS

http://systers.io/powerup-scenario-builder/
http://systers.io/powerup-story-designer/
https://justkd.github.io/powerup-iOS/


https://github.com/systers/powerup-iOS/pull/315

# Cadence Holmes
## Google Summer of Code with Systers Open Source

[@justKD](https://github.com/justKD/GSoC18-Doc) | [@systers](https://github.com/systers) | [cady.notnatural.co](http://cady.notnatural.co) | [systers.io](http://systers.io)

***

### Out-of-Character Contextual Information for PowerUp!

#### Summary

PowerUp is a mobile game by Systers Open Source. It's in the style of a choose-your-own-adventure interactive graphic novel but includes mini-games and character development elements. The target audience for the game is preteen girls, and the goal is to teach adolescent sexual health and safety.

When I first tried PowerUp, one of the things I noticed was the abruptness of the actual story elements. At that time, it didn't seem to leave much flexibility for writing immersive stories and characters, and I felt that could also limit the ability to give clear real-world information about potentially difficult story content. This led me to my [original proposal](https://summerofcode.withgoogle.com/projects/#5377389622722560): to add features meant to improve the story telling aspect and to provide out-of-character information such as statistics or professional statements.

Before I really had a sense of the state of the writing, I had intended for a significant part of my timeline to be adding content after the features were implemented.

As it turned out, there were already ongoing efforts to make significant updates to the existing scenes. The features I wanted to add were still relevant, but it didn't seem like adding story content would be efficient since the writing could change drastically.

That's when I suggested amending my project goals and timeline. I thought it would be more beneficial (but still in the spirit of my original proposal) to finish the intended features for PowerUp, then create utility applications to help write and maintain the story elements.

In the end, I designed and developed:

- [Story Sequences](#story-sequences) - Swift classes for implementing automated story sequences that augment the question/answer scenarios.
>
- [Popup Notifications](#popup-notifications) - Swift classes for implementing notification popups throughout the app.
>
- [Animate](#animate) - A Swift class for scripting staged animations.
>
- [Scenario Builder](#powerup-scenario-builder) - A GoJS web app for writing and maintaining scenario question and answer datasets using an interactive graphical map.
>
- [Story Sequence Designer](#powerup-story-sequence-designer) - A VueJS web app for designing, writing, and maintaining story sequences .

***
### Story Sequences

![](https://github.com/justKD/Powerup-Story-Designer/blob/dev/docs/images/2-ingame-example.gif?raw=true)

***


### Popup Notifications


***


### Animate


***


### Scenario Builder


***

### Story Sequence Designer


***