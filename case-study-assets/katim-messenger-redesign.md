# KATIM Messenger Redesign - A UX Case Study

## Overview

KATIM® Application Suite is designed for organizations that need to keep sensitive data secure, private, and trusted at all times, in transit, at rest, and wherever it may be in a communication channel. Designed for stringent use cases where sovereign and uncompromising security are required for collaboration and communication, KATIM® Application Suite provides a necessary additional layer of protection for the most security-sensitive organizations. KATIM® Application Suite consists of applications to secure data messaging, voice communication, and video conferencing.

## My role

**Senior UX Architect | E&Y**

- Managing design deliverables and ensuring quality
- Sprint planning and documentation
- Wire-framing, prototyping, User Research, Design system

### Team
1 UX Program manager | 4 UX designers | 6 Visual designers

### Duration
Jan 2019 - Feb 2020

## The Challenge

Our objective was to revamp KATIM's application suite, elevating the design language to align with contemporary industry standards. This included addressing existing design flaws, introducing new features, ensuring multi-platform support, and creating both dark and light themes for Android, iOS, and Web platforms. By implementing these improvements, we aimed to provide users with a cohesive and visually pleasing experience across all devices and platforms.

*(Before/after messenger screens shown: legacy "Timeline" list view vs. redesigned "Messages" view.)*

## The design process

We followed a 6D design process to achieve the desired results: **Discover → Define → Dream → Design → Develop → Deliver.**

### Discover

In this phase, I and my team studied the existing messenger application to:
- Understand and map existing task flows
- Identify and categorise design issues both in terms of Experience and Visual design

The first task we did was to study the existing application in-depth and map the task flows so that we can identify the areas of optimisation.

We then went on to analyze the application from a UI point of view and highlight the areas of improvement and categorize them into High, Medium, and Low impact to help us prioritize.

**Existing design: Timeline view — findings**
- **High impact:** The tab bar navigation icons are too small. The inactive icons look disabled. The icon and the notification bubble are similar in size.
- **Medium impact:** Icon and supporting status are not in close proximity to each other, thus resulting in ambiguity for the user and cluttering the layout (e.g. outgoing call icon and label "Outgoing voice call").
- **Low impact:** Iconography is inconsistent — both filled and outline styles have been used.

### Define

During this phase, our focus was to conduct secondary user research. This involved creating personas, user stories, and journey maps to gain insights into user behaviors and pain points. These findings served as the foundation for developing optimized task flows and a cohesive visual language.

**Persona** — Creating personas is a way to imagine who we would be designing for. Listed goals & needs, motivation, and fears & frustrations (e.g. Ahmed Shakeel, Army Officer persona; a VVIP persona).

**Information Architecture** — The information architecture serves as the foundation of any product, providing essential clarity for subsequent steps. Priority was a simple yet effective architecture that avoided excessive complexity and unnecessary levels, ensuring clear navigation and intuitive user experiences.

**Optimized task flows** — After finalizing the information architecture, we shifted focus to optimizing the task flows to better address user needs, concerns, and frustrations.

Optimizations made vs. the existing flow:
1. Removed the concept of "Timeline" and made entry points clear as **Messages** and **Calls** — reduced 1 click for users.
2. Users can now either continue messaging or initiate a voice/video call directly from the message details screen.
3. When starting a new chat, users select whether they want a group chat first, and only then search/select multiple users — since most conversations are 1:1, this reduced ~2 clicks.

### Dream / Design

**Wireframes and Screen-Flows** — Starting from initial sketches and progressing to mid-fidelity screens, we crafted the necessary wireframes. These served as a visual representation of the improved task flows, communicating the overall flow and giving stakeholders a comprehensive understanding of the project.

**Style guide** — We went the extra mile by developing two distinct style guides, and consequently two separate design systems, to accommodate both Light and Dark themes for both Android and iOS devices. We also supported dedicated KATIM devices, which required three sets of typefaces:
- **Android** — Roboto
- **iOS** — San Francisco Pro Text
- **KATIM device** — Barlow

Each theme documented core elements — checkboxes, toggles, radio buttons, input fields (default + error state), search fields (default + with clear/cancel), the message input field, and scrollbar colour tokens — for both Light and Dark modes.

**Design system** — The core essence of a successful product lies in its design system. Given the extensive scope, we developed a highly comprehensive and detailed design system in Sketch (design systems were still a novel concept at the time).

### Develop / Deliver

Final icon library spanned six size scales (Icons‑28, 30, 36, 42, 48, 60) to support dense information contexts across chat, calls, and settings. Final screens shipped across Barlow (KATIM device), Roboto (Android), and San Francisco Pro Text (iOS) — pixel-matched across all three typefaces for the same core chat screen.

## Lessons learned

- **Dual ownership builds range** — Balancing Program Director and Lead UX Designer roles taught me how design quality and program execution constantly influence each other, not separate tracks.
- **Governance is a design skill too** — Structuring sprints, resourcing, and project governance felt as critical to the outcome as the design decisions themselves.
- **Client relationships need proactive expectation-setting** — Learned that setting expectations early — and consistently exceeding them — matters more than reacting well to problems as they arise.
- **Distance demands documentation discipline** — Working with a globally distributed dev team with no direct channel taught me that clear, structured documentation (use cases, gesture/pattern specs) isn't a nice-to-have — it's the primary interface when direct collaboration isn't possible.
- **Complexity rewards resourcefulness over rigidity** — The biggest lesson was that ambiguity and multi-hat responsibility are manageable when you stay adaptable rather than over-relying on a fixed process.
- **Smooth execution is a signal, not luck** — Delivering with minimal friction reinforced that most "smoothness" is actually the payoff of early structure and clear communication, not chance.

---
*Source: "KATIM Messenger Redesign - A UX Case Study" PDF, transcribed to Markdown for portfolio case study development.*
