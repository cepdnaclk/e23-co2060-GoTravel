---
layout: home
permalink: index.html

# Please update this with your repository name and project title
repository-name: e23-co2060-GoTravel
title: GoTravel
---

[comment]: # "This is the standard layout for the project, but you can clean this and use your own template, and add more information required for your own project"

<!-- Once you fill the index.json file inside /docs/data, please make sure the syntax is correct. (You can use this tool to identify syntax errors)

Please include the "correct" email address of your supervisors. (You can find them from https://people.ce.pdn.ac.lk/ )

Please include an appropriate cover page image ( cover_page.jpg ) and a thumbnail image ( thumbnail.jpg ) in the same folder as the index.json (i.e., /docs/data ). The cover page image must be cropped to 940×352 and the thumbnail image must be cropped to 640×360 . Use https://croppola.com/ for cropping and https://squoosh.app/ to reduce the file size.

If your followed all the given instructions correctly, your repository will be automatically added to the department's project web site (Update daily)

A HTML template integrated with the given GitHub repository templates, based on github.com/cepdnaclk/eYY-project-theme . If you like to remove this default theme and make your own web page, you can remove the file, docs/_config.yml and create the site using HTML. -->

# Project Title

GoTravel

## Team
-  E/23/122, P.H.S. Gunawardhana, e23122@eng.pdn.ac.lk(mailto:name@email.com)
-  E/23/116, D.M.N.N.L. Gunathilake, e23116@eng.pdn.ac.lk(mailto:name@email.com)
-  E/23/271, U.T.N Perera, e23271@eng.pdn.ac.lk(mailto:name@email.com)
-  E/23/270, T.N.D. Perera, e23270@eng.pdn.ac.lk(mailto:name@email.com)
<!-- Image (photo/drawing of the final hardware) should be here -->

<!-- This is a sample image, to show how to add images to your page. To learn more options, please refer [this](https://projects.ce.pdn.ac.lk/docs/faq/how-to-add-an-image/) -->

<!-- ![Sample Image](./images/sample.png) -->

#### Table of Contents
1. [Introduction](#introduction)
2. [Solution Architecture](#solution-architecture )
3. [Software Designs](#hardware-and-software-designs)
4. [Testing](#testing)
5. [Conclusion](#conclusion)
6. [Links](#links)

# TravelAt - Smart Travel Planning Made Simple
------------------------------------------------------------------------------------------------------------------------
## Introduction

Planning a trip should be exciting, not exhausting. GoTravel transforms the chaotic process of organizing travel into a seamless, enjoyable experience.

### The Problem

Modern travelers waste **8-12 hours** planning a single trip, juggling:
- 20+ browser tabs across booking sites and review platforms
- Scattered information in emails, screenshots, and notes
- Manual price comparisons with no centralized view
- Difficult coordination with travel companions
- Hidden costs that blow budgets

**The result?** Frustration, wasted time, and decision fatigue before the trip even begins.

### Our Solution

GoTravel is an AI-powered platform that brings everything into one intelligent workspace:

- **AI Recommendations** - Smart suggestions for destinations, activities, and itineraries tailored to you
- **Unified Dashboard** - All bookings and plans organized in one beautiful interface
- **Collaborative Planning** - Plan with friends and family in real-time
- **Smart Budgeting** - Track expenses automatically and stay on budget
- **Personalized Itineraries** - Custom day-by-day plans that match your style

### Impact

✨ **Save time** - Plan trips in minutes, not hours  
✨ **Reduce stress** - No more scattered tabs and lost information  
✨ **Travel smarter** - Make better decisions with organized, comprehensive data  
✨ **Stay on budget** - Clear cost visibility prevents overspending  

**Our mission:** Give travelers back the joy of planning, so they can spend less time stressing and more time dreaming about their next adventure.

------------------------------------------------------------------------------------------------------------------------------
## Solution Architecture

### High-Level Overview

GoTravel is built on a three-tier architecture with distinct presentation, application, and data layers, ensuring modularity, scalability, and maintainability.

### Architecture Diagram
```
┌─────────────────────────────────────────────────────────────────────────────────┐
│                            PRESENTATION LAYER                                    │
├──────────────┬──────────────┬──────────────┬──────────────┬─────────────────────┤
│              │              │              │              │                     │
│  Front Page  │ Login/Register│ Destination │  Hotel Page  │  Transport Page    │
│              │     Page     │     Page     │              │                     │
│              │              │              │              │                     │
└──────┬───────┴──────┬───────┴──────┬───────┴──────┬───────┴──────┬──────────────┘
       │              │              │              │              │
       │      ┌───────┴──────┐       │              │              │
       │      │              │       │              │              │
┌──────▼──────▼────┐  ┌──────▼───────▼──────────────▼──────────────▼──────┐
│                  │  │                                                    │
│    Traveler      │  │              Business Dashboard                   │
│    Dashboard     │  │                                                    │
│                  │  │                                                    │
└──────┬───────────┘  └──────┬─────────────────────────────────────────────┘
       │                     │
       └──────────┬──────────┘
                  │
┌─────────────────┴─────────────────────────────────────────────────────────────┐
│                          APPLICATION LAYER                                     │
├────────────────┬──────────────┬─────────────────────┬────────────────────────┤
│                │              │                     │                        │
│ Authentication │      AI      │ Hotel/Transport     │  Hotel/Transport      │
│    Service     │   Service    │ Searching Service   │  Storing Service      │
│                │              │                     │                        │
└────────┬───────┴──────┬───────┴──────────┬──────────┴────────┬───────────────┘
         │              │                  │                   │
         │              │                  │                   │
         │              └────────┬─────────┘                   │
         │                       │                             │
         │                  ┌────▼─────┐                       │
         │                  │          │                       │
         │                  │ Booking  │                       │
         │                  │ Service  │                       │
         │                  │          │                       │
         │                  └────┬─────┘                       │
         │                       │                             │
         └───────────────────────┼─────────────────────────────┘
                                 │
┌────────────────────────────────▼───────────────────────────────────────────────┐
│                               DATA LAYER                                        │
│                                                                                 │
│                          ┌─────────────────┐                                   │
│                          │                 │                                   │
│                          │    Supabase     │                                   │
│                          │    Database     │                                   │
│                          │                 │                                   │
│                          └─────────────────┘                                   │
│                                                                                 │
└─────────────────────────────────────────────────────────────────────────────────┘
```

### Architecture Components

#### **Presentation Layer**
- **Front Page** - Landing page and entry point
- **Login/Register Page** - User authentication
- **Destination Page** - Browse destinations
- **Hotel Page** - Search hotels
- **Transport Page** - Find transportation
- **Traveler Dashboard** - User trip management
- **Business Dashboard** - Provider management interface

#### **Application Layer**
- **Authentication Service** - User login & session management
- **AI Service** - Personalized recommendations
- **Hotel/Transport Searching Service** - Real-time availability search
- **Hotel/Transport Storing Service** - Inventory management
- **Booking Service** - Reservation processing

#### **Data Layer**
- **Supabase** - PostgreSQL database for all application data

### Data Flow

1. Users access frontend pages (Presentation Layer)
2. Authentication Service validates user sessions
3. AI Service provides personalized recommendations
4. Search services query stored inventory
5. Booking Service processes reservations
6. All data persists in Supabase database
-------------------------------------------------------------------------------------------------------------------------
## Software Design

### 1. System Architecture

#### 1.1 Architectural Pattern
TravelAt follows a **Three-Tier Architecture** with a lightweight frontend and serverless backend:
- **Presentation Layer** - HTML, CSS, JavaScript (Vanilla JS)
- **Application Layer** - Google Apps Script for business logic
- **Data Layer** - Supabase (PostgreSQL database)

This design ensures:
- **Simplicity** - No complex frameworks, easy to understand and maintain
- **Cost-Effective** - Serverless backend with minimal hosting costs
- **Scalability** - Supabase handles database scaling automatically
- **Fast Development** - Quick iterations without build processes

#### 1.2 Design Principles
- **Progressive Enhancement** - Core functionality works without JavaScript
- **Responsive Design** - Mobile-first approach
- **Separation of Concerns** - HTML for structure, CSS for styling, JS for behavior
- **Modular Code** - Reusable functions and components
- **Security First** - Client-side validation + server-side verification

---

### 2. Frontend Design

#### 2.1 Technology Stack
- **HTML5** - Semantic markup
- **CSS3** - Styling with Flexbox/Grid
- **Vanilla JavaScript** - No frameworks, pure JS
- **Supabase JS Client** - Database interaction from frontend



## Testing

### 1. Testing Overview

GoTravel is currently in the development phase. Testing has been conducted on completed modules and prototypes to validate core functionality and design decisions.

---

### 2. Completed Tests

#### 2.1 Authentication System
| Test Case | Expected Result | Status |
|-----------|----------------|--------|
| User Registration (Supabase) | Account created successfully | ✅ Pass |
| Login functionality | User authenticated, token generated | ✅ Pass |
| Logout functionality | Session cleared | ✅ Pass |
| Password validation | Weak passwords rejected | ❌ Fail (yet) |

#### 2.2 Database Operations
| Test Case | Expected Result | Status |
|-----------|----------------|--------|
| Insert data into Supabase | Data saved correctly | ✅ Pass |
| Retrieve data from tables | Data fetched successfully | ✅ Pass |
| Update existing records | Changes reflected in database | ✅ Pass |
| Delete records | Records removed properly | ✅ Pass |

#### 2.3 Frontend Components
| Test Case | Expected Result | Status |
|-----------|----------------|--------|
| Responsive layout (mobile) | Elements adapt to screen size | ✅ Pass |
| Form validation | Invalid inputs show errors |❌ Fail (yet)  |
| Navigation menu | Links work correctly | ✅ Pass |
| CSS styling consistency | Design matches mockups | ✅ Pass |

#### 2.4 AI Integration (Google Apps Script)
| Test Case | Expected Result | Status |
|-----------|----------------|--------|
| API connection test | Script responds successfully | ✅ Pass |
| Send request to OpenAI | Response received | ✅ Pass |
| Handle API errors | Error messages returned | ✅ Pass |

---

### 3. Browser Compatibility

Tested on available browsers:

| Browser | Status |
|---------|--------|
| Chrome | ✅ Working |
| Firefox | ✅ Working |
| Edge | ✅ Working |

---

#### Current Status
✅ Database connectivity functional  
✅ Authentication system working  
✅ Basic UI components responsive  
✅ AI integration tested successfully  
⏳ Full feature testing in progress  

#### Next Steps
- Complete remaining page development
- Implement full booking workflow
- Conduct comprehensive user testing
- Perform security audits
- Test with real user data

## Conclusion

### What Was Achieved

GoTravel successfully addresses the pain point of chaotic travel planning by consolidating the entire process into one intelligent platform. We have developed:

- A functional three-tier architecture with HTML/CSS/JS frontend and Supabase backend
- AI-powered recommendation engine using Google Apps Script and OpenAI
- User authentication and role-based dashboards (Traveler & Business)
- Core database structure for destinations, hotels, transport, and bookings
- Responsive web interface with modern UI/UX design

The project demonstrates the feasibility of creating a smart travel planning solution that saves users time and reduces decision fatigue.
## Links

- [Project Repository](https://github.com/cepdnaclk/{{ page.repository-name }}){:target="_blank"}
- [Project Page](https://cepdnaclk.github.io/{{ page.repository-name}}){:target="_blank"}
- [Department of Computer Engineering](http://www.ce.pdn.ac.lk/)
- [University of Peradeniya](https://eng.pdn.ac.lk/)

[//]: # (Please refer this to learn more about Markdown syntax)
[//]: # (https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
