<div align="center">
  <img src="https://developers.google.com/open-source/gsoc/resources/downloads/GSoC-logo-horizontal.svg"
       alt="GSoC logo" width="300" style="display:block; margin:auto;"/>
  <h2 style="margin-top: 12px; font-size: 36px; font-weight: bold;">
    @ <a href="https://github.com/ankidroid/anki-android" style="text-decoration: none; color: inherit;">AnkiDroid</a>
  </h2>
</div>


<h1 align="center">Shaan Narendran</h1>
<h2 align="center">Deck Picker Redesign - Google Summer of Code 2026</h2>


<p align="center">
  <a href="https://github.com/ShaanNarendran">GitHub</a> | <a href="https://www.linkedin.com/in/shaan-narendran/">LinkedIn</a>
</p>

---

## Mentors
- [Sanjay Sargam](https://www.linkedin.com/in/sanjaysargam/)
- [David Allison](https://github.com/david-allison)
- [Ashish Yadav](https://www.linkedin.com/in/criticalay/)

## Org Admins
- [David Allison](https://github.com/david-allison)
- Mike Hardy - github@mikehardy.net

---

## Organization Overview

[**AnkiDroid**](https://github.com/ankidroid) is a flashcards app that allows anyone to easily harness the power of spaced repetition and active recall to quickly study whatever material they need to. 

### **Project Goal**
My project was related to redesigning the look and feel of the deck picker and the UI of the app as a whole through the introduction of various new elements like a bottom navigation bar, hierarchy lines and a new settings destination. My main goals were to translate user feedback into developable features, this involved a refactor of the existing structure to allow for the navigation bar to function as well as many iterations of design to get the best fit for the app.

---

## Project Achievements

### 1. **Introduced the bottom navigation bar**

The bottom navigation bar redesigns the entire navigation of the app to allow users to seamlessly switch between the various destinations rather than having to open the sidebar each time. Due to the way it has been engineered, every destination saves the context wherever the user left it off in. The main blocker I had during proposal phase was that we have to save context between tabs and the way I accomplished this is by making sure each destination had its own standalone fragment, fragments are lightweight components that can be placed inside activities. Another big blocker was that Kotlin does not support multiple inheritance so having a main bottom nav class then subclasses under it was not a possibility so instead we went with the idea of using composition and extracted out a BottomNavController that went around this issue and allowed for the implementation to be smooth.

**Before:**

<p align="center">
  <img width="250" alt="Screenshot_20260815_232718" src="https://github.com/user-attachments/assets/5b462609-1ac5-46ce-a7c3-d8f07535b3ed" />
  <img width="250" alt="Screenshot_20260815_232742" src="https://github.com/user-attachments/assets/e899a343-cdf9-4f14-9842-7238f4b366e3" />
</p>

**After:**

<p align="center">
  <img width="250" alt="Screenshot_20260816_125658" src="https://github.com/user-attachments/assets/897d6dad-027f-47cd-bd32-c74a97a3942d" />
</p>

### 2. **More destination**

There was no place to see all the various things you could do to support the app and also tweak your account and the more destination was the perfect place to solve this problem. This destination is also a fragment and the design was set up for this after a lot of back and forth from users of the app.
<p align="center">
  <img width="250" alt="Screenshot_20260815_232643" src="https://github.com/user-attachments/assets/79f927a9-f3d4-4ec5-8f05-2ab271d149ac" />
</p>

### 3. **Hierarchy Lines**

The current way the deck picker screen shows sundecks is not user-friendly due to there being no indication apart from spacing to tell you what is a child of a deck. To help this, we decided to bring in hierarchy lines so that users can easily tell what deck is a child of what deck. The development of this was the most taxing from a design perspective, many users had different ideas of what they wanted the lines to look like. The second challenging part about this particular feature was the performance, in collections with thousands of decks where we have to draw tens or even hundreds of lines instantly, the app can face severe performance issues. I initially had a very high complexity of around O(VN) for sibling searches but the current lookahead logic using bit masking reduced that to O(N) + O(V).
<p align="center">
  <img width="250" alt="Screenshot_20260816_125658" src="https://github.com/user-attachments/assets/897d6dad-027f-47cd-bd32-c74a97a3942d" />
</p>

### 4. **Screenshot Tests**

One of the main testing implementations I did was with regard to the deck picker screenshot test, this was completely new to me since it was a recent adoption to the repository. The first issue I encountered here was that with my initial implementation of the test, the bottom nav pref was not being selected consistently and so I used the exact prefs key that is used by the singleton to make sure we are turning on the pref each time. The second instance was that we were not clearing the prefs after use so screenshot tests were being commented in every PR (oops..) and the way we fixed this was to use an @After annotation then reset the pref. Finally, there were several race conditions due to the way Roboelectric's looper loops through coroutines so sometimes we were skipping deck expansions when they were supposed to happen for the tests. Fixing all of this really helped me understand how to deal with race conditions and how to better write tests in general.

### 5. **Embedding the Nav Bar to the legacy card browser**

This was my last PR for the project and it basically allows the nav bar to work with the card browser that is live for everyone right now. We have a new search view as a developer preference that is completely it's own fragment and so for the majority of the project, this was coupled with the nav bar preference. This change makes it so the nav bar can live by itself as its own standalone preference. Initially, when trying to implement this, the main issue was that the old card browser was heavily coupled with the activity and the toolbar on top was actually from the activity. This meant that when I tried to integrate it with the nav bar, the card browser toolbar would leak into the other destinations as well since we had one host activity that was now conflicting.
To solve this issue, I decided to create a new embedded layout that will take the toolbar from the card browser activity and decouple it so that the card browser fragment can provide the toolbar. This essentially solves our leakage issue.
<p align="center">
  <img width="250" alt="Screenshot_20260815_232614" src="https://github.com/user-attachments/assets/69608f3d-a3f1-41ae-bd0d-14a264d8366e" />
</p>

---

## Pull Requests

Here's a list of the pull requests I created during GSoC 2026:

1. [Setting up of the bottom nav class](https://github.com/ankidroid/Anki-Android/pull/21114)
2. [Decoupling of the CardBrowserFragment from it's activity](https://github.com/ankidroid/Anki-Android/pull/21158)
3. [Adding of the more fragment destination](https://github.com/ankidroid/Anki-Android/pull/21186)
4. [Extracting a controller for the BottomNavActivity](https://github.com/ankidroid/Anki-Android/pull/21191)
5. [Add wiring and analytics for the BottomNavBar](https://github.com/ankidroid/Anki-Android/pull/21274)
6. [Disabling of the NavigationDrawer](https://github.com/ankidroid/Anki-Android/pull/21321)
7. [Draw hierarchy lines for decks](https://github.com/ankidroid/Anki-Android/pull/21373)
8. [Resolving Deck Picker screenshot flakiness](https://github.com/ankidroid/Anki-Android/pull/21436)
9. [Adding Shortcuts for the Bottom Nav Bar](https://github.com/ankidroid/Anki-Android/pull/21439)
10. [Making the bar compatible with the current card browser](https://github.com/ankidroid/Anki-Android/pull/21499)
---

## Outcome

GSoC with AnkiDroid has been one of the most rewarding experiences for me. I was able to learn so much about capturing user requirements and converting them to real features, discussions with users was taxing at times since you have to balance all the requirements, but getting a feature just right was worth it. This project has redefined the entire UI/UX for an app used by millions of students around the world and it will hopefully improve their experience and give them a little boost of motivation knowing their favorite study app is being constantly worked on by a group of amazing contributors.

---

## Future Work

For future work, my upcoming goals are: 
- To implement the ability to drag decks and drop them into other decks or out of decks instead of having to manually add subdecks.
- To make the deck settings more accessible from a UX standpoint.
- To slowly start migrating the nav bar to compose.
- To make sure we have a working navigation rail for tablets.

---
