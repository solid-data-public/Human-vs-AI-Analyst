Process Documentation: Tableau Public
=====================================

**Dataset Fields Used:**

*   `Title (Dimension)`
    
*   `AI Applicability Score (Measure)`
    
*   `Employment Percent Change (Measure)`
    
*   `Median Annual Wage (Measure)`
    
*   `SOC Code (Dimension)`
    

### **Step 1: Load the Data**

1.  Open Tableau Public.
    
2.  Connect to your data source (the `employment_data_final.csv` in this case).
    
3.  Go to Sheet 1.
    
4.  Ensure your measures (`AI Applicability Score`, `Employment Percent Change`, `Median Annual Wage`) are recognized as numbers and `Title` / `SOC Code` are dimensions.
    

### **Step 2: Answer Question 1: "Is my job 'safe'?" (The AI vs. Growth Map)**

This worksheet will be a scatter plot that maps all jobs.

1.  **Name Worksheet:** Rename Sheet 1 to 'AI vs. Growth Map'.
    
2.  **Create Scatter Plot:**
    
    *   Drag `AI Applicability Score` to the **Columns** shelf.
        
    *   Drag `Employment Percent Change` to the **Rows** shelf.
        
    *   Drag `Title` to the **Detail** shelf on the Marks card.
        
    *   Drag `Median Annual Wage` to the **Tooltip** and **Color** under Marks.
  
    *   Click **Color** and then 'Edit Colors' and select 'Orange-Blue Diverging' with Orange being the high end of the scale.  This helps visualize higher salaries.
        
    *   Drag `Employment Change` to **Size** under Marks.
        
3.  **Add Quadrants (Reference Lines):**
    
    *   Right-click the AI Applicability Score axis and select Add Reference Line.
        
    *   In the dialog:
        
        *   **Line:** Choose Entire Table.
            
        *   **Value:** Select Average (or Median, if you prefer).
            
        *   **Label:** Set to Average.
            
        *   **Formatting:** Choose a thin, dashed line.
            
    *   Repeat this process for the Employment Percent Change axis.
        
4.  **Initial Insight:** You now have four quadrants:
    
    *   **Top-Right:** High AI Score, High Growth (Jobs evolving with AI)
        
    *   **Bottom-Right:** High AI Score, Low Growth (Jobs at potential risk)
        
    *   **Top-Left:** Low AI Score, High Growth (Traditional "safe" growth jobs)
        
    *   **Bottom-Left:** Low AI Score, Low Growth (Stagnant jobs)
        

### **Step 3: Answer Question 2: "How are analytics roles affected?"**

This worksheet will be a set of bar charts filtering for specific roles.

1.  **Name Worksheet:** Create a new worksheet named Analytics Role Deep-Dive.
    
2.  **Create the Filter:**
    
    *   Drag Job Title to the **Filters** card.
  
    *   Under 'Select from List' I chose analy roles with "Analyst", "Data" and several "Specialist" and "Operations" roles that are linked to analytics.
        
    *   Click OK. This will filter your sheet to only analytics roles.
        
3.  **Create Bar Chart (AI Score):**
    
    *   Drag AI Applicability Score to the **Columns** shelf.
        
    *   Drag Job Title to the **Rows** shelf.
        
    *   Click the Sort Descending icon in the toolbar to see which analyst roles have the highest AI score.
        
4.  **Create Bar Chart (Growth):**
    
    *   Duplicate the sheet (right-click the tab > Duplicate).
        
    *   Name the new sheet Analytics Role Growth.
        
    *   In the new sheet, remove AI Applicability Score from Columns and replace it with Employment Percent Change.
        
    *   Sort descending to see the fastest-growing analyst roles.
        
5.  **Create "Not Affected" Chart:**
    
    *   Duplicate your first sheet (Analytics Role Deep-Dive).
        
    *   Name it Least AI-Affected Jobs.
        
    *   Remove the `Title` filter.
        
    *   Drag AI Applicability Score to the **Filters** card. Select All values.
        
    *   Click the Sort Ascending icon in the toolbar.
        
    *   Right-click `Title` on the Rows shelf and select Filter....
        
    *   Go to the Top tab. Select By field, 'Top 20', by `Employment Percent Change`.  This will show jobs that are going to continue to grow, and their respective AI impacts.
        

### **Step 4: Answer Question 3: "Jobs that evolve, grow, and pay well?"**

This can actually be answered by utilizing the Scatter Plot from Step 2.

1.  **Go to Worksheet:** AI vs Growth Map
        
2.  **Initial Insight:**
    
    *   The jobs in the **top-right quadrant** (High AI, High Growth) that are also the **largest circle** (employment growth in thousands) and **darkest orange in color** (highest salaries) are likely going to be the ones to go after, if they interest you.
    *   It's worth noting that jobs that may not be affected as much by AI are in the **top-left quadrant** (Low AI, High Growth) are also the great, old reliable, high growth jobs that are anticipated to be needed regardless of AI's involvement in society.

3. For the purpose of creating a non-analytics role view as well, I duplicated the `Analytics Role Growth` worksheet and cleared the "Title" filter so it worked for all roles.

### **Step 5: Build The Final Dashboard**

1.  Click the New Dashboard icon (the square with a +).
    
2.  **Add Sheets:** Drag your worksheets onto the dashboard canvas. A good layout would be:
    
    *   AI vs. Growth Map (main, large view - taking up left side of dashboard)
        
    *   Analytics Role Deep-Dive (top right)
  
    *   Analytics Role Growth (bottom right)
        
3.  **Add Interactivity:**
    
    *   Add a Job Title filter. Click on one of your sheets (like AI vs. Growth Map) in the dashboard, click the small dropdown arrow, and select Filters > Title.
        
    *   This will add the filter you created in Step 3.
        
    *   Click the filter's dropdown arrow, select Customize, and check Show "All" Value and Show Search Box (or Wildcard Match).
        
4.  **You're Done:** Now you have a dashboard where you can see the overall map, and you (or a user) can type in any job title (like "Analyst" or "Dentist" or "Manager") to see exactly where it falls on the map.

5.  **Bonus:** If you want to add a non-analytics roles version of this dashboard, just duplicate it, and change out the Analytics Role Deep-Dive for the Least AI-Affected Jobs worksheet, and the Analytics Role Growth worksheet for the Non-Analytics Role Top Growth worksheet I recommended in Step 4.
