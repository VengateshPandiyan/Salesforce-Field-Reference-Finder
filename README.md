# Salesforce Field Reference Finder

Find where your Salesforce fields are used across Apex classes, LWC, Aura components, Visualforce pages, and more.

---

## What You Need

1. Your Salesforce project with `force-app/` folder containing the retrieved metadata
2. An Excel file with the fields you want to search for
3. Node.js installed on your machine

---

## Step 1: Prepare Your Input Excel

Create an Excel file with **two columns** (exact header names required):

| ObjectApiName | FieldApiName |
|---------------|--------------|
| Account | Industry |
| Custom_Object__c | Custom_Field__c |

Save this file anywhere on your computer.

---

## Step 2: Run the Tool

Open your terminal in the project folder and run:

```
npm run find:refs -- --input <path-to-your-excel>
```

**How to get the path:**
1. Right-click your Excel file
2. Select **Copy Path** (or "Copy as Path")
3. Paste it into the command

**Example:**
```
npm run find:refs -- --input /Users/john/Desktop/my_fields.xlsx
```

---

## Step 3: View the Results

The tool creates `field_references_output.xlsx` in the project folder with **3 tabs**:

### Tab 1: Field References
Every file where each field was found, with:
- Object and Field name
- Metadata type (Apex Class, LWC, etc.)
- File name
- How many times it appears
- Which line numbers

### Tab 2: Summary
One row per field showing:
- How many files it was found in
- Total number of matches
- Which metadata types use it

### Tab 3: Not Found
List of fields that weren't found anywhere in the codebase.

---

## Tips

- Use the **filter** on any column to narrow down results (e.g., filter Metadata Type = "Apex Class")
- Fields are color-coded in groups for easy scanning
- The search is **case-insensitive** — `stagename` will match `StageName`

---

## First Time Setup

If you haven't installed dependencies yet:

```
npm install
```

This only needs to be done once.
