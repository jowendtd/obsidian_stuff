<%*
let vendor_name = await tp.system.prompt("Vendor Name")
await tp.file.rename(vendor_name + " Certifications")
-%>
---
vendor: <%* tR += vendor_name %>
created: <% tp.file.creation_date('YYYY-MM-DD HH:mm') %>
last_modified: <% tp.file.last_modified_date('YYYY-MM-DD HH:mm') %>
---

# <%* tR += vendor_name %> Certifications

Partner Information: [[Vendors/<%* tR += vendor_name %>/<%* tR += vendor_name %> Partner Info]]

```dataview
TABLE
status,
completion_date as "Completion Date",
expiration_date as "Expiration Date",
cred_id as "Certification ID"
FROM "Vendors/<%* tR += vendor_name %>/training"
WHERE contains(file.frontmatter.type, "certification")
SORT expiration_date ASC
```

---