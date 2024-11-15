---
aliases: 
type: certification
status: <% await tp.system.suggester(["Current", "Expired", "In Progress", "Planned"], ["Current", "Expired", "In Progress", "Planned"]) %>
completion_date: 
expiration_date: 
cred_id: 
cred_url: 
created: <% tp.file.creation_date('YYYY-MM-DD HH:mm') %>
last_modified: <% tp.file.last_modified_date('YYYY-MM-DD HH:mm') %>
---

<%*
// Get title if not provided
let title = tp.file.title
if (title.startsWith("Untitled")) {
    title = await tp.system.prompt("Note Title");
    await tp.file.rename(title);
}
-%>

# <% title %>

## Study Notes
- 

## Exam Details
- Exam Code: 
- Score Required: 
- Time Limit: 
- Question Format: 

## Resources
- 

## Progress Log
<% tp.file.creation_date('YYYY-MM-DD') %>
-