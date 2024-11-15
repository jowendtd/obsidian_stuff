<%*
let client_name = await tp.system.prompt("Client Name")
await tp.file.rename(client_name + " Info")
-%>
---
client_name: <%* tR += client_name %>
type: client
aliases: 
  - <%* tR += client_name %>
status: <% await tp.system.suggester(["active", "prospective", "archived"], ["active", "prospective", "archived"]) %>
onboarding_date: <% tp.date.now("YYYY-MM-DD") %>
account_manager: 
technical_lead: 
tags:
  - client
created: <% tp.file.creation_date('YYYY-MM-DD HH:mm') %>
last_modified: <% tp.file.last_modified_date('YYYY-MM-DD HH:mm') %>
---

# <%* tR += client_name %>

# 🏢 Client Overview
## Company Information
- Industry: <% await tp.system.suggester(["Agriculture", "Education", "Energy/Utilities", "Finance", "Healthcare", "Manufacturing", "Retail", "Technology", "Transportation"], ["Agriculture", "Education", "Energy/Utilities", "Finance", "Healthcare", "Manufacturing", "Retail", "Technology", "Transportation"]) %>
- Size: <% await tp.system.suggester(["Small", "Mid-Market", "Large Enterprise"], ["Small", "Mid-Market", "Large Enterprise"]) %>
- Location: 
- Key Business Areas:
    - 

## Key Contacts
| Name | Role | Email | Phone |
|------|------|-------|-------|
|      |      |       |       |

# 🔑 Critical Information
## Services Contracted
<% await tp.file.include("[[Services Checklist]]") %>

# 💻 Technical Environment
## Infrastructure
- 

## Tools & Technologies
- 

## Access Information
```dataview
TABLE file.mday as "Last Modified"
FROM "Clients/<%* tR += client_name %>/access"
SORT file.mday desc
```

# 📝 Meeting History
```dataview
TABLE date, attendees
FROM "Clients/<%* tR += client_name %>/meetings"
SORT date desc
LIMIT 5
```

# 🗂️ Related Documents
```dataview
TABLE file.mday as "Last Modified"
FROM "Clients/<%* tR += client_name %>/documents"
SORT file.mday desc
```

# 📌 Notes & Updates
- <% tp.date.now("YYYY-MM-DD") %>: Created client note

---
Related:: [[Clients]]