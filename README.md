# **Enterprise Multi-Tenant Bible Reading Progress Tracker - Complete System Architecture Prompt**

Build the existing **Bible Reading Progress Tracker** into a **production-ready, enterprise-grade, multi-tenant SaaS platform** that supports multiple churches, ministries, fellowships, Bible study groups, and organizations. The platform must be scalable, secure, and architected using modern SaaS principles with complete tenant isolation.

The application must have **three primary roles**:

* **Super User (Platform Owner)**
* **Admin (Church/Fellowship Leader)**
* **Member (Church Member)**

Every organization is completely isolated from one another. One Admin must never be able to view or access another Admin's members or data. The Super User has complete platform access.

---

# Overall Architecture

```
Platform (Rooted)

                    Super User
                         │
      ┌──────────────────┼──────────────────┐
      │                  │                  │
   Church A           Church B          Church C
    Admin               Admin             Admin
      │                  │                  │
 ┌────┴────┐        ┌────┴────┐       ┌────┴────┐
Member A1 A2       Member B1 B2      Member C1 C2
```

Each Admin owns an independent workspace.

Each workspace contains:

* Members
* Reading Plans
* Reading Progress
* Streaks
* Rewards
* Announcements
* Reports
* Leaderboards
* Dashboard
* Settings

No data can ever be shared across Admin workspaces.

---

# Authentication

## Super User Authentication

Authenticate using Supabase Authentication.

Login using:

* Gmail
* Email
* Password

The Super User logs into a dedicated platform dashboard.

Example

```
super@rooted.app
********
```

---

## Admin Authentication

Authenticate using Supabase Authentication.

Each Admin has:

* Email
* Password

created by the Super User.

Example

```
pastorjohn@church.org
********
```

Admins log into the Admin Portal.

---

## Member Authentication

Members do not use Supabase Authentication.

Members login using:

Member ID

or

Email (future support)

Example

```
Member ID

ROOT-000123
Password
```

The Admin creates Member accounts.

---

# Role Hierarchy

```
Super User
      │
Creates
      ▼
Admins
      │
Owns
      ▼
Members
      │
Reads
      ▼
Bible Reading Plan
      │
Creates
      ▼
Reading Progress
```

---

# SUPER USER RESPONSIBILITIES

The Super User is the platform owner.

The Super User manages the entire SaaS platform.

The Super User never creates Members.

The Super User only manages Admins.

The Super User has unrestricted access.

Features:

## Dashboard

Platform Statistics

* Total Churches
* Total Admins
* Total Members
* Active Members
* Active Reading Plans
* Today's Completed Readings
* Weekly Completion
* Monthly Completion
* Reading Streak Statistics
* Total Announcements
* Total Rewards
* Platform Usage
* New Registrations
* Active Organizations

Charts

* Member Growth
* Reading Completion Trend
* Organization Growth
* Active Users
* Daily Usage
* Monthly Activity

---

## Admin Management

Create Admin

Edit Admin

Deactivate Admin

Suspend Admin

Delete Admin

Reset Password

Assign Organization

Assign Church Name

Assign Fellowship

Assign Ministry

Assign Subscription

Assign Plan

Assign Limits

View Login History

View Activity Logs

Impersonate Admin

---

## Organization Management

View every organization

Search organizations

Filter organizations

View organization statistics

View organization reports

Deactivate organizations

---

## Member Monitoring

View every member

Search members

Filter members

View reading history

View reading streak

View activity

View reports

Reset Member Password

Deactivate Member

---

## Reading Plan Monitoring

View every reading plan

Edit any reading plan

Delete reading plans

Assign templates

Monitor completion

---

## Reports

Global Reports

Organization Reports

Admin Reports

Reading Reports

Leaderboard Reports

Growth Reports

CSV Export

Excel Export

PDF Export

---

## Platform Settings

Authentication

Branding

Notifications

Maintenance Mode

System Logs

Audit Logs

Platform Configuration

Feature Flags

Email Configuration

Backups

---

# ADMIN RESPONSIBILITIES

Each Admin represents one independent Church.

Examples

Grace Church

Faith Fellowship

Hope Ministries

Youth Fellowship

Bible Study Group

Each Admin only manages their own members.

An Admin cannot access another Admin.

Everything belongs to one Admin.

---

## Admin Dashboard

Dashboard Cards

Total Members

Today's Reading Completion

Weekly Completion

Monthly Completion

Reading Percentage

Current Reading Plan

Reading Streaks

Inactive Members

Announcements

Rewards

Leaderboards

Recent Activity

Charts

Daily Reading

Monthly Reading

Member Growth

Completion %

Reading Heatmap

Streak Analysis

---

## Member Management

Create Members

Edit Members

Delete Members

Deactivate Members

Reactivate Members

Import CSV

Bulk Create Members

Reset Password

Assign Member ID

Assign Reading Plan

Assign Groups

Assign Departments

Assign Family

View Member Activity

---

## Reading Plan Management

Create Plans

Edit Plans

Delete Plans

Assign Plans

Duplicate Plans

Import Plans

Export Plans

Future Plans

Calendar View

Schedule Reading

Automatic Publishing

---

## Reading Progress

Track Daily Reading

Track Completion

Track Missed Days

Track Streak

Track Percentage

View History

View Analytics

---

## Rewards

Create Rewards

Milestones

Badges

Achievements

Streak Rewards

Monthly Rewards

Yearly Rewards

---

## Leaderboard

Top Readers

Weekly

Monthly

Yearly

Most Consistent

Longest Streak

Perfect Attendance

---

## Announcements

Create Announcement

Edit Announcement

Delete Announcement

Schedule Announcement

Pin Announcement

Urgent Announcement

---

## Reports

Reading Reports

Attendance Reports

Completion Reports

Member Reports

Leaderboard Reports

CSV Export

Excel Export

PDF Export

---

## Settings

Church Details

Logo

Profile

Password

Notifications

Reading Preferences

Theme

Backup

---

# MEMBER RESPONSIBILITIES

Each Member belongs to exactly ONE Admin.

Members cannot move between organizations unless transferred.

Members only access their own information.

---

## Member Dashboard

Today's Reading

Progress

Current Streak

Longest Streak

Reading Percentage

Achievements

Rewards

Announcements

Upcoming Reading

Reading Calendar

Recent Activity

Profile

---

## Member Features

Mark Reading Complete

View Today's Reading

View Previous Reading

View Reading Calendar

View Streak

View Progress

View Rewards

View Achievements

View Leaderboard

Receive Announcements

Edit Profile

Change Password

Dark Mode

Notifications

---

# Database Design

The application must be fully multi-tenant.

Every table (except platform tables) must include:

```
admin_id UUID NOT NULL
```

Example Tables

Admins

```
id
email
password
church_name
status
created_at
```

Members

```
id
admin_id
member_id
name
email
phone
gender
dob
status
created_at
```

Reading Plans

```
id
admin_id
title
date
chapter
book
created_at
```

Reading Progress

```
id
admin_id
member_id
plan_id
completed
completed_at
```

Announcements

```
id
admin_id
title
description
published_at
```

Rewards

```
id
admin_id
title
badge
points
```

Leaderboards

```
id
admin_id
member_id
rank
score
```

Every query must filter using:

```
WHERE admin_id = current_admin_id
```

---

# Security

Implement enterprise-grade security.

Supabase Authentication

JWT Authentication

Refresh Tokens

Secure Sessions

Password Hashing

Role-Based Access Control (RBAC)

Row Level Security (RLS)

Tenant Isolation

API Authorization

Backend Authorization

Never trust frontend permissions.

Every API endpoint must validate permissions.

---

# Row Level Security

Super User

Can access every record.

Admin

Can only access records where:

```
admin_id = current_admin
```

Member

Can only access:

Own Profile

Own Reading Progress

Own Rewards

Own Announcements

Own Reading Plan

Nothing else.

---

# Navigation

## Super User Portal

Dashboard

Organizations

Admins

Members

Reports

Analytics

Audit Logs

Settings

Profile

---

## Admin Portal

Dashboard

Members

Reading Plans

Progress

Rewards

Announcements

Reports

Leaderboard

Settings

Profile

---

## Member Portal

Home

Today's Reading

Progress

Calendar

Rewards

Leaderboard

Announcements

Profile

---

# UI Requirements

Use a modern Apple-inspired premium UI with:

* Glassmorphism where appropriate
* Soft shadows and rounded cards
* Responsive layouts for desktop, tablet, and mobile
* Dark and Light themes
* Smooth Framer Motion animations
* Consistent spacing and typography
* Accessible color contrast and keyboard navigation
* Reusable component library

Each role (Super User, Admin, Member) must have its own distinct dashboard layout and navigation while maintaining a consistent brand identity.

---

# Performance

The application must support:

* 10,000+ Admin organizations
* 1,000,000+ Members
* 100,000+ daily active users
* High-performance server-side pagination
* Optimized database indexing
* Query caching
* Lazy loading
* Virtualized tables
* Background jobs for reports and notifications

---

# Technology Stack

* **Frontend:** React 19 + TypeScript + Vite + Tailwind CSS + Framer Motion + TanStack Query + Zustand
* **Backend:** FastAPI + SQLAlchemy 2.0 + Alembic + Pydantic v2
* **Database:** PostgreSQL (Supabase)
* **Authentication:** Supabase Auth (Super User & Admin), custom Member authentication
* **Storage:** Supabase Storage
* **Realtime:** Supabase Realtime
* **Deployment:** Vercel (Frontend), Render/Fly.io (Backend), Supabase (Database)

---

# Final Goal

Transform the existing Bible Reading Progress Tracker into a **production-ready, enterprise-grade, multi-tenant SaaS platform** where a single **Super User** manages multiple independent organizations, each **Admin** manages only their own church or fellowship and its members, and each **Member** has a secure, personalized Bible reading experience. The system must enforce strict tenant isolation, role-based access control, Supabase Row Level Security, scalable architecture, comprehensive auditing, and a premium user experience suitable for deployment to thousands of churches and ministries worldwide.



# Enterprise UI/UX Design Prompt – Apple Liquid Glass Bible Reading Progress Tracker

Design and rebuild the entire **Rooted – Bible Reading Progress Tracker** as a **premium Apple-inspired application** using the latest **Liquid Glass design language** (inspired by Apple's newest UI philosophy). The application should feel elegant, premium, modern, calm, and spiritually uplifting while remaining highly performant and production-ready.

This is **not** a basic CRUD application. It should feel like a premium native Apple application, similar to Apple Fitness, Apple Health, Apple Wallet, Apple Music, and Apple Journal.

The UI should combine **Liquid Glass**, **soft translucency**, **dynamic depth**, **glass reflections**, **fluid animations**, **micro interactions**, **premium typography**, and **minimalism**.

---

# Overall Design Philosophy

The design should communicate:

* Growth
* Faith
* Consistency
* Peace
* Achievement
* Motivation
* Community

Every screen should feel clean with plenty of white space, subtle gradients, and premium animations.

Avoid clutter.

Every interaction should feel smooth.

---

# Apple Liquid Glass Design System

Implement Apple's newest Liquid Glass design language throughout the application.

Features include:

* Frosted glass cards
* Dynamic translucent navigation bars
* Soft reflections
* Layered depth
* Dynamic blur backgrounds
* Floating UI elements
* Rounded continuous corners (28–36px radius)
* Glass morphism with realistic light refraction
* Adaptive light/dark mode
* Smooth spring animations
* Premium easing curves
* Soft shadows
* Floating bottom navigation
* Interactive glass buttons
* Animated gradients
* Frosted modals
* Glass sidebars
* Floating action buttons
* Dynamic hover states
* Subtle glow effects
* Beautiful loading skeletons
* Glass notification toasts

The application should feel like a native Apple application rather than a typical web application.

---

# Visual Style

Color Palette

Primary

Forest Green

Fresh Green

Emerald

Accent Gold

Warm White

Glass White

Soft Gray

Dark Graphite

Background

Use soft gradients with blurred floating shapes.

Example

White → Soft Green → Frosted Blur

Avoid flat backgrounds.

---

# Typography

Use premium typography.

Examples

SF Pro Display

Inter

Geist

Large bold headers

Minimal labels

Perfect spacing

Excellent readability

---

# Icons

Use premium outline icons.

Rounded icons.

Apple-like icons.

No heavy icons.

Use animated icons where appropriate.

---

# Animations

Every interaction should animate.

Examples

Card hover

Card expansion

Button press

Completion celebration

Achievement unlocked

Leaderboard update

Progress increase

Streak increment

Page transitions

Loading animations

Micro interactions

Confetti celebrations

Floating particles

Spring animations

Everything should feel alive.

---

# Dashboard Design

Every dashboard should contain beautiful glass widgets.

Examples

Today's Reading

Current Streak

Weekly Progress

Monthly Progress

Completion %

Achievements

Rewards

Leaderboard Position

Recent Activity

Reading Calendar

Reading Heatmap

Upcoming Reading

Announcements

Charts

Every card should have:

Glass background

Blur

Shadow

Gradient border

Animated number counters

Floating icon

---

# Member Experience

The Member dashboard should feel like Apple Fitness.

The homepage should immediately motivate users to continue reading.

Show

Today's Bible Reading

Continue Reading button

Reading Progress Ring

Weekly Progress Ring

Current Streak

Longest Streak

Achievement Showcase

Recent Badges

Reading Calendar

Motivational Verse

Upcoming Reading

Announcements

Daily Encouragement

Everything should animate beautifully.

---

# Achievement System

Build a comprehensive gamified achievement and badge system to encourage consistent Bible reading.

Achievements should unlock automatically when milestones are reached.

Each badge must have:

* Premium glass icon
* Gold accents
* Beautiful illustration
* Unlock animation
* Confetti celebration
* Progress tracker
* Description
* Date earned

Members should have a dedicated **Achievements Gallery** where all earned and locked badges are displayed in a collectible showcase.

---

# Achievement Categories

## Streak Achievements

* 🔥 First Day
* 🔥 3 Day Streak
* 🔥 7 Day Streak
* 🔥 14 Day Streak
* 🔥 30 Day Streak
* 🔥 50 Day Streak
* 🔥 100 Day Streak
* 🔥 180 Day Streak
* 🔥 365 Day Streak
* 🔥 Faithful Reader
* 🔥 Never Missed
* 🔥 Consistency Champion

---

## Weekly Completion Badges

Members receive a premium badge every time they complete an entire week's reading.

Examples:

Week 1 Completed

Week 2 Completed

Week 3 Completed

Week 4 Completed

52 Week Champion

These badges should display a beautiful gold laurel wreath with a green checkmark and glass finish.

---

## Monthly Achievements

* January Completed
* February Completed
* March Completed
* …
* December Completed

Special:

12 Month Champion

---

## Bible Reading Progress

* 10 Chapters Read
* 25 Chapters Read
* 50 Chapters Read
* 100 Chapters Read
* 250 Chapters Read
* 500 Chapters Read
* 1000 Chapters Read

---

## Book Completion Badges

Each completed Bible book earns a unique illustrated badge.

Examples:

Genesis Explorer

Matthew Disciple

Romans Scholar

Psalms Worshipper

Acts Messenger

Revelation Finisher

Each book should have its own premium icon inspired by its theme.

---

## New Testament Milestones

* First Gospel Completed
* Four Gospels Completed
* Paul's Letters Completed
* Entire New Testament Completed

---

## Community Achievements

Top 10 Reader

Top 5 Reader

Top 3 Reader

#1 Reader

Perfect Attendance

Encourager

Consistent Member

---

## Special Celebration Badges

Easter Reader

Christmas Reader

Good Friday Reader

Bible Month Champion

Church Anniversary Reading

Vacation Without Missing

Morning Reader

Night Reader

Weekend Warrior

---

## Hidden Legendary Badges

Secret achievements that are unlocked unexpectedly.

Examples

Early Bird

Night Watch

Grace Upon Grace

Faithful Servant

Rooted in Christ

Walking with God

The user should discover these naturally.

---

# Achievement Animations

When a badge is unlocked:

* Glass popup appears
* Background softly blurs
* Badge rotates into view
* Gold particles appear
* Leaves float upward
* Confetti animation
* Soft haptic feedback (mobile)
* Achievement sound (optional)
* "Achievement Unlocked" banner
* Automatically added to profile

This experience should feel similar to unlocking an achievement in Apple Fitness or completing an Apple Activity Ring.

---

# Profile Page

The profile should become a personal showcase.

Display:

Large profile image

Current Level

Reading Streak

Total Chapters

Completion %

Favorite Book

Achievement Collection

Recent Badges

Longest Streak

Weekly Performance

Monthly Performance

Reading Calendar Heatmap

Reading Statistics

Member Rank

Beautiful achievement gallery with horizontal scrolling glass cards.

---

# Leaderboard

Beautiful Apple-style leaderboard.

Top 3 users displayed as large floating glass podium cards with gold, silver, and bronze styling.

Remaining members displayed as elegant glass list cards.

Animate rank changes.

Show badges beside names.

---

# Rewards

Instead of plain points, use:

Faith Points (FP)

Members earn Faith Points for:

Daily reading

Weekly completion

Monthly completion

Streak milestones

Special events

Faith Points unlock cosmetic profile frames, badge borders, themes, and milestone rewards.

---

# Navigation

Floating bottom navigation bar with Liquid Glass styling.

Smooth page transitions.

Blurred floating top app bar.

Floating profile button.

Animated active indicators.

---

# Dark Mode

Create an exceptional dark mode.

Use:

Graphite

Black Glass

Emerald Glow

Soft White Text

Golden Highlights

No harsh colors.

Everything should maintain readability and elegance.

---

# Accessibility

Support:

Large text

Keyboard navigation

High contrast

Reduced motion

Screen readers

Accessible color ratios

---

# Technical Requirements

* React 19
* TypeScript
* Tailwind CSS
* Framer Motion
* Motion One where appropriate
* Lucide Icons
* React Spring for fluid interactions
* CSS backdrop-filter for Liquid Glass
* Reusable design system and component library
* Responsive layouts for mobile, tablet, and desktop
* Optimized performance with lazy loading and code splitting

---

# Final Goal

Create a **world-class, Apple-quality Bible Reading Progress Tracker** that feels like a premium native application rather than a web app. Every interaction should inspire users to stay consistent in their Bible reading through beautiful Liquid Glass visuals, meaningful animations, and a rewarding achievement system. The experience should motivate members to build lifelong reading habits while giving Super Users and Admins elegant, enterprise-grade dashboards. The final product should be polished enough to be featured on the App Store and serve thousands of churches worldwide with a delightful, accessible, and highly performant user experience.
