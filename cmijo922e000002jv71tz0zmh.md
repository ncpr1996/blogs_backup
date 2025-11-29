---
title: "Building an Expense Tracker with AWS Kiro"
datePublished: Sat Nov 29 2025 02:28:02 GMT+0000 (Coordinated Universal Time)
cuid: cmijo922e000002jv71tz0zmh
slug: building-an-expense-tracker-with-aws-kiro
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1764381893312/4778a759-facc-4f4d-b1ad-aa6c9c417ad4.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1764383265366/2c840e7d-09f3-4c7b-8166-dbb3fe79d812.png
tags: aws, amazon-web-services, ai-development, aws-community, ai-assisted-coding, budget-tracking, aws-kiro

---

Few people truly track their expenditures on a daily basis, despite the fact that most people know they should. It is tedious, time-consuming, and a lot of the apps are either too complicated or not designed beginner users. My Daily Expense Tracker aims to address this issue by providing customers with an easy-to-use, quick, and aesthetically pleasing web application that helps them manage their spending.

I'll describe the issue, the fix, and how AWS Kiro made it far quicker for me to move from an idea to a finished, live web application than if I had to start from scratch.

**Live Demo :** [https://ncpr1996.github.io/daily-expense-tracker/](https://ncpr1996.github.io/daily-expense-tracker/)

**GitHub:** [https://github.com/ncpr1996/daily-expense-tracker](https://github.com/ncpr1996/daily-expense-tracker)

## Problem: Budgeting That Actually Fits Users

Most generic expense apps miss a few important points:

* They don't think in lakhs and thousands, which is how many Indians view money on a daily basis.
    
* To add a single tiny tea or auto ride, they require you to tap through an excessive number of screens.
    
* They rarely show a clear picture of “How much can I safely spend today?” or “How many days until salary?”.
    

I have a different idea for the AI for Bharat Hackathon:

* Web-based and browser-based (no mobile installation needed).
    
* Designed with the ₹ symbol, lakh formatting, and salary-based budgeting in mind for Indian customers.
    
* Easy to use on a daily basis, yet capable of providing charts, patterns, and insightful insights.
    

## Solution Overview: A Premium Daily Expense Tracker

The finished product is a desktop-first web application that functions well on mobile devices as well. It features a main area for dashboards, tables, and charts, as well as a fixed sidebar for easy expense entry.

## Key features

* **Fast expense entry**: Amount, category, date, and optional notes in a few seconds.​
    
* **Eight categories**: Food, Transport, Bills, Shopping, Entertainment, Health, Education, and Other, each with its own emoji so the UI feels friendly.​
    
* **Budget tracking**: Monthly budget, real‑time “spent vs remaining”, color‑coded state, and days until salary with a safe daily spend recommendation.​
    
* **Visual insights**: Category breakdown chart, month filter, and recent expenses preview to understand where money is going.​
    
* **Savings and reminders**: Daily savings calculator and a simple bill‑reminder system so you don’t miss due dates.​
    
* **Smart UX**: Dark mode, glass‑morphism cards, animations, and fully responsive layout.​
    

There is no backend because all data is kept locally in the browser using LocalStorage, giving users complete control over their data.

## Architecture: Simple Files, Clear Flow

Because the project is purposefully lightweight, it may be installed on any static server, GitHub Pages, or Netlify.

## Project structure

* `index.html` – Main HTML and layout.
    
* `styles.css` – All styling, themes, and responsive rules.
    
* `app.js` – Core application logic.
    
* `manifest.json` – PWA configuration so it can also work like an installable app.
    
* `.kiro/` – Documentation generated and refined with Kiro: requirements, architecture, user guide, prompts, and more.​
    

Expenses, budgets, reminders, profile, theme, and chosen chart month are all included in a single state object within `app.js`. Every user activity follows to the same pattern:

`User Action → Event Listener → Update State → Save to LocalStorage → Update UI.​`

This keeps logic predictable and easy to reason about.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1764382247929/ac8aaffc-48a8-4e11-862e-2f8e4a23b291.png align="center")

### Main modules

* **Expense management**: Functions to add, delete, filter, and render expenses in a table.​
    
* **Budget tracking**: Functions to compute total spent, remaining budget, and update the overview cards.​
    
* **Visualization**: Functions to render the category breakdown chart and month filters; currently done with CSS‑based charts, with Chart.js ready for future upgrades.​
    
* **Profile and greetings**: Functions to store name, occupation, and city, and use them for time‑based greetings like “Good Evening”.​
    
* **Utilities**: Currency formatting for ₹, date formatting, category emojis, and dark‑mode toggling.​
    

This modular strategy follows to single-responsibility standards and enables future maintenance or expansion.

## Designing the Experience: From Requirements to UI

Kiro assisted me in gathering specific requirements in an organized manner before to writing any code. The `requirements.md` file, which outlines the functions of the application, the data structures it requires, and the format of the user stories, reads nearly exactly like a product specification.

### Requirements turned into UI

From those requirements, the UI naturally emerged:

* A **Budget Overview** card to show current month budget, spent, and remaining at a glance.​
    
* A **quick add form** in the sidebar with category buttons laid out in a neat 4×2 grid so nothing overflows, even on smaller screens.​
    
* Tabs for **Dashboard, Expenses, Saving Plan, and Reminders**, each focusing on one part of the requirements.​
    
* Date validation to block future expenses and keep financial data realistic.​
    

In this case, Kiro was very helpful since it generated clear HTML structure and logical CSS tokens like theme colors, spacing, and glass-morphism card styles when given natural-language criteria.

## How Kiro Helped: From First Prompt to Final Polish

`Prompts.md` is the most fascinating file in the `.kiro` folder. It is essentially the history of conversations with Kiro, including all of the key directives that influenced the development of the app. I iterated by altering my prompts rather than manually rewriting the entire application multiple times.

1. ### Vibe mode: first full version
    

The primary idea was outlined in the first prompt: a Daily Expense Tracker for Indian consumers with intelligent entry, analytics, budgets, and a high-end user interface. In response, Kiro created the basic manifest file, `styles.css`, `app.js`, and `index.html` all at once.

At this stage the app:

* Looked more like a mobile view centered on desktop.
    
* Had most of the logic, but charts and filters still needed work.
    

2. ### Desktop‑first redesign
    

The next set of prompts asked Kiro to:

* Use the full browser width.
    
* Move expense entry into a fixed left sidebar.
    
* Turn the main area into a dashboard with cards and tables.
    

Kiro rewrote the layout with a desktop‑first grid, fixed sidebar, and SaaS‑style header, which immediately made the app feel more professional and friendly.​

3. ### Bug fixing by conversation
    

During my testing, I discovered problems such as overflowing category buttons, unreadable dark-mode text, malfunctioning date filters, and non-rendering charts. Every issue was transformed into a brief, targeted prompt:

* “Fix category buttons that go out of bounds in the Add Expense section.”
    
* “Make dark‑mode text high‑contrast.”
    
* “Make ‘This Week’, ‘This Month’, and ‘All Time’ actually filter expenses and update totals.”
    

Then, while maintaining the current structure, Kiro modified CSS and JavaScript to address these issues. Additionally, it frequently updated validation algorithms, such as preventing future spending dates and accurately recalculating the header summary.

4. ### Documentation and guides for free
    

Finally, Kiro generated the markdown files you see in the `.kiro` directory:

* `requirements.md` – formal list of features, data model, and user stories.​
    
* `architecture.md` – description of modules, data flow, CSS architecture, and performance considerations.​
    
* `user-guide.md` – step‑by‑step instructions on how to use the app and understand the dashboard.
    
* `CONTRIBUTING.md` – guidelines for future contributors.
    
* `prompts.md` – record of how prompts evolved across iterations.
    

Writing this documentation by hand would typically take hours. Here, clear technical documents were created alongside the code using prompts and a few modifications.

***Every significant instruction I provided Kiro during the app's development was kept in a file named*** `prompts.md`***, allowing you to view the precise prompts that influenced each iteration. You can follow the complete prompt history step-by-step by opening this file directly in the GitHub repository that is linked in this blog.***

## A Quick Look at the Core Logic

Even novices are able to understand the application because it is coded in vanilla JavaScript. Based on the architecture description, the following is a brief summary of the core state object and the fundamental data flow:

* A single `state` object holds expenses, budget, reminders, profile, and dark‑mode state.
    
* `loadState()` pulls this data from LocalStorage when the page loads.
    
* `saveState()` writes it back whenever something changes.
    
* `updateUI()` refreshes the budget cards, tables, and charts so the screen is always in sync.
    

This structure makes it easy to add more features later, such as recurring expenses, exports, or even backend sync, without changing the overall pattern.

## Why This Approach Worked Well

Looking back, three things made this project smooth:

* **Clear requirements first** – Writing a requirements file with Kiro forced clarity about what the app should do before styling anything.​
    
* **Iterative prompts instead of big rewrites** – Each improvement (layout, charts, filters, validation) came from focused prompts rather than manually refactoring everything. The `prompts.md` file shows this evolution very clearly.
    
* **Built‑in documentation** – Having README, architecture, user guide, and contributing instructions generated alongside the code means anyone landing on the GitHub repo can understand the project quickly.​
    

Time-wise, it seemed like this combination of Kiro and manual testing reduced two or three days of hand-coding into a few concentrated sessions.

## Key Takeaways

* It is considerably simpler to direct an AI tool like Kiro and prevent random outputs with a precise requirements document.
    
* For serious web applications like expenditure trackers, a desktop-first design with a fixed sidebar and a simple dashboard works well.
    
* Keeping a single state object and simple data flow (action → state → LocalStorage → UI) makes the code easy to extend later.​
    
* Kiro is most powerful when used iteratively: start with a big “vibe” prompt, then send small, targeted prompts to fix layout, bugs, and UX problems.​
    
* Auto‑generated docs (`requirements.md`, `architecture.md`, `user-guide.md`, `prompts.md`) save a lot of time and make the project easier for others to understand.​
    

## Conclusion

It would typically take many days of design, coding, and documentation to create a fully functional Daily Expense Tracker from start, particularly with a sophisticated user interface and extensive feature set. In just a few concentrated sessions, a production-ready, India-focused budgeting solution with charts, insights, and documentation may be shipped by combining precise requirements with AWS Kiro and iterating through prompts.

This workflow demonstrates to developers and students how AI can serve as a useful coding partner: you maintain control over the product vision and testing, while Kiro speeds up repetitive tasks.