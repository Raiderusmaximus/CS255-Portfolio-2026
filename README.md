# CS255-Portfolio-2026

CS-255 Systems Analysis and Design portfolio: DriverPass system design, UML diagrams, and reflections.

## Contents

- [DriverPass-Business-Requirements-Document.docx](DriverPass-Business-Requirements-Document.docx): Project One requirements document
- [DriverPass-System-Design-Document.docx](DriverPass-System-Design-Document.docx): Project Two system design document with UML diagrams

## Reflection

### 1. Summary of DriverPass and the client

DriverPass is a new driver-training company with no existing system for managing registrations, scheduling, or progress tracking. The company was founded on the observation that more than 65% of students who apply for a DMV driving exam fail, largely because they only review previous test questions. DriverPass combines online practice exams with on-the-road lessons from a licensed instructor.

The system I designed lets customers create an account, purchase one of three tiered packages, and schedule, modify, or cancel two-hour lessons online. Secretaries can make the same changes by phone or in person. Every lesson is matched to a specific driver, car, and time slot, and the system prevents double-booking. The owner can disable a package without developer help, and every reservation change is recorded with the user and a timestamp. The system also maintains a connection to the DMV so practice material stays current with rule and question changes.

### 2. What I did well

I kept the business requirements traceable. The requirements document converts the client interview into goals, objectives, and testable functional and nonfunctional requirements, so each one can be traced back to something the client actually said. For example, the owner's request to disable packages without a developer appears as a goal, an adaptability requirement, a functional requirement, and a limitation that only developers can add or remove a package.

I treated security and accountability as core requirements rather than add-ons. Account lockout after failed logins, time-limited password reset tokens, role-based access control, and an activity log all come directly from client needs and are specified in enough detail for a developer to implement. The login and password-reset activity diagrams and the login sequence diagram show how those rules work together.

I also documented scope limits. The requirements document states what the interview did not cover, including future features and the assumption that payments run through a third-party gateway. Writing those limits down makes it clear what the release does and does not promise.

### 3. What I would revise

The system design document does not fully match the requirements document. The requirements describe driver training with a fleet of 10 cars, assigned drivers, pickup and drop-off locations, and secretary-managed reservations. The design document describes an online learning and practice-test platform with DMV appointment scheduling, and it does not mention drivers, cars, secretaries, the owner dashboard, or the DMV connection. I would rewrite the use case, class, and sequence diagrams around the driver and car reservation model so the design reflects what the client asked for.

The design document also includes requirements the client never stated, such as GDPR and PCI compliance, support for 10,000 concurrent users, and 99% uptime. I would either confirm these with the client or label them as assumptions for review.

The class diagram should include the entities the requirements describe: Driver, Car, Lesson (reservation), and Payment, along with the package-disable flag and the pickup and drop-off fields. I would also specify who can unlock an account after lockout, since the requirements allow self-service password reset but do not say how a locked account is restored.

### 4. How I interpreted the user's needs

I grouped the interview into three main needs. Customers want self-service scheduling without calling the office. Staff need every lesson matched to a real driver and car. The owner wants direct control over packages and accountability for changes without relying on developers for routine business decisions.

Where needs conflicted, I gave priority to what the owner explicitly asked for, since the owner is the client. I also limited the release to what was discussed. The client did not identify future features, so anything beyond the interview is marked as out of scope and would need a follow-up conversation. I interpreted "offline" access to mean viewing previously synced data, not making live edits while disconnected, which matches the interview.

### 5. How I approach designing software

I start by identifying who uses the system and what each person needs to accomplish. I write requirements as statements that can be tested, then model the data and main workflows with UML before writing any code. That order makes the structure visible early, so problems surface during design rather than during development.

I check each design decision against the requirements and record assumptions I could not verify. Keeping the diagrams and requirements consistent is harder than it sounds. The mismatch between the two DriverPass documents in this portfolio is a reminder that a design can drift from its requirements, so I now check the diagrams against the requirements before treating a design as finished.
