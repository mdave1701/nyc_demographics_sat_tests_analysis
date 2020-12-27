# SAT Test Analysis for NYC Schools

## Description
Have you ever wondered what affects standardized test scores like the Scholastic Assessment Test (SAT)?

Look no further! In this project, I analyze data from 6 different datasets about factors that affect SAT scores of students in New York City.

## Description of Data
All the datasets are from https://opendata.cityofnewyork.us/.

The data files are contained within the _data_ folder in this reporsitory.

1. **ap_2010.csv**: This file contains information on the number of Advanced Placement (AP) test takers per school in the NYC area, total number of exams admisinitered, and number of students who passed these exams. 
2. **class_size.csv**: As the name suggests, this file contains information on different aspects of a class, such as the class size, teacher-student ratio, grade, core subjects, etc. for all schools in the NYC area.
3. **demographics.csv**: This file contains information about the race/ethnicity of students, their gender, and English Language Learner (ELL) status, sometimes also called English as Second Language (ESL) status.
4. **graduation.csv**: This file includes information about the size of the student cohort, percent of students that graduated, percent of students that dropped out, and the percent of students still enrolled.
5. **hs_directory.csv**: This file contains geographical information about the schools such as, borough, district, address, metropolitan area, etc.
6. **sat_results.csv**: This file contains the average SAT test scores per school. The overall SAT score, along with the critical reading, math, and writing average scores are also listed.
7. **survey.txt and survey_d75.txt**: These two files contain a plethora of information that comes from a survey that NYC conducts for their schools. Parents, teachers, and students participate in this survey where they answer questions about their opinion on academic expectation, engagement, and safety and respect. The fields extracted from this file (for tha analysis) were concerned with communication, engagement, academics, and safety. 
8. **survey_data_dictionary.xls**: The data dictionary of the two survey files.

**combined.csv** is the cleaned up, merged file that combines all the other datasets in a useful manner. If someone wants to take this analysis further, this file can save you a lot of time since all of the columns that I used in my analysis are in here, joined on the DBN column (which is used as a primary key for all the data files).

## Analysis Steps
### Data Preprocessing
All the data files listed above were read into dataframes and merged on the DBN column. There was some data cleaning done prior to the merging, such as adding an _Overall SAT Score_ column and adding latitude and longitude columns for each school.

The dataset was then condensed by making sure it only contained data from high schools only, along with some other filters dealing with Cohort, School Year, and Program Type.

### Correlation Analysis
The main tool through which important factors were selected was through correlation analysis. Correlations coefficients of SAT results to all the other columns in the dataset were calculated. Based on the correlation coefficents, two main types of features were selected for further analysis, namely, survey ratings and race.

## Results
The correlation analysis of the surveys with SAT scores revealed that overall safety ratings from teachers and students had medium positive correlation (0.3 - 0.4) with SAT scores. Academic engagement was also found to be relatively strongly correlated with SAT scores, although this is a bit obvious.

It was found that as safety ratings increased, SAT scores also increased, however there were a few anomalies. There were some schools that had a high safety rating, but lower SAT scores than some of the less safe schools. It was found that Queens and Bronx generally had lower safety ratings, whereas Brooklyn had some of the highest safety ratings for schools.

The correlation analysis also revealed that race had a significant impact on SAT scores. The schools that had high percentages of whites and asians generally had high SAT scores, whereas schools with high percentages of blacks and hispanics had lower SAT scores. It is worth looking into the economic conditions of the neighborhoods/schools where such disparaties exist.

One possible data-driven explanation of this disparaity for hispanics was explored. It was found that the schools with high percentages of hispanics were usually international schools, which had high percentages of ELL (or ESL -- English as Second Language) students. Naturally, it could be said that if the students are not proficeint in English, then their SAT scores will suffer dramatically.

Lastly, it was also found that schools that had 25-60% of their students take AP exams had SAT scores of 1700 or higher. This also seems to make sense: the more academically advanced students are, the better they perform on the SAT.