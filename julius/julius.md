Julius AI Process: Replicating the Tableau Dashboard
====================================================

This guide outlines the conversational process to replicate your final Tableau dashboard using Julius AI. The prompts are designed to match your specific chart logic.

### **Step 1: Setup and Load Data**

1.  Drag and drop your employment\_data\_final.csv file into the Julius chat box.
    
2.  **First Prompt:** "Hi Julius. Please load this file and show me a summary. I need to see all the column names, their data types, and any missing values. I'm especially interested in Title, AI Applicability Score, Employment Percent Change, Median Annual Wage, and Employment Change."
    

### **Step 2: Q1 & Q3: The "AI vs. Growth Map" (Bubble Chart)**

This chart answers _Question 1 ("Is my job safe?")_ and _Question 3 ("Jobs that evolve, grow, and pay well?")_.

1.  **Prompt:** "Please create a single bubble chart that shows me the relationship between AI, job growth, and salary. This chart needs to show four things at once:"
    
    *   AI Applicability Score on the x-axis
        
    *   Employment Percent Change on the y-axis
        
    *   The _size_ of the bubble should be based on Employment Change (the absolute number)
        
    *   The _color_ of the bubble should be based on Median Annual Wage
        
2.  **Refinement Prompt 1 (Color):** "This is perfect. Can you change the color scale to an 'Orange-Blue Diverging' one, where orange means a higher salary?"
    
3.  **Refinement Prompt 2 (Quadrants):** "Now, please add dashed reference lines for the average AI Applicability Score and average Employment Percent Change to divide the chart into four quadrants."
    
4.  **Insight Prompt (Q3):** "Based on this chart, which jobs are in the top-right quadrant (high AI score and high growth) and also have high salaries? Show me a list."
    

### **Step 3: Q2 (Part 1): "How are analytics roles affected?"**

This replicates your two specific bar charts for analytics roles.

1.  **Filter Creation Prompt:** "I want to look at analytics roles. Can you find all the job Titles that include the words 'Analyst', 'Data', 'Specialist', or 'Operations'? Show me the list of titles you find."
    
2.  **Verification Step:** (You review the list. If it's good, you proceed. If it's bad, you tell Julius "remove 'Operations Manager'" etc.)
    
3.  **Chart 1 Prompt (Deep-Dive):** "Okay, using that list of analytics jobs, please make a horizontal bar chart showing their AI Applicability Score. Sort it from highest to lowest score."
    
4.  **Chart 2 Prompt (Growth):** "Great. Now make another horizontal bar chart for those _same jobs_, but this time show their Employment Percent Change. Sort it from highest to lowest growth."
    

### **Step 4: Q2 (Part 2): "What roles aren't affected much at all?"**

This replicates your Least AI-Affected Jobs logic.

1.  **Prompt:** "I need to find jobs that are 'safe' from AI but still growing. Can you show me a list of the top 20 jobs that meet two conditions:
    
    1.  Their AI Applicability Score is _below_ the average.
        
    2.  They have the highest Employment Percent Change (out of that below-average group)."
