# Manufacturing Operations ERP/BOM Analytics

## 1. Overview
This project analyzes engineering and manufacturing BOM errors, revision activity, rework cost, and error resolution time using a realistic operations dataset modeled in Excel.

---

## 2. How to Use the Dashboard

1. Open **Engineering_Analytics_Dashboard.xlsx**
2. Go to the **Dashboard** tab
3. Use slicers to filter by:
   - Error Type
   - Department
   - Month
4. Review primary KPIs:
   - Total Errors
   - Rework Cost
   - Avg Time to Resolve
   - Revision Count
5. Explore trend charts for deeper operational insights

---

## 3. Dataset Schema

### BOM_Error_Data
| Column | Description |
|--------|-------------|
| error_id | Unique error record |
| unit_id | Affected transformer/unit |
| error_type | Wrong part, wrong rev, routing issue, etc. |
| department | Eng, Mfg, Quality |
| date_logged | Date issue discovered |
| time_to_resolve_days | Days required to fix |
| cost_impact | Estimated rework cost |

### Revision_Change_Log
| Column | Description |
|--------|-------------|
| change_id | Revision event ID |
| part_number | Affected part |
| old_rev | Previous revision |
| new_rev | Updated revision |
| change_reason | ECO reason code |
| date_changed | Date of change |

---

## 4. Tools Used
- Excel  
- Power Query  
- PivotTables  
- KPI dashboards  
- Mock operational datasets  


