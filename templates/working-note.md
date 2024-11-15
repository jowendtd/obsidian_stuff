---
type: working-note
created: <% tp.file.creation_date('YYYY-MM-DD HH:mm') %>
last_modified: <% tp.file.last_modified_date('YYYY-MM-DD HH:mm') %>
tags: [working-note]
---
<%*
// Get title if not provided
let title = tp.file.title
if (title.startsWith("Untitled")) {
    title = await tp.system.prompt("Note Title");
    let titleName = tp.date.now("YYYY-MM-DD") + " - " + title
    await tp.file.rename(titleName);
}

// Get context (client, project, or internal)
const context = await tp.system.suggester(
    ["Client", "Vendor", "Project", "Internal"],
    ["client", "vendor", "project", "internal"]
);

// If client context, get client name
let client = "";
if (context === "client") {
    client = await tp.system.prompt("Client Name");
}

// If vendor context, get vendor name
let vendor = "";
if (context === "vendor") {
    vendor = await tp.system.prompt("Vendor Name");
}
-%>
# <% title %>

**Date**: <% tp.date.now("YYYY-MM-DD") %>
**Context**: <% context %>
<%* if (context === "client") { -%>
**Client**: <% client %>
<%* } -%>
<%* if (context === "vendor") { -%>
**Vendor**: <% vendor %>
<%* } -%>

## Notes
- 

## Action Items
- [ ] 

## Follow-ups
- 

## References
- 

---
<%* if (context === "client") { -%>
Client:: [[<% client %> Info]]
<%* } -%>
<%* if (context === "vendor") { -%>
Vendor:: [[<% vendor %> Info]]
<%* } -%>
Context:: #<% context %>