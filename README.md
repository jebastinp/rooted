# rooted



PROJECT BRAND
Application Name

Rooted

Tagline

Rooted in God's Word.
Growing Every Day.

Logo

Use the uploaded Rooted logo.

Brand Colors

Primary
#0B5D3B

Secondary
#79C141

Accent
#A8D672

Background
#F8F4EC

Surface
#FFFFFF

Text
#1B1B1B

Secondary Text
#6B7280


# MASTER_PROMPT.md

# Bible Reading Tracker 2026 (Production Ready)

You are an Expert Software Architect, Senior Full Stack Engineer, UI/UX Designer, Database Architect and DevOps Engineer.

I want you to build an ENTIRE production-ready application from scratch.

Do NOT generate sample code.

Do NOT generate placeholders.

Do NOT leave TODOs.

Everything must work.

The final output must be a COMPLETE project.

------------------------------------------------------------

# PROJECT NAME

Bible Reading Tracker 2026

------------------------------------------------------------

# PURPOSE

This is NOT a Bible App.

Users already own physical Bibles or use Bible apps.

This application ONLY tracks daily Bible reading progress.

The church follows one reading plan for the whole year.

Members simply mark today's reading as completed.

------------------------------------------------------------

# TARGET USERS

Church Members

Youth Fellowship

Leaders

Admins

Super Admin

------------------------------------------------------------

# PLATFORM

Mobile-first Responsive Web App

Must work perfectly on

Android Chrome

iPhone Safari

Desktop

Tablet

PWA Ready

------------------------------------------------------------

# TECHNOLOGY STACK

Frontend

React 19
Vite
TypeScript
TailwindCSS
Shadcn UI
React Router
TanStack Query
React Hook Form
Framer Motion

Backend

FastAPI
Python 3.12
SQLAlchemy
Alembic
Pydantic

Database

Supabase PostgreSQL

Authentication

JWT

User ID Login

NO PASSWORD

NO OTP

NO EMAIL

NO GOOGLE LOGIN

------------------------------------------------------------

# LOGIN FLOW

User enters

User ID

Example

REH001

Backend checks database.

If valid

Create JWT

Store session

User stays logged in.

Logout available.

Admin also logs in using User ID.

Role determines access.

------------------------------------------------------------

# USER ROLES

Member

Leader

Admin

Super Admin

------------------------------------------------------------

# MOBILE NAVIGATION

Bottom Navigation

🏠 Home

📈 Progress

👥 Community

👤 Profile

------------------------------------------------------------

# USER FEATURES

## HOME

Modern premium dashboard.

Contains

Good Morning

User Name

Today's Reading

Day Number

Date

Old Testament Chapters

New Testament Chapters

Estimated Reading Time

Large "Mark as Completed" button

Current Streak

Overall Progress

Top 5 Readers

Verse of the Day

Church Announcement

Beautiful UI

------------------------------------------------------------

## MARK AS COMPLETED

One click.

If already completed

Disable button

Show Completed badge.

Update

Progress

Leaderboard

Statistics

Current Streak

Completion %

------------------------------------------------------------

## PROGRESS PAGE

Show

Overall %

Current Streak

Longest Streak

Days Completed

Weekly Progress

Monthly Progress

Books Completed

OT Progress

NT Progress

Achievement Cards

Calendar Heatmap

Beautiful graphs

------------------------------------------------------------

## COMMUNITY PAGE

Leaderboard

Top Readers

Announcements

Birthdays

Today's Readers

Community Statistics

NO CHAT

NO COMMENTS

NO POSTS

NO AUDIO

------------------------------------------------------------

## PROFILE

Photo

User ID

Role

Joined Date

Current Streak

Days Completed

Overall Progress

Achievements

Settings

Logout

------------------------------------------------------------

# ADMIN PANEL

Responsive Dashboard

Desktop First

------------------------------------------------------------

## DASHBOARD

Cards

Total Members

Today's Readers

Completion %

Current Reading Day

Current Streak

Charts

Reading Completion

Weekly Completion

Monthly Completion

Recent Activities

Top Readers

Announcements

------------------------------------------------------------

## MEMBER MANAGEMENT

Search

Filters

Pagination

Add Member

Edit Member

Deactivate Member

Delete Member

Bulk Import

Export

------------------------------------------------------------

Each member has

Name

User ID

Role

Phone

Status

Joined Date

Progress

Current Streak

------------------------------------------------------------

## READING PLAN

Table

Day

Date

Old Testament

New Testament

Estimated Minutes

Edit

Delete

Add Day

Search

Pagination

------------------------------------------------------------

## REPORTS

Reading Completion

Daily Reports

Weekly Reports

Monthly Reports

Member Reports

Leaderboards

Export Excel

------------------------------------------------------------

## ANNOUNCEMENTS

CRUD

Title

Description

Date

Expiry

Visibility

------------------------------------------------------------

## SETTINGS

Church Name

Church Logo

Reading Year

General Settings

------------------------------------------------------------

# CSV IMPORT

Very Important

There are NO CSV files now.

Later I will upload them.

Therefore create the feature.

CSV Import Wizard.

Supports

users.csv

reading_plan.csv

progress.csv

Each upload should

Validate

Preview

Import

Rollback on Error

Show statistics

Skip duplicates

Upsert existing rows

------------------------------------------------------------

users.csv

Will contain

User ID

Name

Role

Phone

Joined Date

------------------------------------------------------------

reading_plan.csv

Contains

Day

Date

Old Testament

New Testament

Estimated Minutes

------------------------------------------------------------

progress.csv

Contains

User ID

Day

Completed

Completed Date

------------------------------------------------------------

After importing

Automatically calculate

Current Streak

Longest Streak

Overall %

Leaderboard

Statistics

Everything.

------------------------------------------------------------

# DATABASE

Design proper normalized schema.

Include

Users

Reading Plan

Reading Progress

Announcements

Settings

Roles

Audit Logs

------------------------------------------------------------

Use

UUID Primary Keys

Indexes

Foreign Keys

Constraints

------------------------------------------------------------

# SUPABASE

I'll paste

SUPABASE_URL

SUPABASE_ANON_KEY

later.

Everything should already support Supabase.

------------------------------------------------------------

# UI

Use uploaded reference images.

DO NOT COPY.

Use them only as inspiration.

Make everything cleaner.

More premium.

More modern.

Apple-level UI.

Not Material Design.

Rounded Cards

Soft Shadows

Beautiful Typography

Responsive

Animations

------------------------------------------------------------

# PERFORMANCE

Lazy Loading

Image Optimization

Pagination

Code Splitting

Caching

Optimized Queries

------------------------------------------------------------

# SECURITY

JWT

Role Based Access

Protected Routes

Input Validation

Rate Limiting

Secure APIs

Environment Variables

------------------------------------------------------------

# API

REST API

Proper HTTP Status Codes

Validation

Swagger

------------------------------------------------------------

# CODE QUALITY

Professional Folder Structure

Reusable Components

Reusable Hooks

Reusable Services

Reusable APIs

Reusable Utilities

Clean Architecture

Zero duplicate code

------------------------------------------------------------

# TESTING

Frontend

Backend

Validation

CSV Import

API

------------------------------------------------------------

# README

Complete Documentation

Installation

Environment Variables

Supabase Setup

Run Commands

Deployment

CSV Import Guide

------------------------------------------------------------

# OUTPUT

The FINAL OUTPUT MUST be a SINGLE ZIP PROJECT.

The ZIP should contain EVERYTHING.

Project Structure

bible-reading-tracker/

frontend/

admin/

backend/

database/

supabase/

public/

assets/

README.md

.env.example

package.json

requirements.txt

docker-compose.yml

------------------------------------------------------------

# IMPORTANT

Do NOT stop midway.

Do NOT split responses.

Do NOT ask questions.

Generate the ENTIRE production-ready project.

Everything should compile.

Everything should run.

Everything should be connected.

Every page should work.

Every API should work.

Every database connection should work.

Every CRUD should work.

Every import should work.

Every report should work.

The application should be deployable immediately after I provide my Supabase credentials.

The final deliverable must be a SINGLE COMPLETE ZIP FILE.


All UI must consistently follow this branding.
APPLICATION PURPOSE
This application is NOT a Bible application.

Users already read using their own physical Bible or another Bible app.

This application only manages

• Daily Reading Plan
• Reading Completion
• Reading Progress
• Community Leaderboard
• Church Announcements

No Bible text should be stored inside this application.

No Audio Bible.

No Bible API.

No Bible Search.
PROJECT ARCHITECTURE
Use enterprise architecture.

Frontend

React

Reusable Components

Feature Based Folder Structure

Backend

FastAPI

Service Layer

Repository Layer

Database Layer

API Layer

Dependency Injection

Proper Logging

Central Exception Handling

Typed DTOs

Validation

Never place business logic inside controllers.
DATABASE REQUIREMENTS
Design a production-grade normalized PostgreSQL database.

Use UUID primary keys.

Use timestamps.

Use soft delete where appropriate.

Use created_at

updated_at

deleted_at

Use indexes.

Use foreign keys.

Use constraints.

Generate migration files.

Generate Supabase SQL.

Everything should be production ready.
USER AUTHENTICATION
Login using User ID only.

Example

REH001

No password.

After login

Issue JWT.

Store securely.

Refresh automatically.

Logout clears session.

Protected routes.

Role based authorization.
CSV IMPORT
CSV Import is one of the most important modules.

Support

users.csv

reading_plan.csv

progress.csv

The import system must

Preview data

Validate

Detect duplicate rows

Upsert records

Rollback if failed

Show summary

Generate import log

Store import history

Allow re-import safely

Support thousands of records.

Must not create duplicate progress.

Automatically recalculate

Current Streak

Longest Streak

Completion %

Leaderboard

Reports

Statistics

Everything automatically.
USER EXPERIENCE
Design should look like

Apple

Linear

Notion

Headspace

Minimal

Modern

Beautiful

Clean

Large spacing

Rounded cards

Soft shadows

Smooth animations

No Material Design look.

Mobile First.

Responsive.

PWA Ready.
PERFORMANCE
Application should easily support

1000+

Concurrent users.

Lazy loading

Code splitting

Virtualized tables

Image optimization

Caching

Optimized SQL

Pagination

Debounced search

Background sync

Offline capable PWA.
ADMIN FEATURES
Dashboard

Members

Reading Plan

Reports

Announcements

CSV Import

Settings

Audit Logs

Everything must support CRUD.

Bulk actions.

Search.

Pagination.

Filters.

Export Excel.

Export CSV.

Responsive.
REPORTS
Generate

Daily Report

Weekly Report

Monthly Report

Yearly Report

Member Report

Inactive Members

Most Consistent Readers

Top Readers

Completion %

Reading Statistics

Download Excel

Download CSV

Print Friendly
NOTIFICATIONS
Prepare notification architecture.

Although push notifications are not required now,

design the application so that Firebase or OneSignal can be integrated later without major refactoring.
CODE QUALITY
Professional coding standards.

Reusable components.

Reusable hooks.

Reusable services.

Reusable utilities.

Feature folders.

Strict TypeScript.

ESLint.

Prettier.

Zero duplicate code.

Meaningful naming.

Professional comments only where required.

No generated garbage.

No placeholder code.

No TODO comments.
ERROR HANDLING
Every API must return

Success

Failure

Validation errors

Authentication errors

Authorization errors

Proper HTTP status codes

Proper messages

Frontend should show elegant toast notifications.

Never crash.
TESTING
Create

Backend tests

Frontend tests

CSV import tests

API tests

Authentication tests

Validation tests

Critical workflows.

Everything should pass.
README
README must include

Project Overview

Architecture

Folder Structure

Installation

Supabase Setup

Environment Variables

Run Instructions

Deployment

CSV Import

Troubleshooting

Screenshots

Future Roadmap
FUTURE EXTENSIBILITY
Structure the application so that future modules can be added without changing the architecture.

Possible future modules

Attendance

Events

Prayer Requests

AI Devotions

Bible Notes

Church Groups

Push Notifications

Multi-Church Support

Donation Module

Admin Analytics

Design the architecture with scalability in mind.
FINAL OUTPUT
Instead of:
Generate the ENTIRE production-ready project as a SINGLE COMPLETE ZIP FILE.
Use:
Generate the complete production-ready project in the Claude Code workspace.

Create every required file and folder.

Continue until the entire application is implemented.

Do not stop after generating only part of the project.

The final project must compile, run, and be ready for deployment after Supabase credentials are provided.

No placeholder implementations.

No TODOs.

Every feature described in this specification must be fully functional.
This wording aligns much better with how Claude Code actually operates and will generally produce more reliable results than asking for a single ZIP in one response.
