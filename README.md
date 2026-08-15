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

## 🦉 Mentors
- [Sanjay Sargam]([https://www.linkedin.com/in/sanjaysargam/])
- [Ashish Yadav]([https://www.linkedin.com/in/criticalay/])

# **Admins**
- David Allison
- Mike Hardy

---

## 📚 Organization Overview

[**AnkiDroid**](https://github.com/ankidroid) is a flashcards app that allows anyone to easily harness the power of spaced repetition and active recall to quickly study whatever material they need to. 

### 🎯 **Project Goal**
My project was related to redesigning the look and feel of the deck picker and the UI of the app as a whole through the introduction of various new elements like a bottom navigation bar, hierarchy lines and a new settings destination. My main goals were to translate user feedback into developable features, this involved a refactor of the existing structure to allow for the navigation bar to function as well as many iterations of design to get the best fit for the app.

---

## 🚀 Project Achievements

### 1. **Introduced the bottom navigation bar**

The bottom navigation bar redesigns the entire navigation of the app to allow users to seamlessly switch between the various destinations rather than having to open the sidebar each time. Due to the way it has been engineered, every destination saves the context wherever the user left it off in.

#### Feature or screen name
**Before:**
<p align="center">
  <img width="1080" height="2400" alt="Screenshot_20260815_232718" src="https://github.com/user-attachments/assets/5b462609-1ac5-46ce-a7c3-d8f07535b3ed" />
  <img width="1080" height="2400" alt="Screenshot_20260815_232742" src="https://github.com/user-attachments/assets/e899a343-cdf9-4f14-9842-7238f4b366e3" />
</p>

**After:**
<p align="center">
  <img width="1080" height="2400" alt="Screenshot_20260815_160018" src="https://github.com/user-attachments/assets/691dbee1-e7c0-4914-985d-299549fd5795" />
  After
</p>

### 2. **Added the new more destination**

There was no place to see all the various things you could do to support the app and also tweak your account and the more destination was the perfect place to solve this problem.

<img width="1080" height="2400" alt="Screenshot_20260815_232643" src="https://github.com/user-attachments/assets/79f927a9-f3d4-4ec5-8f05-2ab271d149ac" />


### 3. **Hierarchy Lines**

The current way the deck picker screen shows sundecks is not user-friendly due to there being no indication apart from spacing to tell you what is a child of a deck. To help this, we decided to bring in hierarchy lines so that users can easily tell what deck is a child of what deck.
<img width="1080" height="2400" alt="Screenshot_20260815_232544" src="https://github.com/user-attachments/assets/23963985-c99c-45cf-825a-876e423de8e5" />

---

## 📂 Pull Requests

Here's a list of the pull requests I created during GSoC YEAR:

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

## 💡 Outcome

GSoC with AnkiDroid has been one of the most rewarding experiences for me. I was able to learn so much about capturing user requirements and converting them to real features, discussions with users was taxing at times since you have to balance all the requirements, but getting a feature just right was worth it. This project has redefined the entire UI/UX for an app used by millions of students around the world and it will hopefully improve their experience and give them a little boost of motivation knowing their favorite study app is being constantly worked on by a group of amazing contributors.

---

## 🔮 Future Work

For future work, my upcoming goals are: 
- To implement the ability to drag decks and drop them into other decks or out of decks instead of having to manually add subdecks.
- To make the deck settings more accessible from a UX standpoint.
- To slowly start migrating the nav bar to compose.
- To make sure we have a working navigation rail for tablets.

---
