# miro-org-chart-export
A lightweight Miro Web SDK app that exports a clean CSV representation of:

- **People** (Name, Role)
- **Hierarchy** (manager → direct reports)
- **Teams** (Team: Alpha, Team: Beta, etc.)
- **Team membership** (each person can belong to one or many teams)

The CSV preserves reporting structure AND team structure using simple Miro conventions.

This app requires **no backend**, **no API keys**, and runs **entirely in the browser**.

## What This Exporter Solves
Miro’s native “Export to CSV” only outputs text — not relationships.  
This exporter reconstructs:

- Who reports to whom  
- Who belongs to which team(s)  
- Manager → team → person groupings  
- Frame boundaries (if you use a frame named `Org Chart`)

You click **Export CSV**, and a complete hierarchy + team map is generated.

# How to Structure Your Miro Board

## 1. People nodes  
People can be **cards**, **shapes**, **sticky notes**, or **text objects**.

**Format:**

Direction does **not** matter for person↔team relationships.

The exporter will treat these as **team memberships**.


# CSV Output Columns

The generated CSV includes:

| Column       | Meaning |
|--------------|---------|
| PersonName   | Person’s name |
| Role         | Person’s role/title |
| ManagerName  | Manager's name (blank if top-level) |
| TeamNames    | All teams the person belongs to (pipe-separated) |
| PersonId     | Miro object ID for this person |
| ManagerId    | Miro object ID of the manager |
| TeamIds      | ID(s) of team node(s) |
| ObjectType   | Miro object type (card/shape/text/sticky) |
| Frame        | Name of the frame containing the node (optional) |
| RawText      | Original text pulled from the shape/card |

# Installation 

This app is just a single `index.html` page.


1. Use the published HTTPS URL in the Miro app settings  
2. Install the app into your Miro team (you must get access to Miro Team Dev Hub)

(See detailed developer checklist below.)

# Usage

1. Open your Miro board  
2. Launch the **Org Chart CSV Exporter** from the Apps panel  
3. (Optional) Limit to a frame named `Org Chart`  
4. Choose whether "connector arrow points to **Manager**" or **Report**  
5. Click **Export CSV**  
6. Open the downloaded file in Excel / Google Sheets /. . . 

---

#  Troubleshooting

- **Someone missing?**  
  Ensure their first line contains a name (≥ 2 chars).

- **Manager wrong?**  
  Ensure connector direction matches the app’s setting.

- **Team missing?**  
  Ensure the team node name matches one of the formats above and is connected.

- **Too many items in export?**  
  Place your org chart inside a frame and enable “Limit to frame.”

