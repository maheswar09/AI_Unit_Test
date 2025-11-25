# AI-Powered Multi-Agent Unit Test Generation System

## Architecture & Project Plan

---

## 1. Overview

This project aims to build an automated system that can **generate unit test cases using AI**.  
Developers spend a lot of time manually writing unit tests. This slows down development and reduces productivity.  
Our system uses **multiple AI agents** to automatically create, run, fix, and improve unit tests.

---

## 2. What Is the Current Problem?

### Today’s common issues:

- Developers must manually write unit tests.
- Writing tests is slow, repetitive, and sometimes ignored due to deadlines.
- Poor test coverage leads to bugs in production.
- Teams spend time fixing broken tests instead of building features.
- After every pull request or merge, new tests must be added manually.

This results in:

- Wasted developer hours
- Lower code quality
- Less automation
- Delayed releases

---

## 3. How We Are Solving the Problem

We will build a system where **multiple AI agents work together** to:

1. Read a code file
2. Understand its functions
3. Generate unit tests for them
4. Run the tests automatically
5. Fix tests if they fail
6. Check coverage
7. Commit test files back to the repo

This will:

- Save time
- Improve coverage
- Speed up releases
- Reduce human error
- Make development more productive

---

## 4. Why We Chose LangGraph

We evaluated CrewAI, AutoGen, and LangGraph.  
We chose **LangGraph** because:

- It allows us to build **clear workflows** like a flowchart.
- It supports **state management**, which is important when tests run, fail, and need fixing.
- It is more **stable for production**, especially for CI/CD environments.
- It allows **complex branching**, retries, loops, and conditional logic.
- It integrates well with modern LLMs and tools.

---

## 5. High-Level Architecture (Simple Explanation)

Think of this system like a team of robots working together.

### Main Agents:

1. **Analyzer Agent**

   - Understands the code, extracts functions, dependencies, edge cases
     
2. **Planning Agent**

   - Understands the file
   - Plans what tests must be created

3. **Test Generation Agent**

   - Writes the actual unit test code
     
4. **Mocker Agent**

   - Generates mocks for external dependencies, APIs, DB calls
   
5. **Execution Agent**

   - Runs the tests in a sandbox
   - Collects results

6. **Fixing Agent**

   - Reads test failures
   - Fixes broken test cases

7. **Coverage Agent**

   - Calculates how much code is tested
   - Ensures target coverage is met

9. **Reporting / Commit Agent**
   - Saves test files
   - Commits them to GitHub
   - Sends results to CI/CD

---

## 6. Full System Workflow

1. Developer submits a pull request
2. Analyzer Agent reads code and generates metadata
3. Planning agent splits this metadata into tasks
4. Test generation agent creates unit test file
5. Mocker injects mocks/stubs
6. Execution agent runs tests
7. If tests fail, fixing agent tries again
8. Coverage agent checks percentage
9. Final tests are committed to repo
10. CI/CD pipeline continues normally

---

## 7. Pros and Cons of This Approach

### Pros:

- Saves developer time
- Removes repetitive manual work
- Improves code quality
- Ensures consistent test coverage
- Works automatically after PR / merge

### Cons:

- Hard to design reliable test execution sandboxes
- Requires careful prompt design
- May generate overly broad tests without Analyzer Agent
- Running tests repeatedly may cost compute time
- Requires initial setup and workflow design
- Needs tuning for different tech stacks

---

## 8. Project Phases

### **Phase 1 – Basic Test Generation (MVP)**

- Use LangGraph
- Planner agent + Test generator agent + Executor agent
- Generate simple unit tests
- Run tests automatically
- Fix failures once
- Manual developer review

### **Phase 2 – Advanced Test System**

- Add code coverage agent, mocker agent
- Add retry loops for fixing failed tests
- Support for multiple languages (Python, JS, TS, Java)

### **Phase 3 – Full CI/CD Integration**

- Add analyzer agent
- Auto-run after every PR
- Add commit agent and auto-commit test files

### **Phase 4 – Notifications (optional)**

- Slack/Email notifications

---

## 9. Summary

We are building an AI-driven system that automatically generates and maintains unit tests.  
This will greatly improve developer productivity, reduce bugs, and automate repetitive work.  
Using LangGraph ensures we have a stable, scalable, and production-ready workflow.  
The system is divided into phases to ensure we build it gradually and safely.

---
