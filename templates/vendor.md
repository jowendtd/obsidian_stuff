<%*
let vendor_name = await tp.system.prompt("Vendor Name")
await tp.file.rename(vendor_name + " Partner Info")
-%>
---
vendor_name: <%* tR += vendor_name %>
type: partner
aliases:
  - <%* tR += vendor_name %>
status: <% await tp.system.suggester(["active", "developing", "inactive"], ["active", "developing", "inactive"]) %>
category: <% await tp.system.suggester(["Hardware", "Software", "Cloud", "Security", "Network", "Data Center", "Managed Services"], ["Hardware", "Software", "Cloud", "Security", "Network", "Data Center", "Managed Services"]) %>
tags:
  - partner
  - vendor
created: <% tp.file.creation_date('YYYY-MM-DD HH:mm') %>
last_modified: <% tp.file.last_modified_date('YYYY-MM-DD HH:mm') %>
---

# <%* tR += vendor_name %>

# 🤝 Partnership Overview
## Partner Program Details
- Partnership Level: 
- Program Requirements:
  - Revenue Target: 
  - Certification Requirements: 
  - Training Requirements: 
- Partner Portal: 

## Key Contacts
### Channel Team
| Name | Role | Email | Phone | Territory |
|------|------|-------|-------|-----------|
|      |      |       |       |           |

### Technical Resources
| Name | Specialty | Email | Phone | Coverage |
|------|-----------|-------|-------|----------|
|      |           |       |       |          |

# 📚 Product Portfolio
## Solutions & Services
- Product Categories:
  - 
- Key Solutions:
  - 
- Service Offerings:
  - 

## Deal Registration
- Registration Portal: 
- Approval Process: 
- Margin Protection: 
- Expiration Terms: 

## Pricing Information
- Partner Discount Level: 
- Special Pricing Process: 
- Deal Registration Discount: 
- Volume Discounts: 

# 💡 Sales & Marketing
## Sales Resources
- Sales Portal: 
- Configuration Tools: 
- Quote Tools: 
- Demo Resources: 

## Marketing Programs
- MDF Available: 
- Co-marketing Options: 
- Campaign Resources: 
- Lead Generation Programs: 

## Training & Enablement
- Training Portal: 
- Required Certifications:
  - 
- Available Certifications:
  - 
- Demo Environment Access: 



# 🎯 Partnership Status
## Certification Status
| Certification | Holder | Expiry | Status |
|--------------|--------|--------|--------|
|              |        |        |        |

## Program Requirements
- [ ] Revenue Target
- [ ] Technical Certifications
- [ ] Sales Certifications
- [ ] Marketing Activities
- [ ] Customer Satisfaction

# 🛠️ Support Resources
## Technical Support
- Support Portal: 
- Partner Support Line: 
- Escalation Process: 
- Lab/Demo Environment: 

## Pre-Sales Support
- Solutions Architects: 
- Proof of Concept Process: 
- Design Review Services: 
- Configuration Assistance: 

## Training & Events
```dataview
TABLE
    date as "Date",
    type as "Type",
    attendees as "Attendees"
FROM "vendors/<%* tR += vendor_name %>/training"
SORT date desc
LIMIT 5
```

# 📅 Important Dates
- Partnership Renewal: 
- Certification Renewals: 
- Quarterly Business Review: 
- Training Deadlines: 

# 📎 Documentation
## Partner Resources
```dataview
TABLE file.mday as "Last Modified"
FROM "vendors/<%* tR += vendor_name %>/resources"
SORT file.mday desc
```

## Meeting Notes
```dataview
TABLE date, attendees
FROM "vendors/<%* tR += vendor_name %>/meetings"
SORT date desc
LIMIT 5
```

# 📌 Notes & Updates
- <% tp.date.now("YYYY-MM-DD") %>: Created partner note

---
Related:: [[Partners]] [[Vendors]]