# 🌐 Web Development From Scratch

> A structured, from-scratch journey to learn Web Development — from HTML, CSS, and JavaScript fundamentals to frontend, backend, databases, APIs, deployment, and full-stack applications.

This repository contains my **notes, code examples, exercises, experiments, and projects** while learning web development.

The goal is not simply to memorize syntax or copy tutorials. The goal is to understand **how the web works**, build things from scratch, and gradually become capable of building real applications independently.

---

## 📌 Table of Contents

- [About](#-about)
- [Learning Philosophy](#-learning-philosophy)
- [Roadmap](#-roadmap)
- [Repository Structure](#-repository-structure)
- [01 — Web Fundamentals](#01--web-fundamentals)
- [02 — HTML](#02--html)
- [03 — CSS](#03--css)
- [04 — JavaScript](#04--javascript)
- [05 — Git & GitHub](#05--git--github)
- [06 — Browser & Web APIs](#06--browser--web-apis)
- [07 — Frontend Development](#07--frontend-development)
- [08 — React](#08--react)
- [09 — Node.js](#09--nodejs)
- [10 — Express.js](#10--expressjs)
- [11 — REST APIs](#11--rest-apis)
- [12 — Databases](#12--databases)
- [13 — Authentication & Security](#13--authentication--security)
- [14 — Testing](#14--testing)
- [15 — Deployment & DevOps](#15--deployment--devops)
- [16 — Full-Stack Development](#16--full-stack-development)
- [17 — Projects](#17--projects)
- [18 — Practice](#18--practice)
- [19 — Progress Tracker](#19--progress-tracker)
- [20 — Technologies](#20--technologies)
- [21 — Resources](#21--resources)
- [22 — Learning Workflow](#22--learning-workflow)
- [23 — Final Goal](#23--final-goal)

---

# 📖 About

This repository is my personal **Web Development learning journey**.

Everything is organized progressively:

```text
Web Fundamentals
       ↓
HTML
       ↓
CSS
       ↓
JavaScript
       ↓
Git & GitHub
       ↓
Browser / DOM / APIs
       ↓
Frontend Development
       ↓
React
       ↓
Backend
       ↓
Node.js + Express
       ↓
REST APIs
       ↓
Databases
       ↓
Authentication & Security
       ↓
Testing
       ↓
Deployment
       ↓
Full-Stack Applications
       ↓
Real Projects
```

---

# 🧠 Learning Philosophy

For every important concept, I want to understand:

1. **What is it?**
2. **Why does it exist?**
3. **How does it work?**
4. **When should I use it?**
5. **What are its limitations?**
6. **Can I build something with it?**

The learning cycle is:

```text
Learn
  ↓
Understand
  ↓
Practice
  ↓
Build
  ↓
Break
  ↓
Debug
  ↓
Improve
```

---

# 🗺️ Roadmap

```text
WEB DEVELOPMENT
│
├── 00. Web Fundamentals
│
├── 01. HTML
│
├── 02. CSS
│
├── 03. JavaScript
│
├── 04. Git & GitHub
│
├── 05. Browser & Web APIs
│
├── 06. Frontend Development
│
├── 07. React
│
├── 08. Node.js
│
├── 09. Express.js
│
├── 10. REST APIs
│
├── 11. Databases
│
├── 12. Authentication & Security
│
├── 13. Testing
│
├── 14. Deployment
│
└── 15. Full-Stack Projects
```

---

# 🌐 01 — Web Fundamentals

Understand how the web actually works before going deep into frameworks.

### Topics

- Internet vs Web
- Client and Server
- Browser
- Web Server
- Domain Names
- DNS
- IP Addresses
- URLs
- HTTP
- HTTPS
- HTTP Methods
- HTTP Status Codes
- Request / Response
- Headers
- Cookies
- Sessions
- Caching
- CDN
- Hosting
- SSL/TLS basics

### Basic Request Flow

```text
User
 ↓
Browser
 ↓
DNS
 ↓
Server
 ↓
HTTP Request
 ↓
Application
 ↓
Database
 ↓
HTTP Response
 ↓
Browser
 ↓
Rendered Page
```

---

# 🏗️ 02 — HTML

HTML provides the structure of a webpage.

### Fundamentals

- HTML document structure
- Elements
- Tags
- Attributes
- Nesting
- Comments
- Head
- Body

### Text

- Headings
- Paragraphs
- Emphasis
- Quotes
- Code
- Lists

### Links

- Absolute URLs
- Relative URLs
- Anchor links
- Download links

### Images & Media

- Images
- `alt`
- Audio
- Video
- iframe

### Semantic HTML

- `header`
- `nav`
- `main`
- `section`
- `article`
- `aside`
- `footer`

### Forms

- Form structure
- Inputs
- Labels
- Buttons
- Select
- Textarea
- Checkboxes
- Radio buttons
- Validation

### Tables

- Rows
- Columns
- Headers
- Captions

### Accessibility

- Semantic HTML
- Accessible forms
- Keyboard navigation
- `alt`
- ARIA basics

---

# 🎨 03 — CSS

CSS controls presentation and layout.

### Fundamentals

- CSS syntax
- Selectors
- Classes
- IDs
- Cascade
- Specificity
- Inheritance

### Colors

- HEX
- RGB
- RGBA
- HSL

### Typography

- Font family
- Font size
- Font weight
- Line height
- Letter spacing
- Text alignment

### Box Model

```text
┌───────────────────────────┐
│          Margin           │
│   ┌───────────────────┐   │
│   │      Border       │   │
│   │  ┌─────────────┐  │   │
│   │  │   Padding   │  │   │
│   │  │ ┌─────────┐ │  │   │
│   │  │ │ Content │ │  │   │
│   │  │ └─────────┘ │  │   │
│   │  └─────────────┘  │   │
│   └───────────────────┘   │
└───────────────────────────┘
```

### Layout

- `display`
- Block
- Inline
- Inline-block
- Positioning
- `z-index`
- Overflow

### Flexbox

- Main axis
- Cross axis
- `justify-content`
- `align-items`
- `flex-direction`
- `flex-wrap`
- `gap`

### CSS Grid

- Rows
- Columns
- Grid areas
- `grid-template`
- `gap`

### Responsive Design

- Media queries
- Mobile-first design
- Relative units
- `rem`
- `em`
- `%`
- `vw`
- `vh`
- `clamp()`

### Advanced CSS

- CSS variables
- Transitions
- Transforms
- Animations
- Pseudo-classes
- Pseudo-elements
- Gradients
- Shadows
- Filters

---

# ⚡ 04 — JavaScript

JavaScript adds programming and dynamic behavior.

### Basics

- Variables
- `let`
- `const`
- Data types
- Operators
- Expressions
- Type conversion
- Type coercion

### Conditions

- `if`
- `else`
- `else if`
- Ternary operator
- `switch`

### Loops

- `for`
- `while`
- `do...while`
- `for...of`
- `for...in`

### Functions

- Function declarations
- Function expressions
- Arrow functions
- Parameters
- Return values
- Scope
- Closures

### Arrays

- Indexing
- `push`
- `pop`
- `shift`
- `unshift`
- `slice`
- `splice`
- `map`
- `filter`
- `reduce`
- `find`
- `some`
- `every`
- `sort`

### Objects

- Properties
- Methods
- Nested objects
- Destructuring
- Spread operator
- Optional chaining

### Strings

- Template literals
- String methods
- Searching
- Splitting
- Replacing

### Advanced JavaScript

- Execution context
- Call stack
- Scope chain
- Closures
- Hoisting
- `this`
- Prototypes
- Classes
- Modules
- ES6+

---

# 🧩 05 — Git & GitHub

Learn version control and development workflow.

### Git Fundamentals

- Repository
- Working directory
- Staging area
- Commit
- Branch
- Merge
- Remote

### Common Commands

```bash
git init
git status
git add
git commit
git log
git branch
git switch
git merge
git pull
git push
git clone
```

### GitHub

- Repositories
- README files
- Issues
- Pull requests
- Branches
- Releases
- GitHub Pages
- Collaboration

---

# 🌎 06 — Browser & Web APIs

Learn how JavaScript interacts with the browser.

### DOM

- Selecting elements
- Creating elements
- Modifying elements
- Removing elements
- Attributes
- Classes
- Styles

### Events

- Click
- Input
- Submit
- Keyboard events
- Mouse events
- Event bubbling
- Event delegation

### Browser APIs

- `localStorage`
- `sessionStorage`
- Fetch API
- URL API
- History API
- Clipboard API
- Geolocation basics

---

# 🖥️ 07 — Frontend Development

Combine HTML, CSS, and JavaScript into real applications.

### Topics

- UI architecture
- Component thinking
- Responsive layouts
- Forms
- Client-side validation
- API integration
- State management
- Loading states
- Error states
- Reusable components
- Accessibility
- Performance

---

# ⚛️ 08 — React

Learn modern component-based frontend development.

### Fundamentals

- Components
- JSX
- Props
- State
- Events
- Conditional rendering
- Lists
- Keys

### Hooks

- `useState`
- `useEffect`
- `useRef`
- `useMemo`
- `useCallback`
- Custom hooks

### Application Architecture

- Component structure
- State lifting
- Context
- Routing
- Forms
- API calls
- Error handling

### Advanced Topics

- Performance
- Code splitting
- Lazy loading
- Reusable components
- Application architecture

---

# 🟢 09 — Node.js

Run JavaScript outside the browser.

### Topics

- Node.js runtime
- npm
- `package.json`
- Modules
- CommonJS
- ES Modules
- File system
- Paths
- Environment variables
- Streams
- Events
- HTTP server

---

# 🚂 10 — Express.js

Build backend applications using Node.js.

### Topics

- Express setup
- Routing
- Middleware
- Request
- Response
- Route parameters
- Query parameters
- JSON
- Error handling
- Authentication middleware
- Backend architecture

---

# 🔌 11 — REST APIs

Learn how frontend and backend communicate.

### HTTP Methods

```text
GET       → Retrieve data
POST      → Create data
PUT       → Replace data
PATCH     → Update data
DELETE    → Delete data
```

### HTTP Status Codes

```text
2xx → Success

200 → OK
201 → Created
204 → No Content

4xx → Client Error

400 → Bad Request
401 → Unauthorized
403 → Forbidden
404 → Not Found

5xx → Server Error

500 → Internal Server Error
```

### API Concepts

- REST
- JSON
- CRUD
- Request body
- Query parameters
- Route parameters
- Headers
- Authentication
- Error responses
- API versioning

---

# 🗄️ 12 — Databases

Learn how applications store persistent data.

## SQL

- Tables
- Rows
- Columns
- Primary keys
- Foreign keys
- Relationships
- Constraints
- Indexes

### SQL Operations

```sql
SELECT
INSERT
UPDATE
DELETE
```

### Queries

- `WHERE`
- `ORDER BY`
- `GROUP BY`
- `HAVING`
- `JOIN`
- Aggregate functions
- Subqueries

## PostgreSQL

- Database creation
- Tables
- Relationships
- Queries
- Indexes
- Transactions

## MongoDB

- Documents
- Collections
- CRUD
- Queries
- Indexes
- Schema design

---

# 🔐 13 — Authentication & Security

Understand how applications protect users and data.

### Authentication

- Registration
- Login
- Logout
- Password hashing
- Sessions
- Cookies
- Tokens
- JWT

### Authorization

- Roles
- Permissions
- Protected routes

### Security

- HTTPS
- CORS
- CSRF
- XSS
- SQL Injection
- Password security
- Environment variables
- Input validation
- Rate limiting

Security should be considered while designing the application, not treated as an afterthought.

---

# 🧪 14 — Testing

Learn how to verify that applications behave correctly.

### Testing Types

- Unit testing
- Integration testing
- End-to-end testing

### Topics

- Test cases
- Assertions
- Mocking
- Test coverage
- API testing
- Browser testing

---

# 🚀 15 — Deployment & DevOps

Learn how applications go from a local computer to the Internet.

### Topics

- Production builds
- Environment variables
- Hosting
- Domains
- DNS
- HTTPS
- CI/CD
- Logs
- Monitoring
- Error tracking

### Deployment Flow

```text
Local Development
       ↓
Git
       ↓
GitHub
       ↓
Build
       ↓
Deploy
       ↓
Production
```

---

# 🧱 16 — Full-Stack Development

Combine everything into complete applications.

```text
                USER
                  │
                  ▼
              FRONTEND
                  │
                  │ HTTP
                  ▼
                 API
                  │
                  ▼
               BACKEND
                  │
                  ▼
              DATABASE
```

A full-stack application should handle:

- User interface
- User input
- Client-side logic
- API communication
- Server-side logic
- Database operations
- Authentication
- Authorization
- Error handling
- Deployment

---

# 🛠️ 17 — Projects

Projects are an important part of this repository.

## 🟢 Beginner

### 01. Personal Website

**Technologies**

```text
HTML
CSS
```

Concepts:

- Semantic HTML
- Layout
- Typography
- Responsive design

### 02. Landing Page

**Technologies**

```text
HTML
CSS
```

Concepts:

- Flexbox
- Grid
- Responsive design
- Reusable sections

### 03. Calculator

**Technologies**

```text
HTML
CSS
JavaScript
```

Concepts:

- DOM
- Events
- Functions
- State

### 04. To-Do Application

**Technologies**

```text
HTML
CSS
JavaScript
```

Concepts:

- DOM manipulation
- Arrays
- Objects
- Events
- Local storage

---

## 🟡 Intermediate

### 05. Weather Application

```text
HTML
CSS
JavaScript
REST API
```

Concepts:

- Fetch
- Async/await
- API requests
- JSON
- Error handling

### 06. Quiz Application

```text
HTML
CSS
JavaScript
```

Concepts:

- State
- Events
- Arrays
- Objects
- Dynamic UI

### 07. Expense Tracker

```text
HTML
CSS
JavaScript
LocalStorage
```

Concepts:

- Data management
- Forms
- CRUD
- Persistence

### 08. Movie Search Application

```text
HTML
CSS
JavaScript
API
```

Concepts:

- Search
- API integration
- Async programming
- Dynamic rendering

---

## 🔴 Advanced

### 09. Full-Stack Blog

```text
React
Node.js
Express
PostgreSQL
```

Features:

- User registration
- Login
- Create posts
- Edit posts
- Delete posts
- Comments
- Authentication

### 10. E-Commerce Application

```text
React
Node.js
Express
PostgreSQL
```

Features:

- Products
- Search
- Filtering
- Cart
- Authentication
- Orders
- Admin dashboard

### 11. Real-Time Chat Application

```text
React
Node.js
Express
WebSockets
Database
```

Features:

- Authentication
- Real-time messaging
- Online status
- Chat rooms
- Message history

---

# 🧩 18 — Practice

Practice will be divided into levels.

### Level 1 — Syntax

```text
Variables
Conditions
Loops
Functions
Arrays
Objects
```

### Level 2 — Logic

```text
Validation
Data transformation
Searching
Filtering
Sorting
State management
```

### Level 3 — Implementation

```text
Forms
Menus
Modals
Tabs
Search
Pagination
Authentication
API integration
```

### Level 4 — Projects

Combine multiple concepts into complete applications.

---

# 📊 19 — Progress Tracker

## Web Fundamentals

- [ ] Internet fundamentals
- [ ] HTTP
- [ ] DNS
- [ ] Client / Server
- [ ] Browser
- [ ] Request / Response

## HTML

- [ ] HTML basics
- [ ] Semantic HTML
- [ ] Forms
- [ ] Tables
- [ ] Media
- [ ] Accessibility

## CSS

- [ ] CSS fundamentals
- [ ] Box model
- [ ] Positioning
- [ ] Flexbox
- [ ] Grid
- [ ] Responsive design
- [ ] Animations
- [ ] Advanced CSS

## JavaScript

- [ ] Variables
- [ ] Data types
- [ ] Conditions
- [ ] Loops
- [ ] Functions
- [ ] Arrays
- [ ] Objects
- [ ] DOM
- [ ] Events
- [ ] Async JavaScript
- [ ] Promises
- [ ] Fetch
- [ ] Modules
- [ ] Advanced JavaScript

## Git & GitHub

- [ ] Git basics
- [ ] Branching
- [ ] Merging
- [ ] GitHub
- [ ] Pull requests
- [ ] GitHub workflow

## Frontend

- [ ] UI architecture
- [ ] Responsive design
- [ ] API integration
- [ ] State management

## React

- [ ] Components
- [ ] JSX
- [ ] Props
- [ ] State
- [ ] Hooks
- [ ] Routing
- [ ] Forms
- [ ] API integration

## Backend

- [ ] Node.js
- [ ] Express
- [ ] Middleware
- [ ] REST APIs
- [ ] Authentication
- [ ] Authorization

## Databases

- [ ] SQL
- [ ] PostgreSQL
- [ ] MongoDB
- [ ] Database design
- [ ] Relationships
- [ ] Indexes

## Deployment

- [ ] Production builds
- [ ] Hosting
- [ ] Domains
- [ ] HTTPS
- [ ] CI/CD
- [ ] Monitoring

---

# 🧰 20 — Technologies

### Core

```text
HTML
CSS
JavaScript
```

### Version Control

```text
Git
GitHub
```

### Frontend

```text
React
```

### Backend

```text
Node.js
Express.js
```

### Databases

```text
PostgreSQL
MongoDB
```

### APIs

```text
HTTP
REST
JSON
```

### Tools

```text
VS Code
Browser DevTools
npm
Terminal
Git
```

---

# 📂 Repository Structure

```text
web-development/
│
├── 00-web-fundamentals/
│   ├── notes/
│   ├── examples/
│   └── exercises/
│
├── 01-html/
│   ├── notes/
│   ├── examples/
│   └── exercises/
│
├── 02-css/
│   ├── notes/
│   ├── examples/
│   └── exercises/
│
├── 03-javascript/
│   ├── 01-basics/
│   ├── 02-control-flow/
│   ├── 03-functions/
│   ├── 04-arrays/
│   ├── 05-objects/
│   ├── 06-dom/
│   ├── 07-events/
│   ├── 08-async/
│   └── 09-apis/
│
├── 04-git-github/
│
├── 05-frontend/
│
├── 06-react/
│
├── 07-nodejs/
│
├── 08-express/
│
├── 09-apis/
│
├── 10-databases/
│
├── 11-authentication/
│
├── 12-testing/
│
├── 13-deployment/
│
├── 14-full-stack/
│
└── projects/
    ├── 01-personal-website/
    ├── 02-landing-page/
    ├── 03-calculator/
    ├── 04-todo-app/
    ├── 05-weather-app/
    ├── 06-quiz-app/
    ├── 07-expense-tracker/
    ├── 08-movie-app/
    ├── 09-blog/
    ├── 10-ecommerce/
    └── 11-chat-app/
```

---

# 🐛 Debugging Philosophy

Errors are part of development.

Instead of immediately searching for a complete solution:

```text
Read the error
      ↓
Understand the error
      ↓
Locate the problem
      ↓
Form a hypothesis
      ↓
Test the hypothesis
      ↓
Fix the problem
      ↓
Understand why it worked
```

The goal is to become capable of debugging independently.

---

# 🔄 Learning Workflow

For every new topic:

```text
1. Learn the concept
        ↓
2. Read documentation
        ↓
3. Write a small example
        ↓
4. Modify the example
        ↓
5. Break it intentionally
        ↓
6. Debug it
        ↓
7. Solve exercises
        ↓
8. Build a small feature
        ↓
9. Build a project
        ↓
10. Review the concept
```

---

# 📚 Resources

Resources will be added as the journey progresses.

### Documentation

- HTML documentation
- CSS documentation
- JavaScript documentation
- React documentation
- Node.js documentation
- Express documentation
- PostgreSQL documentation
- MongoDB documentation

### Other Resources

- Tutorials
- Articles
- Books
- Courses
- Practice platforms
- Project ideas

Documentation will be treated as an important source of truth rather than relying only on tutorials.

---

# 🎯 Milestones

### Milestone 1 — Understand the Web

```text
HTTP
DNS
Browser
Server
Request / Response
```

### Milestone 2 — Build Websites

```text
HTML
CSS
JavaScript
```

### Milestone 3 — Build Interactive Applications

```text
DOM
Events
APIs
Async JavaScript
```

### Milestone 4 — Modern Frontend

```text
React
Components
State
Hooks
Routing
```

### Milestone 5 — Backend

```text
Node.js
Express
REST APIs
Authentication
```

### Milestone 6 — Databases

```text
SQL
PostgreSQL
MongoDB
Database Design
```

### Milestone 7 — Full Stack

```text
Frontend
+
Backend
+
Database
+
Authentication
+
Deployment
```

---

# 🏁 Final Goal

The final goal is to reach the point where I can take an idea such as:

> "I want to build a web application where users can create accounts, store data, interact with other users, and access the application from anywhere."

and understand how to turn that idea into a working system.

```text
User Interface
      ↓
Frontend Logic
      ↓
HTTP / API
      ↓
Backend
      ↓
Authentication
      ↓
Database
      ↓
Security
      ↓
Deployment
      ↓
Production
```

The goal is not:

> **"I know React."**

The goal is:

> **"I understand enough of the web stack to build, debug, and deploy real applications."**

---

# 🚧 Current Status

```text
Learning Web Development From Scratch
```

This repository will continuously evolve as new concepts, exercises, experiments, and projects are completed.

---

## ⭐ Learning Log

| Date | Topic | Status |
|------|-------|--------|
| — | Web Fundamentals | 🔲 |
| — | HTML | 🔲 |
| — | CSS | 🔲 |
| — | JavaScript | 🔲 |
| — | Git & GitHub | 🔲 |
| — | Frontend | 🔲 |
| — | React | 🔲 |
| — | Backend | 🔲 |
| — | Databases | 🔲 |
| — | Full Stack | 🔲 |

---

> **Learn → Understand → Practice → Build → Break → Debug → Improve**
