# Human Analyst vs. AI Analyst

An honest, hands-on comparison of Tableau Public, Gemini + Colab, Julius AI, and Cursor for a real-world data analysis task.

### **The Hot Question: In analytics, is AI coming for my entire job, or just my task list?**

As the founder of the dataGOATs community, it’s something that comes up a lot during our discussions: What are analytics roles going to look like as AI continues to get better and better? Will it replace me, or will it just evolve?

I wanted to demonstrate what an evolution could look like for analysts and then try to answer the “will it replace me?” question. In order to do that, I took a dataset about AI applicability across various jobs (yes, I know, it’s very meta), one human analyst (me), and three different AI tools to give an honest comparison to what gives the best analysis, and in what ways. 

### **Project Documentation & Files**

I utilized a Github Repository to store the files and documentation, you can access that [here](https://github.com/zackm-solid/Human-vs-AI-Analyst) if you’d like to try any of this for yourself or see my process.

I generated a basic process markdown file for each part of the project so you can see the steps I took to get to the insights I ultimately uncovered.  Just go into the respective directories for each analysis workflow, or as I call them here, “The Contenders”.

### **The Dataset**

I combined data from the Microsoft “AI Applicability” [study](https://github.com/microsoft/working-with-ai) with [BOLS data](https://data.bls.gov/projections/occupationProj) because I went through several datasets on Kaggle in preparation for this process, and couldn’t find a data source on “AI and job impact” that didn’t have really weird miscategorizations and assumptions (e.g. dentist is classified as an “entertainment” industry job).

While I had my own “hot take” on the Microsoft “AI Applicability” Study ([see that post here](https://www.linkedin.com/posts/zwmartin_ai-dataanalytics-datascience-activity-7366911201739464705-d7HT?utm_source=share&utm_medium=member_desktop&rcm=ACoAAAxNibABVOMPtxVPc81Yp9lP-GsNAXLCKts)), I recognize that my own take on it may have been a little flawed as I read through their documentation further. The Microsoft Study wasn’t suggesting that you could use their data alone to determine if AI is going to replace the job. I think many of us took it a little too seriously. It’s really just how much you could use AI in the role for various tasks.

BOLS tends to have reliable and relatively clean data, and they use SOC Codes in the Microsoft data, so it allows me to augment the basic takeaways from the Microsoft study with standard occupational data from BOLS.  An easy “left” join on the SOC Codes from the MS Data to combine the tables.

Funny note, the first column (SOC Code) in the Microsoft dataset had the classic “Excel perceives this as a date”, so I had to correct that before doing all my VLOOKUPs in GSheets.

![Image of excel dates formatted incorrectly](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/images/Annoying%20Date%20Format.png)

The Microsoft Data ‘soc\_ai\_applicability\_scores.csv’ has 3 key columns - SOC Code, Job Title and an AI Applicability Score. The BOLS dataset has 14 columns, 12 to the left of the SOC Code that I actually cared about, so it was simple to drag those headers over, create some VLOOKUPS under those headers, validate it transferred the data that I wanted, then copy/paste as values over my VLOOKUPS to preserve true values transferred from the other data.

**This will be my final dataset that we’ll perform our analysis off of - with the goal of answering the following questions:**

1.  Is my job "safe"?
    
2.  How are analytics roles affected? What roles aren’t affected much at all?
    
3.  Which jobs will evolve with AI, grow, and command high salaries?
    

### **The Contenders**

*   **Contender 1: The Human (Me + Tableau):** The traditional "old school" approach. I’ll be loading the dataset into Tableau Public (free) and surfacing answers to the questions.
    
*   **Contender 2: The Co-pilot (Gemini + Colab):** Using Gemini to write code for me directly in Colab. I know Python pretty well, but for this exercise, I’m not touching a single line of code. Gemini in Colab will create all of it, and the process for visualizing it. I will just provide the prompting and questions I’m looking to answer.
    
*   **Contender 3: The “Full Stack” AI Analyst (Julius AI):** An AI tool designed to _be_ the analyst.  I’ve interacted a little with Julius (and they sponsored the dataGOATs analytics meme contest!), but I’m by no means a power user of their tools.  I’m excited to give it a shot for this.
    
*   **Contender 4: The AI-Native IDE (Cursor):** A tool designed to _build_ with AI.  I’ve seen use cases where you can connect it with Snowflake (thank you [Eden Litvin](https://www.linkedin.com/in/eden-litvin/) for showing me that) and run SQL queries, etc. but we’ll just focus on what sort of interactive dashboards and insights we can surface using this dataset for this exercise.
    

### **The Human Baseline (Tableau)**

First, I had to set a baseline.  To be fair, I’m not a Tableau **expert**, but I’m decent with it and have used other BI tools quite extensively.  I wanted this to be a comparison of mostly free, accessible tools and [Tableau Public](https://public.tableau.com/app/discover) is just that - free.

So, I fired up Tableau, imported my CSV as the data source and got to visualizing.

If you want all of the nitty-gritty details on how I put this together and the final dashboard, go see the Github [documentation](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/tableau/tableau.md).

**Results:** 

![Final Tableau Dashboard](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/images/Tableau%20Final.png))

**My Takeaway:** It was manual. What you would expect. Every single insight was one I had to dig for myself, but hey… it seriously wasn’t bad, it’s the norm.  Not my prettiest dashboard ever, but it is useful and got to my key insights.

**Time to Insight:** Approximately 1 hour creating documentation, the dashboard itself and publishing to Tableau Public.

### **The Co-pilot (Gemini + Colab)**

Next, I opened a Google Colab notebook and started a chat with Gemini. I broke the process down into a series of 7 [prompts](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/gemini/gemini.md), with one final prompt to create an interactive dashboard with the visuals in _streamlit_.

**Results:**

This was a night-and-day difference, but not necessarily 100% for the better.  It was MUCH faster but not as clean.

![Final Colab Dashboard](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/images/Gemini.png))

**My Takeaway:** This is awesome when you need to create a few visuals quickly, but not as worried about “polish” like with the classic Tableau option.  Quick, and dirty.  As soon as I started prompting Gemini, it wrote code that I could execute in the notebook.

**Time to Insight:** 15 Minutes

### **The “Full-Stack” AI Analyst (Julius AI)**

This tool claims to do the _entire_ job. No code, just prompts. I uploaded the CSV and asked it my questions (full prompts in [Github](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/julius/julius.md)).

**Results:**

![Final Julius Dashboard](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/images/Julius.png)

**My Takeaway:** For pure, rapid-fire exploratory data analysis, this is pretty great. It's like having an incredibly fast, slightly junior analyst at your fingertips.

Keep in mind, this is a relatively clean and straightforward dataset.  I’m not sure how it performs on messier data, or poorly documented schemas when you’re connecting to a live database.

I do have a piece of feedback for Julius - the color scale ended up reversing in the chart above.  Not critical, and not something that couldn’t be fixed easily, but I wanted to give an honest take of the tool and potential things you’ll need to look out for & adjust yourself, just as if you were working with a junior analyst to create an analysis.

Not perfect, but pretty damn good for the effort and time required.

**Time to Insight:** 10 Minutes

### **The AI-Native IDE (Cursor)**

Cursor is more of a developer's tool. I wanted to know if it was "too much" for daily analysis, or if it could be useful for building out interactive dashboards. I’ve recently learned it could connect to Snowflake and write SQL queries, for instance.

**Results:**

Pretty incredible stuff.  I literally just pulled down the Github repo I hosted this project in, told it to look at the Cursor directory and [markdown reference file](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/cursor/cursor.md), then start building.

![Final Cursor Dashboard](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/images/Cursor.png)

**My Takeaway:** Similar results in quality to the Colab-generated or Julius visuals, since it’s all generated with common Python libraries and then served up like Colab using Streamlit, but it did make everything a little more visually appealing (even if it probably needed some tweaking at the end too).

Having it create everything that quickly and present it in Streamlit is really impressive, considering it’s doing a lot of work on the backend to make all this happen, this quickly.

**Time to Insight:** 5 Minutes

### **The Final Showdown: Man vs. Machines**

![Final Table Comparison with Rankings by Category](https://github.com/zackm-solid/Human-vs-AI-Analyst/blob/main/images/Table.png)

### **The Final Insights**

If you’re curious about what I actually found in the data?  Well, you’re welcome to dig into my [Tableau Public](https://public.tableau.com/views/AIJobImpact_17632417332070/AnalyticsDashboard?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link) dashboard or any of the other stuff I included in the Github [repo](https://github.com/zackm-solid/Human-vs-AI-Analyst/tree/main).

**Here’s a few Highlights:** 

*   Data Scientist roles are projected to have a high impact from AI (high applicability score at 0.36) but are still expected to have major growth (33.5%).
    
    *   Data Scientist stood out among non-analytics roles as well.
        
*   Other analyst roles still show positive growth (average of 6-8%) but not growing at the rate of Data Science and have a high AI Applicability score, which could signal slower growth if more tasks could be automated.
    
*   _This data shouldn’t be treated as conclusive_ because as Microsoft highlights, AI Applicability does not equal AI Automation, and we’re not sure with advancements in AI over the next 10 years how roles may further change.
    
*   The quadrant chart is the most useful; with the top-right being roles that are high AI applicability and still high growth and top-left being roles with high growth and low AI applicability.
    

### **Conclusion: My Job Isn't Gone, It's Just Evolving.**

So, is my job gone? Absolutely not.  I think I proved effectively that I can do a higher quantity of analyses using these tools, and my job as a good analyst is still to ask the right questions, document my plan to conduct the analysis, then go after it.

I’m still doing that with the AI tools, it’s just doing a lot of the coding & building for me.  I’m still directing.  It’s more like I’m an analytics lead in this case, directing a junior.

**Here’s how I would utilize each of the tools:**

*   **Julius** was the fastest for _answers_ immediately and additional insights outside visuals.
    
*   **Gemini + Colab** was the best for _workflow_ and customization since it’s easy to manipulate the code directly in the notebook and iterate through different results.
    
*   **Cursor** was the best for _building_ an interactive dashboard VERY quickly.
    
*   **Tableau** still has the best polished, interactive dashboards.  If you’re planning on entering a visualization contest, or presenting to non-technical stakeholders, this to me is still the winner.
    

I have to admit, I still really enjoyed building the Tableau dashboard.  It certainly wasn’t the fastest, but it looked the best to me in the end.  Maybe that’s just my very human, emotional, nostalgic side.  Maybe it’s my bias towards human creativity.

Though, the elephant in the room is… if I spent 3x more time dialing in Julius, Cursor or Colab, it likely would look better than my Tableau dashboard.

Perhaps that will be a future write-up.

### **What Do You Think?**

What tools are you using? What did I miss?

Come join the conversation and share your own AI workflows in the [GOATs Community](https://community.datagoats.org/) (dataGOATs.org).
