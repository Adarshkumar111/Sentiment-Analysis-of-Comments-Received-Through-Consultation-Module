# Sentiment Analysis of Comments Received Through Consultation Module

> **Project Type:** College Academic Project\
> **Complexity:** Medium\
> **Framework:** ASP.NET Core MVC (.NET 10)\
> **Language:** C#\
> **Database:** Microsoft SQL Server\
> **Sentiment Detection:** Rule-Based Keyword Matching\
> **AI/ML Usage:** None

------------------------------------------------------------------------

## 1. Project Overview

The **Sentiment Analysis of Comments Received Through Consultation
Module** is a web-based application developed using ASP.NET Core MVC and
SQL Server.

The system allows students or users to submit comments and feedback on
different consultation topics. It automatically categorizes each comment
into one of three sentiment categories:

-   **Positive**
-   **Negative**
-   **Neutral**

Sentiment detection will use a predefined keyword dictionary and simple
C# logic. The project will not use Artificial Intelligence, Machine
Learning, deep learning, generative AI, or external AI APIs.

Administrators can create consultations, manage feedback, view sentiment
analytics, search and filter comments, and generate reports.

## 2. Project Aim

To develop a web-based consultation management system that collects user
feedback and categorizes submitted comments into Positive, Negative, or
Neutral sentiments using a simple rule-based approach.

## 3. Project Objectives

1.  Provide a platform for users to submit feedback.
2.  Allow administrators to create and manage consultations.
3.  Automatically classify comments into Positive, Negative, and Neutral
    categories.
4.  Display sentiment statistics through charts and dashboards.
5.  Help administrators understand users' opinions and concerns.
6.  Generate consultation-wise feedback reports.
7.  Support anonymous feedback submission.

## 4. User Roles

The application will have two main roles.

  -----------------------------------------------------------------------
  Role                                Responsibilities
  ----------------------------------- -----------------------------------
  Admin                               Manage consultations, users,
                                      comments, analytics, and reports

  Student/User                        View active consultations and
                                      submit feedback
  -----------------------------------------------------------------------

### 4.1 Admin

-   Log in to the admin dashboard.
-   Create, edit, close, and manage consultations.
-   View submitted comments.
-   View sentiment analytics.
-   Search and filter feedback.
-   Mark comments as reviewed.
-   Generate and export reports.

### 4.2 Student/User

-   Register and log in.
-   View available consultations.
-   Submit comments and feedback.
-   Choose anonymous feedback where available.
-   View their previous submissions.

## 5. Functional Requirements and Modules

### Module 1: Authentication and Authorization

**Features:**

-   User registration.
-   User login and logout.
-   Admin login.
-   Role-based authorization.
-   Secure password hashing.
-   Basic profile management.

**Rules:**

-   Admin users can access admin functionalities.
-   Students can access student functionalities.
-   Students cannot access admin-only pages.
-   Passwords must never be stored as plain text.

### Module 2: Consultation Management

Administrators can create and manage consultation campaigns.

**Features:**

-   Create consultation.
-   View all consultations.
-   Edit consultation details.
-   Delete consultation when appropriate.
-   Activate or close a consultation.
-   Set start and end dates.

**Consultation fields:**

  Field            Description
  ---------------- ---------------------------
  ConsultationId   Unique consultation ID
  Title            Consultation title
  Description      Consultation details
  StartDate        Consultation start date
  EndDate          Consultation closing date
  Status           Active or Closed
  CreatedAt        Record creation date

**Example:**

-   **Title:** University Campus Facilities
-   **Description:** Share your feedback about campus facilities.
-   **Status:** Active

Only active consultations within their allowed date range should accept
new comments.

### Module 3: Comment and Feedback Management

Students can submit comments for active consultations.

**Features:**

-   View available consultations.
-   Submit feedback.
-   View previous submissions.
-   Anonymous feedback option.
-   Validate empty comments.
-   Store the submission date and time.

**Example:**

-   **Consultation:** University Campus Facilities
-   **Comment:** The library is good, but the canteen food is very
    expensive.

After submission, the system will automatically analyze the comment and
save its sentiment.

### Module 4: Rule-Based Sentiment Analysis

> **Important: This project does not use AI or Machine Learning.**

The application will use a predefined dictionary of positive and
negative keywords. A C# service will compare words in the submitted
comment with the dictionary and calculate the matching counts.

**Example positive keywords:**

-   Good
-   Excellent
-   Amazing
-   Helpful
-   Great
-   Beautiful
-   Clean
-   Satisfied

**Example negative keywords:**

-   Bad
-   Poor
-   Worst
-   Dirty
-   Expensive
-   Disappointing
-   Difficult
-   Unsatisfied

#### Sentiment detection process

1.  The student submits a comment.
2.  The application normalizes the text, for example by converting it to
    lowercase.
3.  The text is tokenized into words.
4.  The system checks words against the positive and negative keyword
    lists.
5.  It counts positive and negative matches.
6.  It assigns a sentiment category.
7.  The result is stored with the comment.

#### Classification rules

  Condition                                               Sentiment
  ------------------------------------------------------- -----------
  Positive keyword count is greater than negative count   Positive
  Negative keyword count is greater than positive count   Negative
  Both counts are equal, including zero matches           Neutral

**Examples:**

  Comment                                        Positive Count   Negative Count Result
  -------------------------------------------- ---------------- ---------------- ----------
  The library is good and excellent.                          2                0 Positive
  The canteen food is bad and expensive.                      0                2 Negative
  The university has a library.                               0                0 Neutral
  The service is good but the staff is rude.                  1                1 Neutral

**Limitations and handling:**

-   This is a basic keyword-matching system, not a
    language-understanding model.
-   It may not understand sarcasm, context, spelling variations, or
    complex sentences.
-   A phrase such as "not good" may be incorrectly classified as
    Positive if negation is not handled.
-   A simple negation rule can be added as an improvement, but the
    system will remain rule-based.
-   The keyword dictionary should be maintained and tested with
    representative comments.

### Module 5: Admin Dashboard and Analytics

The admin dashboard provides an overview of consultation activity and
feedback.

**Dashboard statistics:**

-   Total consultations.
-   Total registered students.
-   Total comments.
-   Positive comments.
-   Negative comments.
-   Neutral comments.
-   Recent feedback.

**Charts:**

-   Pie chart: Overall sentiment distribution.
-   Bar chart: Sentiment comparison by consultation.
-   Line chart: Daily or weekly comment trends.

Charts can be implemented using Chart.js.

### Module 6: Search and Filter

Administrators can find relevant comments using:

-   Sentiment type.
-   Consultation name.
-   Submission date.
-   Student name, where identity is available.
-   Keyword search.

**Example:** An administrator can view only negative comments submitted
for the "University Campus Facilities" consultation.

### Module 7: Anonymous Feedback

Students can submit feedback without displaying their identity in the
admin feedback list.

**Requirements:**

-   Provide an anonymous submission option.
-   Hide the student's identity in ordinary admin comment views.
-   Continue to display the comment and its sentiment.
-   Associate the submission with its consultation.
-   Apply suitable access controls to any stored identity information.

Anonymous feedback should not be described as fully untraceable if the
application retains the user's account association for security or audit
purposes.

### Module 8: Comment Review

Administrators can review submitted comments and track which feedback
has been handled.

**Features:**

-   Mark a comment as Reviewed.
-   View reviewed and pending comments.
-   Optionally add an internal admin note.
-   Filter comments by review status.

### Module 9: Report Generation

Administrators can generate reports for individual consultations.

**Report contents:**

-   Consultation details.
-   Total comments.
-   Positive comment count.
-   Negative comment count.
-   Neutral comment count.
-   Sentiment distribution.
-   Submission date range.

**Export formats:**

-   PDF
-   CSV

Reports can be generated using suitable .NET libraries.

## 6. Non-Functional Requirements

  Requirement       Description
  ----------------- ---------------------------------------------------------
  Security          Password hashing, authorization, and safe data handling
  Performance       Quick comment classification and dashboard loading
  Usability         Simple, clear, responsive interface
  Reliability       Correctly store comments and analysis results
  Maintainability   Organized MVC and service-based code
  Validation        Validate user input on both client and server
  Compatibility     Support modern desktop and mobile browsers

## 7. Database Design

The application will use Microsoft SQL Server.

### 7.1 Users

Stores admin and student account information.

  Column         Description
  -------------- -----------------------
  UserId         Primary key
  Name           User's name
  Email          Unique email address
  PasswordHash   Hashed password
  Role           Admin or Student
  CreatedAt      Account creation date

### 7.2 Consultations

Stores consultation information.

  Column           Description
  ---------------- --------------------------
  ConsultationId   Primary key
  Title            Consultation title
  Description      Consultation description
  StartDate        Start date
  EndDate          End date
  Status           Active or Closed
  CreatedAt        Creation date

### 7.3 Comments

Stores submitted feedback and its analysis result.

  Column           Description
  ---------------- ------------------------------------------------------------
  CommentId        Primary key
  ConsultationId   Foreign key
  UserId           Foreign key; nullable only if the chosen design permits it
  CommentText      Submitted comment
  Sentiment        Positive, Negative, or Neutral
  IsAnonymous      Whether identity is hidden in normal views
  ReviewStatus     Pending or Reviewed
  CreatedAt        Submission date and time

### 7.4 SentimentKeywords

Stores predefined sentiment keywords.

  Column          Description
  --------------- -------------------------------
  KeywordId       Primary key
  Word            Keyword
  SentimentType   Positive or Negative
  IsActive        Whether the keyword is in use

### 7.5 Reports (Optional)

Stores report-generation history if required.

  Column           Description
  ---------------- -----------------
  ReportId         Primary key
  ConsultationId   Foreign key
  GeneratedBy      Admin user ID
  GeneratedAt      Generation date
  ReportType       PDF or CSV

### 7.6 Database Relationships

-   One User can submit multiple Comments.
-   One Consultation can receive multiple Comments.
-   One Consultation can have multiple Reports.
-   SentimentKeywords contains the dictionary used by the sentiment
    service.

The sentiment result can be stored directly in the Comments table. A
separate Sentiment table is not required for the initial version.

## 8. Technology Stack

  Technology                   Purpose
  ---------------------------- -------------------------------
  C#                           Backend programming language
  ASP.NET Core MVC (.NET 10)   Web application framework
  Entity Framework Core        Object-relational mapping
  SQL Server                   Relational database
  HTML5                        Page structure
  CSS3                         Styling
  Bootstrap 5                  Responsive UI
  JavaScript                   Client-side interactions
  Razor Views                  Dynamic server-rendered pages
  LINQ                         Querying data
  Chart.js                     Analytics charts

## 9. Application Architecture

The application will follow the Model-View-Controller (MVC)
architecture, with a separate service for sentiment classification.

### View Layer

-   Razor Views
-   HTML
-   CSS
-   Bootstrap
-   JavaScript

### Controller Layer

-   AccountController
-   ConsultationController
-   CommentController
-   DashboardController
-   ReportController

### Business Logic / Service Layer

-   SentimentAnalysisService
-   Consultation validation
-   Comment validation
-   Analytics calculations
-   Report preparation

### Data Access Layer

-   Entity Framework Core
-   ApplicationDbContext
-   Models and database relationships

### Database Layer

-   Microsoft SQL Server

## 10. Suggested Project Folder Structure

``` text
ConsultationSentimentAnalysis/
│
├── Controllers/
│   ├── AccountController.cs
│   ├── ConsultationController.cs
│   ├── CommentController.cs
│   ├── DashboardController.cs
│   └── ReportController.cs
│
├── Models/
│   ├── User.cs
│   ├── Consultation.cs
│   ├── Comment.cs
│   ├── SentimentKeyword.cs
│   └── Report.cs
│
├── Data/
│   └── ApplicationDbContext.cs
│
├── Services/
│   └── SentimentAnalysisService.cs
│
├── Views/
│   ├── Account/
│   ├── Consultation/
│   ├── Comment/
│   ├── Dashboard/
│   └── Report/
│
├── wwwroot/
│   ├── css/
│   ├── js/
│   └── lib/
│
├── appsettings.json
└── Program.cs
```

This is a suggested structure. The exact folders and controllers can be
adjusted during implementation.

## 11. Application Workflow

1.  Admin logs in.
2.  Admin creates and activates a consultation.
3.  Student registers or logs in.
4.  Student views available consultations.
5.  Student submits a comment.
6.  The application validates the comment.
7.  The sentiment service checks the predefined keyword dictionary.
8.  The system classifies the comment as Positive, Negative, or Neutral.
9.  The comment and sentiment are saved in SQL Server.
10. Admin views comments and analytics on the dashboard.
11. Admin reviews feedback and generates reports.

## 12. Project Scope

### Included in the Initial Version

-   Admin and student authentication.
-   Consultation CRUD operations.
-   Comment submission.
-   Rule-based sentiment classification.
-   Positive, Negative, and Neutral categories.
-   Admin analytics dashboard.
-   Search and filter.
-   Anonymous feedback option.
-   Comment review status.
-   PDF and CSV report generation.

### Not Included

-   Machine Learning models.
-   Deep Learning.
-   Generative AI.
-   Chatbots.
-   External AI APIs.
-   Advanced Natural Language Processing.
-   Automated language translation.

## 13. Future Enhancements

The following improvements may be considered in a future version:

-   Multilingual keyword dictionaries.
-   Improved negation handling.
-   Additional emotion categories.
-   Email notifications.
-   Mobile application.
-   More advanced sentiment scoring.

These are optional future enhancements and are not required for the
initial college project.

## 14. Development Roadmap

  Phase      Development Work
  ---------- ----------------------------------------------------------
  Phase 1    Create ASP.NET Core MVC project and configure SQL Server
  Phase 2    Create models, DbContext, and database migrations
  Phase 3    Implement registration, login, and role authorization
  Phase 4    Implement consultation CRUD
  Phase 5    Implement comment submission and validation
  Phase 6    Develop the rule-based sentiment analysis service
  Phase 7    Build admin dashboard and charts
  Phase 8    Implement search, filters, and anonymous feedback
  Phase 9    Add comment review and report export
  Phase 10   Perform testing, validation, and UI improvements

## 15. Acceptance Criteria

The initial project will be considered complete when:

-   Admin and student users can log in with the correct permissions.
-   Admin can create, edit, and close consultations.
-   Students can submit comments to active consultations.
-   Each submitted comment receives a Positive, Negative, or Neutral
    classification using the rule-based service.
-   Comments and sentiment results are saved in SQL Server.
-   Admin can view sentiment counts and charts.
-   Admin can search and filter comments.
-   Anonymous feedback does not display the student's identity in the
    normal feedback view.
-   Admin can mark comments as reviewed.
-   Consultation reports can be exported in the supported formats.

## 16. Final Project Configuration

  -----------------------------------------------------------------------
  Item                                Final Decision
  ----------------------------------- -----------------------------------
  Project Name                        Sentiment Analysis of Comments
                                      Received Through Consultation
                                      Module

  Project Type                        Web-Based Application

  Programming Language                C#

  Framework                           ASP.NET Core MVC (.NET 10)

  Database                            SQL Server

  ORM                                 Entity Framework Core

  Architecture                        MVC with a separate service layer

  Sentiment Method                    Rule-Based Keyword Matching

  AI/ML                               Not Used

  Main Users                          Admin and Student

  Project Complexity                  Medium

  Target                              College Academic Project
  -----------------------------------------------------------------------

------------------------------------------------------------------------

## Conclusion

The proposed system provides a simple and effective way to collect,
organize, and analyze feedback received through consultation modules. By
using a rule-based sentiment analysis mechanism in C#, the application
can categorize comments without depending on AI, Machine Learning, or
external services.

The project combines CRUD operations, authentication, database
management, sentiment classification, analytics, and report generation
in a single ASP.NET Core MVC application. It is suitable for a
medium-level college project and can be extended in the future if
required.
