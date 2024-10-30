java c
Econ 145 - Fall 2024 
Homework 9: Long: UN Data 2 
Overview 
The goal of this assignment is to practice plotting and to make intuitive conclusions from the data. You will again be working with the same UN Fertility Rate Data you used in Assignment 8. However, I have also included some additional columns downloaded from other UN Datasets that are often cited as impacting birth rates. The new columns include:
• infantMortality: The infant mortality rate per 1000 births.
• gdp: The Gross Domestic Product (GDP) in 2015 US dollars.
• hdi: The Human Development Index (HDI) score, out of 100.
• hdiscore: The HDI category code (Low, Medium, High, Very High).
• urbanization: The percentage of the population living in urban areas.
• contraPerc: The percentage of married women who have access to any method of contraception.
You will use the graphs you created in Assignment 8 and graphs you will create in this assignment to analyze birth rates and commonly cited indicators that impact birth rates. In this assingment’s write-up, you will write a one-page newspaper article discussing the trends in birth rates over time across the world in the past several decades.
To Receive Credit 
• Save the scripting file (i.e. your R program file) as assignment_9.R. Make sure your capitalization is correct as the autograder is case-sensitive.
• Save your PERMID at the top of the Rscripts (i.e. PERMID ← xxxx)
• Be sure to include your first name, last name, and perm number on your one page write-up.
• Make sure all changes to the original dataset are done within the R script.
• Your one page write-up must be submitted in a .pdf to receive credit.
Grading on Coding Questions 
Grading on the coding portion of the homework will come in two types of questions: Public Questions and Private Questions. Public Questions can be submitted as many times as you like to the autograder, and the autograder will give detailed feedback. Additionally, the TAs will help you on Nectir and in office hours on the Public Questions. On the other hand, Private Questions can be thought of as a mini quiz within the homework. While you still have as many times to upload your answer as you want, the autograder will not provide any feedback, and the TAs and Professor Startz will not provide any guidance or assistance (but getting advice from classmates on Nectir or elsewhere is completely okay). Private Questions will be marked on the homework assignment.
Things that can break the autograder: 
• Please read the autograder_instructions.pdf file on CANVAS.
For each homework assignment, words colored in magnenta indicate a variable/vector/tibble that will be graded by the autograder. Pay close attention to these colored texts and be sure not to miss any. You always always always need to include PERMID ← xxx to receive credit. (Use your real permid, not “xxx”–but you knew that.) The beginning of your code should look like the code below for all future assignments. (Refer to the autograder_instructions.pdf file for more details).
rm(list=ls()) # clear the environment
#-------Import necessary packages here-------------------#
# Load necessary packages here
#------ Uploading PERMID --------------------------------#
PERMID <- "ABC1234" #Type your PERMID with the quotation marks
PERMID <- as.numeric(gsub("\\D", "", PERMID)) #Don't touch
set.seed(PERMID) #Don't touch
#------- Answers ----------------------------------------#
Part 1: Coding assignment 
Go to the data website for the class and download the file un_data2.csv data for homework 9.
1. (Public Question) Import the data from the un_data2.csv file into R. Then, mutate the infantMortality column such that it records the infant mortality rate per 100 births, instead of per 1000 births. Then, using the gdp and population columns, create a new column called gdp_per_capita. Hint: Recall that population is represented in terms of 1000s of people. Finally, filter to only keep data between the years 1970 to 2015. Save your tibble as un_data.
2. (Public Question) Before you begin your analysis, create two new tibbles: un_data_tfr and un_data_mac. To create un_data_tfr, filter un_data to keep only the rows that measure the Total Fertility Rate (TFR). Next, to create un_data_mac filter un_data to keep only the rows that measure the Mean Age at Childbearing (MAC).
3. (Public Question) Using un_data_tfr, create a tibble called un_data_tfr_2010 that only contains rows for the year 2010. Then, using un_data_tfr_2010, you will recreate Figure 1. Figure 1 presents four scatter plots comparing gdp_per_capita to hdi, infantMortality, contraPerc, and urbanization, respectively. Hint: To create a single figure containing multiple plots you can use the command par(mfrow= c(2,2)).
4. (Private Question) After plotting the scatter plots in Figure 1, you will notice that the relationship between GDP per capita and the other four indicators is very non-linear and that there are many countries with low GDP per capita values and few countries with high GDP per capita values. Therefore, you will recreate the plot, now with a log transformation of GDP per capita (using a base 10 log transformation). Your new figure should look like Figure 2. Note: This plot will be graded with your write-up and will not be graded by the autograder.
5. (Public Question) Next, using un_data_tfr create a new 代 写Econ 145 Homework 9: Long: UN Data 2 Fall 2024R
代做程序编程语言tibble called un_data_tfr_gdp that contains a column for the year, a column for the region, and a column for the average GDP per capita in each region for each year. The new column should be called gdp_per_capita, and should be created by dividing the sum of GDP by the sum of population for each region and year. Then, using un_data_tfr_gdp and ggplot, you will recreate Figure 3. Figure 3 plots the log base 10 transformation of the average GDP per capita in each region across time. Save your plot as gdp_per_capita_region_plot. Note: You should not implement the log transformation of gdp_per_capita in your tibble, un_data_tfr_gdp. You should instead only implement the log transformation when creating your plot. Hint: You should first filter out all rows that have a missing gdp or population value so that the sum of gdp and population are over the same rows.
6. (Public Question) Using un_data_mac, you will create a new tibble called un_data_mac_summary that contains the mean weighted value of the Infant Mortality Rate, Urbanization Rate, Contraceptive Access Rate, and Mean Age at Childbearing indicators for each region in each year between 1970 and 2015. The columns of un_data_mac_summary should be called year, infantMortality, urbanization, contraPerc, and MAC.
7. (Private Question) Using un_data_mac_summary, you will recreate Figure 4, which contains 4 line graphs. Each line graph plots the Infant Mortality Rate, Urbanization Rate, Contraceptive Access Rate, or Mean Age at Childbearing for each region over time. Each line graph should have time on the x-axis and the indicator on the y-axis. Hint: This can be done with base R (using par(mfrow= c(2,2))) or with ggplot (using facet_wrap) to create multiple line graphs in a single figure. Note: This plot will be graded with your write-up and will not be graded by the autograder.
8. (Public Question) Using un_data_tfr_2010, you will create a new tibble called un_data_hdi_category which counts the number of countries in each region that have each HDI category code (Low, Medium, High, or Very High), in 2010, as well as the percentage of countries in each region with each code. Your tibble should have the column names hdicode, region, hdiNum, and hdiPerc. Make sure to remove any rows without an HDI category, round your percentages to 3 decimal places, and arrange the rows by the HDI category code (from Low to Very High).
9. (Private Question) Using un_data_hdi_category, you will recreate a figure that looks like Figure 5 or 6. Figure 5 and 6 contain 5 pie charts, one for each region, that show the percentage of countries in each HDI category in 2010. Each pie chart should have a different color for each HDI category. Hint: This can be done with either base R graphing or with ggplot graphing. With base R you can use the pie function and par(mfrow=c(2,3)) to create a figure that looks like Figure 5. With ggplot, you can use the geom_bar function along with the function coord_polar("y", start=0) to create pie charts and facet_wrap to create a figure that looks like Figure 6. You do not need to create both Figure 5 and 6, just choose one method to create the figure. Note: This plot will be graded with your write-up and will not be graded by the autograder.
Part 2: Write-up 
You are working as a reporter and column writer at a newspaper and have been assigned to work on a piece discussing the change in birth rates over time across the world in the past several decades. Your Editor in Chief would like you to discuss some of the indicators often mentioned as impacting birth rates including infant mortality, urbanization, GDP per capita, human development, contraception, and maternal age at childbearing. Using 3-4 figures from homework assignments 8 and 9, you will write a one-page newspaper article discussing the trends in birth rates over time. What can you conclude about birth rates across the world and in different regions? What factors seem to be associated with birth rates? What are some of the implications of these trends?
Remember, your write-up must be written as a narrative and should be a page long, or less - not including graphs and tables. Your write-up should not be any longer than it needs to be to explain what you want to discuss. You will need to title your write-up as you would in a professional setting, with titles such as “Homework 9 Write-up” not being accepted. Attach any figures at the end of your write-up. The grade on the write-up will depend on how clear and concise the answer is, the quality of your writing, and how well labelled your tables/graphs are. Attach graphs and tables at the end of your write-up. Your graphs should be clearly labeled (Eg: Use GDP per capita as a label instead of gdp_per_capita). Note that getting a full grade on the graphs from the autograder does not guarantee that your graphs are clearly labeled because the autograder can only check if your graph is correct. Include all figures from this assignment, although you will only be referencing 3-4 figures in the text of your write-up. Make sure when you reference a figure in your writing that it is clear which figure you are referencing.

Figure 1: Example of Figure 1

Figure 2: Example of Figure 2

Figure 3: Example of Figure 3

Figure 4: Example of Figure 4

Figure 5: Example of Figure 5

Figure 6: Example of Figure 6



         
加QQ：99515681  WX：codinghelp  Email: 99515681@qq.com
