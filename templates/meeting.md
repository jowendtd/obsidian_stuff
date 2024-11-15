---
type: meeting
date: <% tp.date.now("YYYY-MM-DD") %>
time: <% tp.date.now("HH:mm") %>
tags: [meeting]
created: <% tp.file.creation_date('YYYY-MM-DD HH:mm') %>
last_modified: <% tp.file.last_modified_date('YYYY-MM-DD HH:mm') %>
---
<%*
// Get title if not provided
let title = tp.file.title
if (title.startsWith("Untitled")) {
    title = await tp.system.prompt("Meeting Title");
    let titleName = tp.date.now("YYYY-MM-DD") + " - " + title
    await tp.file.rename(titleName);
}

// Get meeting type
const meetingType = await tp.system.suggester(
    ["Internal", "Client", "Vendor"],
    ["internal", "client", "vendor"]
);

// Get client or vendor name if applicable
let client = "";
let vendor = "";
if (meetingType === "client") {
    client = await tp.system.prompt("Client Name");
} else if (meetingType === "vendor") {
    vendor = await tp.system.prompt("Vendor Name");
}

// Get location/URL
const locationType = await tp.system.suggester(
    ["Virtual", "Office", "Client Site", "Other"],
    ["virtual", "office", "client_site", "other"]
);
const location = await tp.system.prompt("Meeting Location/URL");

// Get attendees with role specification
const internalAttendees = await tp.system.prompt("Internal Attendees (comma separated)");
const externalAttendees = await tp.system.prompt("External Attendees (comma separated)");
-%>
# <% title %>

**Type**: <% meetingType %>
**Date**: <% tp.date.now("dddd, MMMM DD, YYYY") %>
**Time**: <% tp.date.now("HH:mm") %>
<%* if (meetingType === "client") { -%>
**Client**: <% client %>
<%* } else if (meetingType === "vendor") { -%>
**Vendor**: <% vendor %>
<%* } -%>
**Location Type**: <% locationType %>
**Location/URL**: <% location %>

## 👥 Attendees
### Internal
<% internalAttendees.split(',').map(a => `- ${a.trim()}`).join('\n') %>

### External
<% externalAttendees.split(',').map(a => `- ${a.trim()}`).join('\n') %>

## 🎯 Meeting Objective
- 

## 📋 Agenda
1. 

## 💬 Discussion Points
### Topic 1
- 

### Topic 2
- 

## ✅ Action Items
- [ ] 

## 📌 Key Decisions
- 

## 📝 Additional Notes
- 

## 👉 Next Steps
- Next meeting date: 
- Key priorities:
    1. 

---
<%* if (meetingType === "client") { -%>
Client:: [[<% client %> Info]]
<%* } else if (meetingType === "vendor") { -%>
Vendor:: [[<% vendor %>]]
<%* } -%>
Meeting Type:: #meeting/<% meetingType %>