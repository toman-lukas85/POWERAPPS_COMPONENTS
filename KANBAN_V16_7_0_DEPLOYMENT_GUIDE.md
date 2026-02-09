# KanBan Board v16.7.0 - Complete Deployment Guide

**Publisher:** Lukas Toman  
**Email:** toman_lukas@icloud.com  
**Website:** https://lukastoman.figma.site/  
**Version:** 16.7.0 (Unmanaged)  
**Release Date:** February 8, 2026

---

## 📦 Package Contents

This solution includes:
- ✅ **PCF Component** `PowerKanban.BoardV8` v16.7.0
- ✅ **Dataverse Table** `Developer Tasks` (lto_developertasks)
- ✅ **Canvas App** `Kanban Board App` (lto_refkanbanapp)
- ✅ **Sample Data** (Optional - can be added post-installation)

---

## 🚀 Installation Steps

### Prerequisites

#### 1. Power Platform Environment
- Environment with **Dataverse** enabled
- Access to [Power Apps Maker Portal](https://make.powerapps.com/)
- Access to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/)

#### 2. Required Security Roles ⚠️ **CRITICAL**
You **MUST** have one of the following security roles to import this solution:

- **System Administrator** (Recommended)
- **System Customizer**

**Why?** This solution creates a new Dataverse table (`Developer Tasks`), which requires the `prvCreateEntity` privilege.

**How to verify your role:**
1. Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/)
2. Select your environment → **Settings** → **Users + permissions** → **Users**
3. Find your user and check **Security roles**

**How to add the required role (if missing):**
1. In Power Platform Admin Center, go to your environment
2. **Settings** → **Users + permissions** → **Users**
3. Select your user
4. Click **Manage security roles**
5. Check **System Administrator** or **System Customizer**
6. Click **Save**
7. Wait 5 minutes for permissions to propagate
8. Refresh your browser and try the import again

#### 3. PCF Components Enabled
PCF (Power Apps Component Framework) must be enabled in your environment:

**Power Apps component framework for canvas apps** - Required for the Kanban component to work

**How to enable:**
1. Navigate to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/)
2. Select your environment → **Settings** → **Product** → **Features**
3. Enable **Power Apps component framework for canvas apps**
4. Click **Save**

#### 4. Allow Publishing of Canvas Apps with Code Components ⚠️ **REQUIRED**
Your environment must allow custom code components in Canvas Apps:

**How to enable:**
1. In [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/)
2. Select your environment → **Settings** → **Product** → **Features**
3. Scroll to **Power Apps**
4. Enable **Allow publishing of canvas apps with code components**
5. Click **Save**
6. Wait 5-10 minutes for the setting to propagate

**Why?** Without this setting, you won't be able to publish or run Canvas Apps that use PCF components like the Kanban Board.

### Step 1: Enable PCF Components (If Required)
**Note:** If you completed Prerequisites #3 and #4 above, skip this step.

1. Navigate to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/)
2. Select your environment → **Settings** → **Product** → **Features**
3. Enable both:
   - **Power Apps component framework for canvas apps**
   - **Allow publishing of canvas apps with code components**
4. Click **Save**
5. Wait 5-10 minutes before proceeding with the import

### Step 2: Import the Solution
1. Navigate to [Power Apps Maker Portal](https://make.powerapps.com/)
2. Select your target environment
3. In the left navigation, click **Solutions**
4. Click **Import solution**
5. Click **Browse** and select `KANBAN_V16_7_0_UNMANAGED.zip`
6. Click **Next**
7. Review the solution details:
   - **Name:** KanBan Board
   - **Version:** 16.7.0.0
   - **Publisher:** Lukas Toman
8. Click **Import**
9. Wait for the import to complete (typically 1-3 minutes)
10. Once complete, click **Publish all customizations**

### Step 3: Verify Installation
1. In **Solutions**, open the **KanBan Board** solution
2. Verify the following components are present:
   - **Table:** Developer Tasks (lto_developertasks)
   - **PCF Control:** PowerKanban.BoardV8
   - **Canvas App:** Kanban Board App

### Step 4: Open the Canvas App
1. In the solution, click on the **Kanban Board App**
2. Click **Play** to run the app
3. The Kanban board should display with default columns:
   - Backlog
   - In Progress
   - Code Review
   - Done

---

## 📊 Developer Tasks Table Structure

The `Developer Tasks` table includes the following fields:

| Display Name | Schema Name | Data Type | Description |
|---|---|---|---|
| **Task Name** | lto_taskname | Single Line Text | Primary title of the task |
| **Project/Feature** | lto_projectfeature | Single Line Text | Subtitle/context (e.g., "Auth Module") |
| **Status** | lto_status | Choice | Task status (Backlog, In Progress, Code Review, Done) |
| **Type** | lto_type | Multi-Select Choice | Task category (UX, UI, Development, Testing, Architecture, Documentation, Project Management) |
| **Story Points** | lto_storypoints | Whole Number | Effort estimation (1, 2, 3, 5, 8, 13) |
| **Assigned To** | lto_assignedto | Lookup (User) | User assigned to the task |

### Status Choice Values
- **Backlog** - Value: `100000000` - Color: `#605E5C` (Gray)
- **In Progress** - Value: `100000001` - Color: `#0078D4` (Blue)
- **Code Review** - Value: `100000002` - Color: `#8764B8` (Purple)
- **Done** - Value: `100000003` - Color: `#107C10` (Green)

### Type Choice Values
- **UX** - Value: `100000000` - Color: `#E3008C` (Magenta)
- **UI** - Value: `100000001` - Color: `#8764B8` (Purple)
- **Development** - Value: `100000002` - Color: `#0078D4` (Blue)
- **Testing** - Value: `100000003` - Color: `#00B7C3` (Cyan)
- **Architecture** - Value: `100000004` - Color: `#498205` (Green)
- **Documentation** - Value: `100000005` - Color: `#FFB900` (Yellow)
- **Project Management** - Value: `100000006` - Color: `#D13438` (Red)

---

## 🎨 Customization & Configuration

### PCF Component Properties

The Kanban component can be fully customized through its properties in the Canvas App:

#### Global Styling
| Property | Type | Default | Description |
|---|---|---|---|
| **Global Accent Color** | Text | `#4f46e5` | Primary color for buttons and interactive elements |
| **Board Background Color** | Text | `#f8fafc` | Background color of the entire board |
| **Border Radius (px)** | Number | `20` | Rounded corners for cards, buttons, and dialogs |
| **Global Font Family** | Enum | Segoe UI | Font family (Segoe UI, Arial, Roboto, Inter, etc.) |

#### Header Section
| Property | Type | Default | Description |
|---|---|---|---|
| **Header Title Text** | Text | "Kanban Board" | Main header title |
| **Header Subtitle Text** | Text | "Manage your tasks efficiently" | Subtitle below the title |
| **Header Color** | Text | `#ffffff` | Header background color |
| **Transparent Header** | Boolean | false | Makes header background transparent |

#### Column Styling
| Property | Type | Default | Description |
|---|---|---|---|
| **Column Background Color** | Text | `#f3f2f1` | Background color of columns |
| **Column Color Mapping** | Text | - | Override column colors (see JSON section below) |

#### Card Styling
| Property | Type | Default | Description |
|---|---|---|---|
| **Card Title Size** | Enum | 15px | Font size for card titles |
| **Card Title Weight** | Enum | 600 | Font weight for card titles |
| **Card Desc Size** | Enum | 13px | Font size for card descriptions |

#### Type/Category Styling
| Property | Type | Default | Description |
|---|---|---|---|
| **Type Color Mapping** | Text | - | Override type tag colors (see JSON section below) |

#### Search & Filter
| Property | Type | Default | Description |
|---|---|---|---|
| **Search Placeholder** | Text | "Search tasks..." | Placeholder text for search input |
| **Filter Button Text** | Text | "Filter" | Label for filter button |
| **Filter Button Icon** | Enum | Filter | Icon for filter button (Filter, Funnel, Sort) |

#### New Task Button
| Property | Type | Default | Description |
|---|---|---|---|
| **New Task Button Text** | Text | "New Task" | Label for the create task button |

---

## 🎨 JSON Configuration for Custom Colors

### Status Choices JSON
Use this property to define custom colors for status columns:

**Property Name:** `statusChoicesJSON`

**Format:**
```json
[
  { "label": "Backlog", "value": "100000000", "color": "#605E5C" },
  { "label": "In Progress", "value": "100000001", "color": "#0078D4" },
  { "label": "Code Review", "value": "100000002", "color": "#8764B8" },
  { "label": "Done", "value": "100000003", "color": "#107C10" }
]
```

**Example - Custom Colors:**
```json
[
  { "label": "Backlog", "value": "100000000", "color": "#FF5733" },
  { "label": "In Progress", "value": "100000001", "color": "#33C1FF" },
  { "label": "Code Review", "value": "100000002", "color": "#9D33FF" },
  { "label": "Done", "value": "100000003", "color": "#33FF57" }
]
```

### Type Choices JSON
Use this property to define custom colors for type tags on cards:

**Property Name:** `typeChoicesJSON`

**Format:**
```json
[
  { "label": "UX", "value": "100000000", "color": "#E3008C" },
  { "label": "UI", "value": "100000001", "color": "#8764B8" },
  { "label": "Development", "value": "100000002", "color": "#0078D4" },
  { "label": "Testing", "value": "100000003", "color": "#00B7C3" },
  { "label": "Architecture", "value": "100000004", "color": "#498205" },
  { "label": "Documentation", "value": "100000005", "color": "#FFB900" },
  { "label": "Project Management", "value": "100000006", "color": "#D13438" }
]
```

**Example - Custom Colors:**
```json
[
  { "label": "UX", "value": "100000000", "color": "#FF1493" },
  { "label": "UI", "value": "100000001", "color": "#9370DB" },
  { "label": "Development", "value": "100000002", "color": "#1E90FF" },
  { "label": "Testing", "value": "100000003", "color": "#20B2AA" },
  { "label": "Architecture", "value": "100000004", "color": "#32CD32" }
]
```

### Quick Color Mapping (Alternative)
If you prefer a simpler string format instead of JSON:

**Column Color Mapping:**
```
100000000:#FF5733;100000001:#33C1FF;100000002:#9D33FF;100000003:#33FF57
```

**Type Color Mapping:**
```
UX:#FF1493;UI:#9370DB;Development:#1E90FF;Testing:#20B2AA;Architecture:#32CD32
```

---


---

## 🔄 Using the Component in Other Apps

The `PowerKanban.BoardV8` component can be reused in **any Canvas App or Model-Driven App** within the same environment.

### In Canvas Apps:
1. Open your Canvas App in edit mode
2. Click **Insert** (+) → **Get more components**
3. Switch to the **Code** tab
4. Find **PowerKanban.BoardV8** (Publisher: Lukas Toman)
5. Click **Import**
6. Drag the component onto your screen
7. Configure the `kanbanDataSet` property to point to your table
8. Map the fields (Status, Title, Description, Type, Value, User)
9. Add the `OnChange` formula (adapt field names to your table)

### In Model-Driven Apps:
1. Open your Model-Driven App in the App Designer
2. Navigate to the form or view where you want to add the Kanban
3. Add a **Custom Control**
4. Select **PowerKanban.BoardV8**
5. Configure the data binding
6. Save and publish

### Using with Custom Tables
The component works with **any Dataverse table** that has:
- A **Choice field** for status (defines columns)
- A **Text field** for title
- Optional: Text field for subtitle, Number field for value, Lookup field for user, Multi-Select Choice for type

**Example with a "Production Plan" table:**
- Status field: `edscha_status` (Planned, In Progress, QA Check, Completed)
- Title field: `edscha_name` (Order Code)
- Subtitle field: `edscha_model` (Car Model)
- Value field: `edscha_quantity` (Quantity)

---

## 🐛 Troubleshooting

### Issue: Import fails with "SecLib::CheckPrivilege failed" or "prvCreateEntity" error
**Error Message Example:**
```
Solution "KanBan Board" failed to import: SecLib::CheckPrivilege failed. 
User: [user-id], PrivilegeName: prvCreateEntity, PrivilegeId: [privilege-id], 
Required Depth: Basic, BusinessUnitId: [bu-id]
```

**Cause:** Your user account does not have permission to create new Dataverse tables.

**Solution:**
1. Go to [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/)
2. Select your environment → **Settings** → **Users + permissions** → **Users**
3. Find your user account
4. Click **Manage security roles**
5. Add **System Administrator** or **System Customizer** role
6. Click **Save**
7. **Wait 5-10 minutes** for permissions to propagate
8. **Sign out** and **sign back in** to Power Apps
9. Try the import again

**Alternative:** Ask your Power Platform administrator to:
- Grant you the required security role, OR
- Import the solution on your behalf

### Issue: Cards show "No Title"
**Solution:** Use the **Manual Override** properties:
- Set `titleFieldNameOverride` to the schema name (e.g., `lto_taskname`)
- Set `statusFieldNameOverride` to the schema name (e.g., `lto_status`)

### Issue: Type field not saving correctly
**Solution:** Ensure you're using the `OnChange` formula provided above. The formula includes:
- `Trim()` to remove whitespace
- Numeric ID mapping for all type values
- Fallback to `Value(CID)` for direct numeric IDs

### Issue: Assigned To field resets to blank
**Solution:** The v16.7.0 includes a fallback mechanism using `varK_CurrentTask`. Ensure the `EDIT_OPEN` event handler is in your `OnChange` formula.

### Issue: Colors not applying from JSON
**Solution:**
- Verify JSON syntax (use a JSON validator)
- Ensure property names match exactly: `statusChoicesJSON` and `typeChoicesJSON`
- Check that `value` fields match your Dataverse choice values

### Issue: Component not visible in "Get more components"
**Solution:**
- Verify PCF is enabled for Canvas Apps in your environment
- Ensure the solution was published after import
- Refresh your browser and try again

---

## 📞 Support & Contact

**Publisher:** Lukas Toman  
**Email:** toman_lukas@icloud.com  
**Website:** https://lukastoman.figma.site/  
**Phone:** +420 724 162 880  
**Location:** Prague, Czech Republic

For technical support, feature requests, or bug reports, please contact via email.

---

## 📄 License & Usage

This is an **Unmanaged Solution**, which means:
- ✅ You can modify the table structure
- ✅ You can customize the Canvas App
- ✅ You can add new fields to the Developer Tasks table
- ✅ You can use the PCF component in multiple apps
- ⚠️ Updates require manual re-import and may overwrite customizations

**Recommended:** Export your customizations before updating to a new version.

---

## 🆕 Version History

### v16.7.0 (February 8, 2026)
- ✅ Strict numeric ID validation for choice fields
- ✅ Enhanced multiselect type handling
- ✅ Improved delete modal styling
- ✅ Optimized delete flow (modals close before blur)
- ✅ Added JSON configuration for custom colors
- ✅ Full support for reusability in other apps

### v16.6.0
- ✅ Optimized delete flow
- ✅ Styled confirmation buttons

### v16.5.0
- ✅ Multi-select ID lock
- ✅ Enhanced type field handling

### v16.4.0
- ✅ Edit context lock
- ✅ Improved data preservation

---

**Thank you for using KanBan Board v16.7.0!** 🚀
