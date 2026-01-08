# Git Introduction Notes

## What is Git?

Git is a **Distributed Version Control System (DVCS)** used to track changes in files, especially source code, over time.

In simple terms, Git helps you:
- Save different versions of your project
- Go back to any previous version when something breaks
- See what changed, when it changed, and who changed it
- Collaborate with others without overwriting each other’s work

Git is widely used in software development and works perfectly with platforms like GitHub, GitLab, and Bitbucket.

---

## What is a Version Control System (VCS)?

A **Version Control System** is a tool that records changes to files over time so you can:
- Review history
- Compare versions
- Recover older versions
- Work safely in teams

Think of it like **Google Docs for code**, but much more powerful.

---

## Types of Version Control Systems

### 1. Local Version Control System

- All versions are stored on your local machine
- Changes are saved as patches

**Problems:**
- No collaboration
- If your system crashes, everything is lost
- No backup or shared history

---

### 2. Centralized Version Control System (CVCS)

- One central server stores all versions
- Developers pull from and push to the server

**Pros:**
- Easy collaboration
- Central control

**Problems:**
- Single point of failure
- Server down = work stops
- Risk of losing full history

Examples: SVN, Perforce

---

### 3. Distributed Version Control System (DVCS)

- Every developer has a full copy of the repository
- Full history is available locally
- Works even without internet

**Advantages:**
- No single point of failure
- Faster operations
- Better collaboration

**Example:** Git

---

## Why Git Was Created

Git was created in **2005** by **Linus Torvalds**, the creator of Linux.

The Linux kernel project previously used a proprietary tool called BitKeeper. When free access was revoked, the community decided to build their own tool with these goals:

- Very fast
- Fully distributed
- Strong support for branching
- Handles large projects efficiently

Git successfully achieved all of these goals and became the industry standard.

---

## How Git Is Different from Other VCS

### 1. Snapshots, Not Differences

- Traditional systems store file differences
- Git stores **snapshots** of the entire project

If a file doesn’t change, Git simply links to the previous version instead of duplicating data.

---

### 2. Nearly Every Operation Is Local

- Most Git commands work locally
- No need to contact a server for history or diffs
- Faster and more reliable

---

### 3. Git Has Integrity

- Every object in Git is secured using a **SHA-1 hash**
- Any corruption or change is instantly detected

Example SHA-1:
```
24b9da6552252987aa493b52f8696cd6d3b00373
```

---

### 4. Git Only Adds Data

- Git rarely deletes data
- Almost everything can be undone
- Commits are very hard to lose

This makes Git extremely safe to use.

---

## Summary

Git helps developers:
- Track history
- Work safely
- Collaborate efficiently
- Recover from mistakes

It is fast, reliable, and essential for modern software development.

