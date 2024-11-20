
# Maintenance Request Control Database Management System

# Overview
A database management system designed to simplify the submission, assignment, tracking, and resolution of maintenance requests. This system is tailored for industries like real estate, educational institutions, and facilities management to improve operational efficiency and transparency.

# Objectives
- Streamline the handling of maintenance requests to ensure prompt resolution.
- Provide reporting and analysis tools to help decision-making and enhance user satisfaction.
- Promote collaboration between tenants, property managers, and maintenance teams.

# Key Features
- Role-Based Access: Separate functionalities for tenants, property managers, and technicians.
- Real-Time Tracking: Status updates for maintenance requests with detailed logs.
- Reporting and Analysis: Generate insights on request trends, team performance, and efficiency.
- User-Friendly Interface: Simple workflows for request submissions and tracking.

# Entities and Relationships
- Property Management: Tracks properties and their managers.
- Users: Maintains tenant details, including property associations.
- Maintenance Requests: Logs maintenance issues and tracks their lifecycle.
- Maintenance Teams: Manages teams assigned to resolve specific issues.
- Categories: Defines types of issues and their priorities.
- Technicians: Maintains details of team members and their roles.
- Logs: Captures all actions and updates on requests for audit purposes.

# ER Diagram

<img width="545" alt="Screenshot 2024-11-20 at 10 17 37 AM" src="https://github.com/user-attachments/assets/32e003ba-6b04-49c7-bf6c-fee582de19cf">

# Technologies Used

- Database: MySQL
- Programming: SQL, Python
- Tools: SQL queries for insights and reporting
- Concepts: Entity-Relationship Modeling, Triggers, Stored Procedures

# SQL Features
- Triggers for logging changes to request statuses.
- Reports on:
    - Total requests by property and category.
    - Status breakdown (Open, In Progress, Completed).
    - Top properties and users by number of requests.

# Sample SQL Query
Example: Requests by Property and Category

SELECT  
    pm.PropertyName, 
    c.CategoryName, 
    COUNT(mr.RequestID) AS Total_Requests 
FROM  
    Property_Management pm 
JOIN  
    Users u ON pm.PropertyID = u.PropertyID 
JOIN  
    Maintenance_Requests mr ON u.UserID = mr.UserID 
JOIN  
    Category c ON mr.CategoryID = c.CategoryID 
GROUP BY  
    pm.PropertyName, c.CategoryName 
ORDER BY  
    pm.PropertyName, c.CategoryName;

# Results
- Enhanced visibility into maintenance operations.
- Improved tracking and resolution times for requests.
- Actionable insights into resource allocation and efficiency.

