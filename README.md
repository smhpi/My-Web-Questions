# Issue Tracker Application

Thank you for the opportunity to share my approach to coding. Below, I outline a code snippet from a feature I implemented in an **Issue Tracker** application built using React. This feature manages the filtering and handling of issues within a ticketing system, demonstrating my ability to design clean, maintainable, and user-centric solutions.

## Code Snippet
```javascript
import React, { useState } from 'react';

// Mock issue data
const issuesData = [
  { id: 1, title: "Login Bug", status: "Open", priority: "High" },
  { id: 2, title: "UI Glitch on Dashboard", status: "In Progress", priority: "Medium" },
  { id: 3, title: "Performance Issue", status: "Resolved", priority: "Low" },
];

function IssueTracker() {
  const [issues, setIssues] = useState(issuesData); // Holds the list of issues
  const [filter, setFilter] = useState({ status: "", priority: "" }); // Holds filter criteria

  // Filtered issues based on the current filter
  const filteredIssues = issues.filter(issue => {
    return (
      (filter.status ? issue.status === filter.status : true) &&
      (filter.priority ? issue.priority === filter.priority : true)
    );
  });

  // Handler for filter change
  const handleFilterChange = (e) => {
    const { name, value } = e.target;
    setFilter({ ...filter, [name]: value });
  };

  return (
    <div style={{ padding: "20px", fontFamily: "Arial, sans-serif" }}>
      <h1>Issue Tracker</h1>
      
      {/* Filter Controls */}
      <div style={{ marginBottom: "20px" }}>
        <label>
          Status:
          <select name="status" value={filter.status} onChange={handleFilterChange}>
            <option value="">All</option>
            <option value="Open">Open</option>
            <option value="In Progress">In Progress</option>
            <option value="Resolved">Resolved</option>
          </select>
        </label>

        <label style={{ marginLeft: "10px" }}>
          Priority:
          <select name="priority" value={filter.priority} onChange={handleFilterChange}>
            <option value="">All</option>
            <option value="High">High</option>
            <option value="Medium">Medium</option>
            <option value="Low">Low</option>
          </select>
        </label>
      </div>

      {/* Issue List */}
      <table style={{ width: "100%", borderCollapse: "collapse" }}>
        <thead>
          <tr>
            <th style={{ border: "1px solid #ddd", padding: "8px" }}>ID</th>
            <th style={{ border: "1px solid #ddd", padding: "8px" }}>Title</th>
            <th style={{ border: "1px solid #ddd", padding: "8px" }}>Status</th>
            <th style={{ border: "1px solid #ddd", padding: "8px" }}>Priority</th>
          </tr>
        </thead>
        <tbody>
          {filteredIssues.length > 0 ? (
            filteredIssues.map(issue => (
              <tr key={issue.id}>
                <td style={{ border: "1px solid #ddd", padding: "8px" }}>{issue.id}</td>
                <td style={{ border: "1px solid #ddd", padding: "8px" }}>{issue.title}</td>
                <td style={{ border: "1px solid #ddd", padding: "8px" }}>{issue.status}</td>
                <td style={{ border: "1px solid #ddd", padding: "8px" }}>{issue.priority}</td>
              </tr>
            ))
          ) : (
            <tr>
              <td colSpan="4" style={{ border: "1px solid #ddd", padding: "8px", textAlign: "center" }}>
                No issues match the selected filters.
              </td>
            </tr>
          )}
        </tbody>
      </table>
    </div>
  );
}

export default IssueTracker;
```

## Explanation

### Purpose
This component enables users to view and filter issues based on their status and priority, solving the problem of efficiently managing and visualizing large datasets by allowing targeted filtering.

### Decisions Behind the Design
1. **State Management:**
   - The `useState` hook is used for maintaining issue data and filter criteria. This approach provides a reactive and clean UI.
2. **Filtering Logic:**
   - Dynamic filtering logic ensures that users can view only the most relevant data based on their selected criteria. This logic is simple yet scalable for future extensions.
3. **User Experience:**
   - Dropdowns provide an intuitive way for users to apply filters, while a table layout ensures the data is presented in an organized, readable format.

### Scalability
The design is modular and easily extendable:
- Adding new filters or issue properties requires minimal code changes.
- Integration with an API or advanced state management (e.g., Redux) can be done seamlessly.

---
This example reflects my coding philosophy: clean, maintainable, and user-focused solutions. Feel free to reach out for further details or additional examples!

