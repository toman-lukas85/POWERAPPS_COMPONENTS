# 🔒 KANBAN DEMO v1.0.0 - READ-ONLY VERSION

**Date:** February 9, 2026  
**Type:** Managed Solution (Read-Only)  
**Author:** Lukas Toman

---

## 📦 WHAT THIS PACKAGE CONTAINS

This package contains the **DEMO version** of the Kanban component, specifically designed for presentations and client demonstrations.

### ✅ What's enabled:
- ✅ **Drag & Drop** - Moving tasks between columns (updates status)
- ✅ **Full Visualization** - Displays cards, columns, and assigned users
- ✅ **Search & Filter** - Instantly find tasks and filter by criteria

### ❌ What's disabled:
- ❌ **Create** - Cannot create new tasks (the "New Task" button is hidden)
- ❌ **Edit** - Cannot edit existing tasks (clicking a card has no effect)
- ❌ **Delete** - Cannot delete tasks (the delete functionality is disabled)

---

## 📁 FOLDER CONTENTS

```
DEMO_READONLY/
├── KANBAN_DEMO_V1_0_0_1_MANAGED.zip   ← Solution file for import
├── SAMPLE_DATA.xlsx                    ← Sample data for Excel import
├── KANBAN_V16_7_0_DEPLOYMENT_GUIDE.md ← General deployment guide
└── DEMO_README.md                      ← This file
```

---

## 📊 SAMPLE DATA

### **How to import sample data:**

1. **Open Power Apps**
   ```
   https://make.powerapps.com
   ```

2. **Navigate to the "Developer Tasks" table**
   - Dataverse → Tables → Developer Tasks

3. **Import Data**
   - Click **Import** → **Import data from Excel**
   - Select the `SAMPLE_DATA.xlsx` file from this folder
   - Wait for the mapping. It should be automatic, but verify:
     - `lto_taskname` → Task Name
     - `lto_projectfeature` → Subtitle / Description
     - `lto_status` → Status (Backlog, In Progress, etc.)
     - `lto_type` → Type (UX, Dev, etc.)
     - `lto_assignedto` → Assigned To (User lookup)
     - `lto_storypoints` → Story Points
   - Click **Import**

### **The Sample Data includes:**
- ✅ 15 realistic tasks
- ✅ 4 different statuses (Backlog, In Progress, Code Review, Done)
- ✅ 3 task types (UX, Development, Testing)
- ✅ 4 assigned team members
- ✅ Story Points distribution (3, 5, 8, 13)

---

## 🚀 HOW TO IMPORT THE SOLUTION

### 1️⃣ **Go to Power Apps**
```
https://make.powerapps.com
```

### 2️⃣ **Import Solution**
1. Navigate to **Solutions**
2. Click **Import solution**
3. **Browse** → Select `KANBAN_DEMO_V1_0_0_1_MANAGED.zip`
4. Click **Next** → **Import**
5. Wait for the import to finish and click **Publish All Customizations**

### 3️⃣ **Add to Canvas App**
1. Create a new **Canvas App** (Tablet layout recommended)
2. Click **Insert** → **Get more components** → **Code**
3. Select **PowerKanban.BoardV8**
4. Drag the component onto your screen

### 4️⃣ **Connect to Data**
- Bind the component to your **Developer Tasks** table
- Map the required fields (Status, Title, Type, etc.)
- Add the **OnChange** formula as described in the `DEPLOYMENT_GUIDE.md`

---

## ⚠️ IMPORTANT NOTES

### **Managed Solution**
- ❌ Cannot be modified within Power Apps Studio
- ❌ The component secondary code is locked
- ✅ Safe for import into production/demo environments without accidental changes

### **For Development, Use the FULL Version**
- If you need to modify the source code or enable editing features, please use the `FULL_FOR_GIT` folder.
- There you will find the original TypeScript source code and an Unmanaged version of the solution.

---

## 🎯 RECOMMENDED USAGE

### **Ideal for:**
- ✅ Client presentations
- ✅ Sales demonstrations
- ✅ UAT (User Acceptance Testing) in read-only mode
- ✅ Showcasing board UI/UX and Drag & Drop behavior

### **NOT suitable for:**
- ❌ Production environments requiring task editing or deletion
- ❌ Developing new component features
- ❌ Customizing the core logic

---

## 📖 DOCUMENTATION

For detailed configuration (colors, font sizes, icons), please refer to:
- `KANBAN_V16_7_0_DEPLOYMENT_GUIDE.md`

---

## 📞 CONTACT

**Developer:** Lukas Toman  
**Email:** toman_lukas@icloud.com  
**Website:** https://lukastoman.figma.site/

---

**🔒 DEMO Version - Intended for presentations and demonstrations only!**
