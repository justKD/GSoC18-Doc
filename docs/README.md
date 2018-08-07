# Cadence Holmes
## Google Summer of Code with Systers Open Source

[@justKD](https://github.com/justKD/GSoC18-Doc) | [@systers](https://github.com/systers) | [cady.notnatural.co](http://cady.notnatural.co) | [systers.io](http://systers.io)

***

### Out-of-Character Contextual Information for PowerUp!

#### GSoC Summary

PowerUp is a mobile game by Systers Open Source. It's in the style of a choose-your-own-adventure interactive graphic novel but includes mini-games and character development elements. The target audience for the game is preteen girls, and the goal is to teach adolescent sexual health and safety.

When I first tried PowerUp, one of the things I noticed was the abruptness of the actual story elements. At that time, it didn't seem to leave much flexibility for writing immersive stories and characters, and I felt that could also limit the ability to give clear real-world information about potentially difficult story content. This led me to my [original proposal](https://summerofcode.withgoogle.com/projects/#5377389622722560): to add features meant to improve the story telling aspect and to provide out-of-character information such as statistics or professional statements.

Before I really had a sense of the state of the writing, I had intended for a significant part of my timeline to be adding content after the features were implemented.

As it turned out, there were already ongoing efforts to make significant updates to the existing scenes. The features I wanted to add were still relevant, but it didn't seem like adding story content would be efficient since the writing could change drastically.

That's when I suggested amending my project goals and timeline. I thought it would be more beneficial (but still in the spirit of my original proposal) to finish the intended features for PowerUp, then create utility applications to help write and maintain the story elements.

The Systers mentors and admins were receptive to the idea. I had already created a basic GoJS app to map the scenario database for myself, so I was able to use that as a starting point/proof-of-concept.

This has been a great experience for me, and I've written about my takeaway [here on Medium](https://medium.com/@justKD/finishing-up-gsoc-2018-with-systers-open-source-ebf56a740560).

>In the end, I’ve certainly learned some new tricks, but, for me, the most valuable part of this experience has been the accountability. That may sound odd, but it’s really helped me to shift how I think about my code.

#### Future Work

As I worked on the designs, I wanted more and more for the apps to be a part of a single ecosystem. I'd like to see the web apps unified with shared and collaborative work spaces and data, and the output to be built along with PowerUp, rather than having to be manually imported into the project. Plans for these features are currently being outlined via git issues in the respective project repos.

#### Deliverables

Ultimately, I designed, developed, and delivered:

- [Story Sequences](#story-sequences) - Swift classes for implementing automated story sequences that augment the question/answer scenarios.
>
- [Popup Notifications](#popup-notifications) - Swift classes for implementing notification popups throughout the app.
>
- [Story Sequence Designer](#powerup-story-sequence-designer) - A VueJS web app for designing, writing, and maintaining story sequences.
>
- [Scenario Builder](#powerup-scenario-builder) - A GoJS web app for writing and maintaining scenario question and answer datasets using an interactive graphical map.
>
- [Animate](#animate) - A Swift class for scripting staged animations.
>

You can get a glimpse into my development processes and more detailed info about each deliverable via the section links below and by checking out my [GSoC weekly reports](https://github.com/systers/powerup-iOS/wiki/GSoC-2018-Cadence-Holmes).

***
#### Story Sequences

![](https://github.com/justKD/GSoC18-Doc/blob/master/docs/images/storysequenceplayerdemo.gif?raw=true)

The following example locates a sequence in the database and launches the player. This class handles its own interactions and lifecycle, so, aside from the optional delegate methods, no other code is required to manage the event.
```
let scenarioID = 5
guard let model = StorySequences().getStorySequence(scenario: scenarioID) else { return }

let sequenceView: StorySequencePlayer = StorySequencePlayer(delegate: self, model: model, firstTime: firstTime())
self.view.addSubview(sequenceView)
```

- [Story Sequence Player API Docs](https://justkd.github.io/powerup-iOS/Classes/StorySequencePlayer.html)
- [View relevant code stored in this archive](https://github.com/justKD/GSoC18-Doc/tree/master/PowerUp-iOS)
- View in the powerup-ios repository - [Files](https://github.com/systers/powerup-iOS/tree/gsoc18-code/Powerup/OOC-Event-Classes) | [Commits](https://github.com/systers/powerup-iOS/pull/315/commits)

***


#### Popup Notifications

![](https://github.com/justKD/GSoC18-Doc/blob/master/docs/images/popupdemo.gif?raw=true)

Adding a popup only requires a PopupEvent model. This class handles its own interactions and lifecycle, so, aside from the optional delegate methods, no other code is required to manage the event.
```
let model = PopupEvent(topText: "Made with ♥",
                       botText: "by Systers Open Source",
                       imgName: "thisPopupBadgeImage",
                       slideSound: "showPopupSound",
                       badgeSound: nil)

let popup: PopupEventPlayer = PopupEventPlayer(model)
self.view.addSubview(popup)
```

- [Popup Event Player API Docs](https://justkd.github.io/powerup-iOS/Classes/PopupEventPlayer.html)
- [View relevant code stored in this archive](https://github.com/justKD/GSoC18-Doc/tree/master/PowerUp-iOS)
- View in the powerup-ios repository - [Files](https://github.com/systers/powerup-iOS/tree/gsoc18-code/Powerup/OOC-Event-Classes) | [Commits](https://github.com/systers/powerup-iOS/pull/315/commits)

***

#### Story Sequence Designer

![](https://github.com/justKD/GSoC18-Doc/blob/master/docs/images/storydesigner.jpg?raw=true)

Web app built with the stateful framework [VueJS](https://vuejs.org/v2/guide/).

- [Story Sequence Designer Docs](http://systers.io/powerup-story-designer/)
- [View on Github](https://github.com/systers/powerup-story-designer)
- [Live App](https://rawgit.com/systers/powerup-story-designer/master/index.html)

***

#### Scenario Builder

![](https://github.com/justKD/GSoC18-Doc/blob/master/docs/images/scenariobuilder.png?raw=true)

Web app built with the interactive diagram library [GoJS](https://gojs.net/latest/index.html).

- [Scenario Builder Docs](http://systers.io/powerup-scenario-builder/)
- [View on Github](https://github.com/systers/powerup-scenario-builder)
- [Live App](https://rawgit.com/systers/powerup-scenario-builder/master/index.html)

***

#### Animate

I developed `Animate.swift` in order to better handle animations in story sequences. It's meant to simplify chaining together animation events in order to build more complex asynchronous animations with a readable syntax.

Basic use:
```
Animate(view, duration).setOptions(.curveLinear).rotate(to: 90)
```

Asynchronous chaining:
```
let view = Animate(view, duration)
view.setSpring(damping, velocity).translate(by: [50, 0], then: {
    view.flip().shake(then: {
       view.reset()
    })
})
```

- [Animate API Docs](https://justkd.github.io/powerup-iOS/Classes/Animate.html)
- [View relevant code stored in this archive](https://github.com/justKD/GSoC18-Doc/tree/master/PowerUp-iOS)
- View in the powerup-ios repository - [Files](https://github.com/systers/powerup-iOS/tree/gsoc18-code/Powerup/OOC-Event-Classes) | [Commits](https://github.com/systers/powerup-iOS/pull/315/commits)

***




