---
title: "Case Study 2"
author: "Jason Lin, Manisha Pednekar, Jason Lingle"
date: "April 16, 2018"
output:       
      html_document:
        keep_md: TRUE
---

#Preliminary Look over of the variables based on column percentages                   


```r
setwd("C:/Users/sams/Desktop/SMU/January 2018/Doing Data Science/CaseStudy2")
casestudy <- read.csv("CaseStudy2data_2.csv",header = TRUE)
library(tigerstats)
```

```
## Warning: package 'tigerstats' was built under R version 3.4.4
```

```
## Loading required package: abd
```

```
## Warning: package 'abd' was built under R version 3.4.4
```

```
## Loading required package: nlme
```

```
## Loading required package: lattice
```

```
## Loading required package: grid
```

```
## Loading required package: mosaic
```

```
## Warning: package 'mosaic' was built under R version 3.4.4
```

```
## Loading required package: dplyr
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following object is masked from 'package:nlme':
## 
##     collapse
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```
## Loading required package: ggformula
```

```
## Warning: package 'ggformula' was built under R version 3.4.4
```

```
## Loading required package: ggplot2
```

```
## 
## New to ggformula?  Try the tutorials: 
## 	learnr::run_tutorial("introduction", package = "ggformula")
## 	learnr::run_tutorial("refining", package = "ggformula")
```

```
## Loading required package: mosaicData
```

```
## Warning: package 'mosaicData' was built under R version 3.4.4
```

```
## Loading required package: Matrix
```

```
## 
## The 'mosaic' package masks several functions from core packages in order to add 
## additional features.  The original behavior of these functions should not be affected by this.
## 
## Note: If you use the Matrix package, be sure to load it BEFORE loading mosaic.
```

```
## 
## Attaching package: 'mosaic'
```

```
## The following object is masked from 'package:Matrix':
## 
##     mean
```

```
## The following objects are masked from 'package:dplyr':
## 
##     count, do, tally
```

```
## The following objects are masked from 'package:stats':
## 
##     binom.test, cor, cor.test, cov, fivenum, IQR, median,
##     prop.test, quantile, sd, t.test, var
```

```
## The following objects are masked from 'package:base':
## 
##     max, mean, min, prod, range, sample, sum
```

```
## Welcome to tigerstats!
## To learn more about this package, consult its website:
## 	http://homerhanumat.github.io/tigerstats
```

```r
boxplot(Age~Attrition,casestudy,main="Age")
```

![](CaseStudy2Final_files/figure-html/preliminary-1.png)<!-- -->

```r
hist(casestudy$Age)
```

![](CaseStudy2Final_files/figure-html/preliminary-2.png)<!-- -->

```r
boxplot(DailyRate~Attrition,casestudy,main="DailyRate")
```

![](CaseStudy2Final_files/figure-html/preliminary-3.png)<!-- -->

```r
boxplot(DistanceFromHome~Attrition,casestudy,main="DailyRate")
```

![](CaseStudy2Final_files/figure-html/preliminary-4.png)<!-- -->

```r
boxplot(HourlyRate~Attrition,casestudy,main="HourlyRate")
```

![](CaseStudy2Final_files/figure-html/preliminary-5.png)<!-- -->

```r
boxplot(MonthlyIncome~Attrition,casestudy,main="MonthlyIncome")#Variable of interest
```

![](CaseStudy2Final_files/figure-html/preliminary-6.png)<!-- -->

```r
boxplot(PercentSalaryHike~Attrition,casestudy,main="% Salaray Hike")
```

![](CaseStudy2Final_files/figure-html/preliminary-7.png)<!-- -->

```r
boxplot(TotalWorkingYears~Attrition,casestudy,main="Total Working Years")#Variable of Interest
```

![](CaseStudy2Final_files/figure-html/preliminary-8.png)<!-- -->

```r
boxplot(YearsAtCompany~Attrition,casestudy,main="Years at Company")# ok not the best
```

![](CaseStudy2Final_files/figure-html/preliminary-9.png)<!-- -->

```r
boxplot(YearsInCurrentRole~Attrition,casestudy,main="Years at Current")# Variable of Interest
```

![](CaseStudy2Final_files/figure-html/preliminary-10.png)<!-- -->

```r
boxplot(YearsSinceLastPromotion~Attrition,casestudy,main="Years since last Promo")
```

![](CaseStudy2Final_files/figure-html/preliminary-11.png)<!-- -->

```r
colPerc(xtabs(~Attrition+Department,casestudy))#maybe
```

```
##          Department
## Attrition Human Resources Research & Development  Sales
##     No              80.95                  86.16  79.37
##     Yes             19.05                  13.84  20.63
##     Total          100.00                 100.00 100.00
```

```r
colPerc(xtabs(~Attrition+Education,casestudy))
```

```
##          Education
## Attrition      1     2      3      4      5
##     No     81.76  84.4  82.69  85.43  89.58
##     Yes    18.24  15.6  17.31  14.57  10.42
##     Total 100.00 100.0 100.00 100.00 100.00
```

```r
colPerc(xtabs(~Attrition+Gender,casestudy))
```

```
##          Gender
## Attrition Female   Male
##     No      85.2  82.99
##     Yes     14.8  17.01
##     Total  100.0 100.00
```

```r
colPerc(xtabs(~Attrition+EducationField,casestudy))#maybe
```

```
##          EducationField
## Attrition Human Resources Life Sciences Marketing Medical  Other
##     No              74.07         85.31     77.99   86.42  86.59
##     Yes             25.93         14.69     22.01   13.58  13.41
##     Total          100.00        100.00    100.00  100.00 100.00
##          EducationField
## Attrition Technical Degree
##     No               75.76
##     Yes              24.24
##     Total           100.00
```

```r
colPerc(xtabs(~Attrition+EnvironmentSatisfaction,casestudy))#Variable of Interest
```

```
##          EnvironmentSatisfaction
## Attrition      1      2      3      4
##     No     74.65  85.02  86.31  86.55
##     Yes    25.35  14.98  13.69  13.45
##     Total 100.00 100.00 100.00 100.00
```

```r
colPerc(xtabs(~Attrition+JobInvolvement,casestudy))#Variable of Interest
```

```
##          JobInvolvement
## Attrition      1      2     3      4
##     No     66.27  81.07  85.6  90.97
##     Yes    33.73  18.93  14.4   9.03
##     Total 100.00 100.00 100.0 100.00
```

```r
colPerc(xtabs(~Attrition+JobLevel,casestudy))#Variable of Interest
```

```
##          JobLevel
## Attrition      1      2      3      4      5
##     No     73.66  90.26  85.32  95.28  92.75
##     Yes    26.34   9.74  14.68   4.72   7.25
##     Total 100.00 100.00 100.00 100.00 100.00
```

```r
colPerc(xtabs(~Attrition+JobRole,casestudy))#Variable of Interest
```

```
##          JobRole
## Attrition Healthcare Representative Human Resources Laboratory Technician
##     No                        93.13           76.92                 76.06
##     Yes                        6.87           23.08                 23.94
##     Total                    100.00          100.00                100.00
##          JobRole
## Attrition Manager Manufacturing Director Research Director
##     No       95.1                   93.1              97.5
##     Yes       4.9                    6.9               2.5
##     Total   100.0                  100.0             100.0
##          JobRole
## Attrition Research Scientist Sales Executive Sales Representative
##     No                  83.9           82.52                60.24
##     Yes                 16.1           17.48                39.76
##     Total              100.0          100.00               100.00
```

```r
colPerc(xtabs(~Attrition+JobSatisfaction,casestudy))#ok not that good
```

```
##          JobSatisfaction
## Attrition      1      2      3      4
##     No     77.16  83.57  83.48  88.67
##     Yes    22.84  16.43  16.52  11.33
##     Total 100.00 100.00 100.00 100.00
```

```r
colPerc(xtabs(~Attrition+MaritalStatus,casestudy))
```

```
##          MaritalStatus
## Attrition Divorced Married Single
##     No       89.91   87.52  74.47
##     Yes      10.09   12.48  25.53
##     Total   100.00  100.00 100.00
```

```r
boxplot(NumCompaniesWorked~Attrition,casestudy)#maybe
```

![](CaseStudy2Final_files/figure-html/preliminary-12.png)<!-- -->

```r
colPerc(xtabs(~Attrition+OverTime,casestudy))
```

```
##          OverTime
## Attrition     No    Yes
##     No     89.56  69.47
##     Yes    10.44  30.53
##     Total 100.00 100.00
```

```r
colPerc(xtabs(~Attrition+PerformanceRating,casestudy))#about the same
```

```
##          PerformanceRating
## Attrition      3      4
##     No     83.92  83.63
##     Yes    16.08  16.37
##     Total 100.00 100.00
```

```r
colPerc(xtabs(~Attrition+StockOptionLevel,casestudy))#Variable of interest
```

```
##          StockOptionLevel
## Attrition      0     1      2      3
##     No     75.59  90.6  92.41  82.35
##     Yes    24.41   9.4   7.59  17.65
##     Total 100.00 100.0 100.00 100.00
```

```r
boxplot(YearsWithCurrManager~Attrition,casestudy)#variable of Interest
```

![](CaseStudy2Final_files/figure-html/preliminary-13.png)<!-- -->

```r
colPerc(xtabs(~Attrition+WorkLifeBalance,casestudy))#variable of Interest
```

```
##          WorkLifeBalance
## Attrition      1      2      3      4
##     No     68.75  83.14  85.78  82.35
##     Yes    31.25  16.86  14.22  17.65
##     Total 100.00 100.00 100.00 100.00
```

```r
boxplot(TotalWorkingYears~Attrition,casestudy)#Variable of Interest
```

![](CaseStudy2Final_files/figure-html/preliminary-14.png)<!-- -->

```r
colPerc(xtabs(~Attrition+TrainingTimesLastYear,casestudy))
```

```
##          TrainingTimesLastYear
## Attrition      0      1      2      3      4      5      6
##     No     72.22  87.32  82.08  85.95  78.86  88.24  90.77
##     Yes    27.78  12.68  17.92  14.05  21.14  11.76   9.23
##     Total 100.00 100.00 100.00 100.00 100.00 100.00 100.00
```

#Final variables Examination                

```r
library(sqldf)
```

```
## Loading required package: gsubfn
```

```
## Loading required package: proto
```

```
## Loading required package: RSQLite
```

```r
library(ggplot2)

hist(casestudy$Age,xlab = "Age", main = "Age Distribution")
```

![](CaseStudy2Final_files/figure-html/final-1.png)<!-- -->

```r
Dept_Attrition <-sqldf("select Department, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by Department,  Attrition")
ggplot(Dept_Attrition, aes(x=Department, y=number_of_employees, fill=Attrition)) + geom_bar(stat="identity") + labs(title="Attrition of Number of Employees Per Department", x="Department", y="Number of Employees") + theme(plot.title = element_text(hjust = 0.5))
```

![](CaseStudy2Final_files/figure-html/final-2.png)<!-- -->

```r
Dept_Attrition$Percent_Employees <- Dept_Attrition$number_of_employees/sum(Dept_Attrition$number_of_employees)
JobRole_Attrition <-sqldf("select JobRole, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by JobRole, Attrition")
JobRole_Attrition$Percent_Employees <- JobRole_Attrition$number_of_employees/sum(JobRole_Attrition$number_of_employees)



#Graphing Stuff
colPerc(xtabs(~Attrition+OverTime,casestudy))
```

```
##          OverTime
## Attrition     No    Yes
##     No     89.56  69.47
##     Yes    10.44  30.53
##     Total 100.00 100.00
```

```r
rowPerc(xtabs(~Attrition+OverTime,casestudy))
```

```
##          OverTime
## Attrition     No    Yes  Total
##       No   76.56  23.44 100.00
##       Yes  46.41  53.59 100.00
```

```r
colPerc(xtabs(~Attrition+WorkLifeBalance,casestudy))#variable of Interest
```

```
##          WorkLifeBalance
## Attrition      1      2      3      4
##     No     68.75  83.14  85.78  82.35
##     Yes    31.25  16.86  14.22  17.65
##     Total 100.00 100.00 100.00 100.00
```

```r
rowPerc(xtabs(~Attrition+WorkLifeBalance,casestudy))#variable of Interest
```

```
##          WorkLifeBalance
## Attrition      1      2      3      4  Total
##       No    4.46  23.20  62.12  10.22 100.00
##       Yes  10.55  24.47  53.59  11.39 100.00
```

```r
colPerc(xtabs(~Attrition+EnvironmentSatisfaction,casestudy))#Variable of Interest
```

```
##          EnvironmentSatisfaction
## Attrition      1      2      3      4
##     No     74.65  85.02  86.31  86.55
##     Yes    25.35  14.98  13.69  13.45
##     Total 100.00 100.00 100.00 100.00
```

```r
rowPerc(xtabs(~Attrition+EnvironmentSatisfaction,casestudy))#Variable of Interest
```

```
##          EnvironmentSatisfaction
## Attrition      1      2      3      4  Total
##       No   17.19  19.79  31.71  31.31 100.00
##       Yes  30.38  18.14  26.16  25.32 100.00
```

```r
colPerc(xtabs(~Attrition+StockOptionLevel,casestudy))#Variable of interest
```

```
##          StockOptionLevel
## Attrition      0     1      2      3
##     No     75.59  90.6  92.41  82.35
##     Yes    24.41   9.4   7.59  17.65
##     Total 100.00 100.0 100.00 100.00
```

```r
rowPerc(xtabs(~Attrition+StockOptionLevel,casestudy))#Variable of interest
```

```
##          StockOptionLevel
## Attrition      0      1      2      3  Total
##       No   38.69  43.80  11.84   5.68 100.00
##       Yes  64.98  23.63   5.06   6.33 100.00
```

```r
colPerc(xtabs(~Attrition+JobLevel,casestudy))#Variable of Interest
```

```
##          JobLevel
## Attrition      1      2      3      4      5
##     No     73.66  90.26  85.32  95.28  92.75
##     Yes    26.34   9.74  14.68   4.72   7.25
##     Total 100.00 100.00 100.00 100.00 100.00
```

```r
rowPerc(xtabs(~Attrition+JobLevel,casestudy))#Variable of Interest
```

```
##          JobLevel
## Attrition      1      2      3      4      5  Total
##       No   32.44  39.09  15.09   8.19   5.19 100.00
##       Yes  60.34  21.94  13.50   2.11   2.11 100.00
```

```r
rowPerc(xtabs(~Attrition+Department,casestudy))#maybe
```

```
##          Department
## Attrition Human Resources Research & Development  Sales  Total
##       No             4.14                  67.15  28.71 100.00
##       Yes            5.06                  56.12  38.82 100.00
```

```r
ggplot(Dept_Attrition, aes(x=Department, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +    theme_minimal()+ggtitle("Attrition of Employees by Department")+theme(plot.title = element_text(hjust = 0.5,size=22),axis.text.x=element_text(angle=90,hjust=0.95,vjust=0.2,size=8))
```

![](CaseStudy2Final_files/figure-html/final-3.png)<!-- -->

```r
ggplot(JobRole_Attrition, aes(x=JobRole, y=number_of_employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Job Role")+theme(plot.title = element_text(hjust = 0.5,size=22),axis.text.x=element_text(angle=90,hjust=0.95,vjust=0.2,size=8))
```

![](CaseStudy2Final_files/figure-html/final-4.png)<!-- -->

```r
colPerc(xtabs(~Attrition+JobRole,casestudy))#Variable of Interest
```

```
##          JobRole
## Attrition Healthcare Representative Human Resources Laboratory Technician
##     No                        93.13           76.92                 76.06
##     Yes                        6.87           23.08                 23.94
##     Total                    100.00          100.00                100.00
##          JobRole
## Attrition Manager Manufacturing Director Research Director
##     No       95.1                   93.1              97.5
##     Yes       4.9                    6.9               2.5
##     Total   100.0                  100.0             100.0
##          JobRole
## Attrition Research Scientist Sales Executive Sales Representative
##     No                  83.9           82.52                60.24
##     Yes                 16.1           17.48                39.76
##     Total              100.0          100.00               100.00
```

```r
rowPerc(xtabs(~Attrition+JobRole,casestudy))#Variable of Interest
```

```
##          JobRole
## Attrition Healthcare Representative Human Resources Laboratory Technician
##       No                       9.89            3.24                 15.98
##       Yes                      3.80            5.06                 26.16
##          JobRole
## Attrition Manager Manufacturing Director Research Director
##       No     7.87                  10.95              6.33
##       Yes    2.11                   4.22              0.84
##          JobRole
## Attrition Research Scientist Sales Executive Sales Representative  Total
##       No               19.87           21.82                 4.06 100.00
##       Yes              19.83           24.05                13.92 100.00
```

```r
ggplot(JobRole_Attrition, aes(x=JobRole, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("% Attrition of Employees by Job Role")+theme(plot.title = element_text(hjust = 0.5,size=22),axis.text.x=element_text(angle=90,hjust=0.95,vjust=0.2,size=8))
```

![](CaseStudy2Final_files/figure-html/final-5.png)<!-- -->

```r
colPerc(xtabs(~Attrition+JobInvolvement,casestudy))#Variable of Interest
```

```
##          JobInvolvement
## Attrition      1      2     3      4
##     No     66.27  81.07  85.6  90.97
##     Yes    33.73  18.93  14.4   9.03
##     Total 100.00 100.00 100.0 100.00
```

```r
rowPerc(xtabs(~Attrition+JobInvolvement,casestudy))
```

```
##          JobInvolvement
## Attrition      1      2      3      4  Total
##       No    4.46  24.66  60.26  10.62 100.00
##       Yes  11.81  29.96  52.74   5.49 100.00
```

```r
JobInvolvement_Attrition <-sqldf("select JobInvolvement, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by JobInvolvement, Attrition")
JobInvolvement_Attrition$Percent_Employees<-JobInvolvement_Attrition$number_of_employees/sum(JobInvolvement_Attrition$number_of_employees)
ggplot(JobInvolvement_Attrition, aes(x=JobInvolvement, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +    theme_minimal()+ggtitle("Attrition of Employees by Job Involvement")+theme(plot.title = element_text(hjust = 0.5,size=22),axis.text.x=element_text(angle=90,hjust=0.95,vjust=0.2,size=8))
```

![](CaseStudy2Final_files/figure-html/final-6.png)<!-- -->

#Plots of some Other Important variables                                                     

```r
#Dept 
Dept_Attrition <-sqldf("select Department, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by Department,  Attrition")
Dept_Attrition$Percent_Employees<-Dept_Attrition$number_of_employees/sum(Dept_Attrition$number_of_employees) 
ggplot(Dept_Attrition, aes(x=Department, y=number_of_employees, fill=Attrition)) + geom_bar(stat="identity") + labs(title="Attrition of Number of Employees Per Department", x="Department", y="Number of Employees") + theme(plot.title = element_text(hjust = 0.5))
```

![](CaseStudy2Final_files/figure-html/other_plots-1.png)<!-- -->

```r
ggplot(Dept_Attrition, aes(x=Department, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +    theme_minimal()+ggtitle("Attrition of Employees by Department")+theme(plot.title = element_text(hjust = 0.5,size=22),axis.text.x=element_text(angle=90,hjust=0.95,vjust=0.2,size=8))
```

![](CaseStudy2Final_files/figure-html/other_plots-2.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ Department,casestudy))
```

```
##          Department
## Attrition Human Resources Research & Development  Sales  Total
##       No             4.14                  67.15  28.71 100.00
##       Yes            5.06                  56.12  38.82 100.00
```

```r
colPerc(xtabs(~Attrition+ Department,casestudy))
```

```
##          Department
## Attrition Human Resources Research & Development  Sales
##     No              80.95                  86.16  79.37
##     Yes             19.05                  13.84  20.63
##     Total          100.00                 100.00 100.00
```

```r
#Job Role
JobRole_Attrition <-sqldf("select JobRole, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by JobRole, Attrition")
JobRole_Attrition$Percent_Employees <- JobRole_Attrition$number_of_employees/
sum(JobRole_Attrition$number_of_employees)
ggplot(JobRole_Attrition, aes(x=JobRole, y=number_of_employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Job Role")+theme(plot.title = element_text(hjust = 0.5,size=22),axis.text.x=element_text(angle=90,hjust=0.95,vjust=0.2,size=8))
```

![](CaseStudy2Final_files/figure-html/other_plots-3.png)<!-- -->

```r
ggplot(JobRole_Attrition, aes(x=JobRole, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("% Attrition of Employees by Job Role")+theme(plot.title = element_text(hjust = 0.5,size=22),axis.text.x=element_text(angle=90,hjust=0.95,vjust=0.2,size=8))
```

![](CaseStudy2Final_files/figure-html/other_plots-4.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ JobRole,casestudy))
```

```
##          JobRole
## Attrition Healthcare Representative Human Resources Laboratory Technician
##       No                       9.89            3.24                 15.98
##       Yes                      3.80            5.06                 26.16
##          JobRole
## Attrition Manager Manufacturing Director Research Director
##       No     7.87                  10.95              6.33
##       Yes    2.11                   4.22              0.84
##          JobRole
## Attrition Research Scientist Sales Executive Sales Representative  Total
##       No               19.87           21.82                 4.06 100.00
##       Yes              19.83           24.05                13.92 100.00
```

```r
colPerc(xtabs(~Attrition+ JobRole,casestudy))
```

```
##          JobRole
## Attrition Healthcare Representative Human Resources Laboratory Technician
##     No                        93.13           76.92                 76.06
##     Yes                        6.87           23.08                 23.94
##     Total                    100.00          100.00                100.00
##          JobRole
## Attrition Manager Manufacturing Director Research Director
##     No       95.1                   93.1              97.5
##     Yes       4.9                    6.9               2.5
##     Total   100.0                  100.0             100.0
##          JobRole
## Attrition Research Scientist Sales Executive Sales Representative
##     No                  83.9           82.52                60.24
##     Yes                 16.1           17.48                39.76
##     Total              100.0          100.00               100.00
```

```r
#Work Life
WorkLifeBalance_Attrition <-sqldf("select WorkLifeBalance, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by WorkLifeBalance, Attrition")
WorkLifeBalance_Attrition$Percent_Employees <- WorkLifeBalance_Attrition$number_of_employees/sum(WorkLifeBalance_Attrition$number_of_employees)
ggplot(WorkLifeBalance_Attrition, aes(x=WorkLifeBalance, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Work Life Balance")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-5.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ WorkLifeBalance,casestudy))
```

```
##          WorkLifeBalance
## Attrition      1      2      3      4  Total
##       No    4.46  23.20  62.12  10.22 100.00
##       Yes  10.55  24.47  53.59  11.39 100.00
```

```r
colPerc(xtabs(~Attrition+ WorkLifeBalance,casestudy))
```

```
##          WorkLifeBalance
## Attrition      1      2      3      4
##     No     68.75  83.14  85.78  82.35
##     Yes    31.25  16.86  14.22  17.65
##     Total 100.00 100.00 100.00 100.00
```

```r
#Environment Satisfaction
EnvironmentSatisfaction_Attrition <-sqldf("select EnvironmentSatisfaction, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by EnvironmentSatisfaction, Attrition")
EnvironmentSatisfaction_Attrition$Percent_Employees <- EnvironmentSatisfaction_Attrition$number_of_employees/sum(EnvironmentSatisfaction_Attrition$number_of_employees)
ggplot(EnvironmentSatisfaction_Attrition, aes(x=EnvironmentSatisfaction, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Environment Satisfaction")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-6.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ EnvironmentSatisfaction,casestudy))
```

```
##          EnvironmentSatisfaction
## Attrition      1      2      3      4  Total
##       No   17.19  19.79  31.71  31.31 100.00
##       Yes  30.38  18.14  26.16  25.32 100.00
```

```r
colPerc(xtabs(~Attrition+ EnvironmentSatisfaction,casestudy))
```

```
##          EnvironmentSatisfaction
## Attrition      1      2      3      4
##     No     74.65  85.02  86.31  86.55
##     Yes    25.35  14.98  13.69  13.45
##     Total 100.00 100.00 100.00 100.00
```

```r
#Job Involvement
JobInvolvement_Attrition <-sqldf("select JobInvolvement, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by JobInvolvement, Attrition")
JobInvolvement_Attrition$Percent_Employees <- JobInvolvement_Attrition$number_of_employees/sum(JobInvolvement_Attrition$number_of_employees)
ggplot(JobInvolvement_Attrition, aes(x=JobInvolvement, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Job Involvement")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-7.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ JobInvolvement,casestudy))
```

```
##          JobInvolvement
## Attrition      1      2      3      4  Total
##       No    4.46  24.66  60.26  10.62 100.00
##       Yes  11.81  29.96  52.74   5.49 100.00
```

```r
colPerc(xtabs(~Attrition+ JobInvolvement,casestudy))
```

```
##          JobInvolvement
## Attrition      1      2     3      4
##     No     66.27  81.07  85.6  90.97
##     Yes    33.73  18.93  14.4   9.03
##     Total 100.00 100.00 100.0 100.00
```

```r
#Stock Option Level
StockOptionLevel_Attrition <-sqldf("select StockOptionLevel, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by StockOptionLevel, Attrition")
StockOptionLevel_Attrition$Percent_Employees <- StockOptionLevel_Attrition$number_of_employees/sum(StockOptionLevel_Attrition$number_of_employees)
ggplot(StockOptionLevel_Attrition, aes(x=StockOptionLevel, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Stock Option Level")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-8.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ StockOptionLevel,casestudy))
```

```
##          StockOptionLevel
## Attrition      0      1      2      3  Total
##       No   38.69  43.80  11.84   5.68 100.00
##       Yes  64.98  23.63   5.06   6.33 100.00
```

```r
colPerc(xtabs(~Attrition+ StockOptionLevel,casestudy))
```

```
##          StockOptionLevel
## Attrition      0     1      2      3
##     No     75.59  90.6  92.41  82.35
##     Yes    24.41   9.4   7.59  17.65
##     Total 100.00 100.0 100.00 100.00
```

```r
#Years Since Last Promotion
YearsSinceLastPromotion_Attrition <-sqldf("select YearsSinceLastPromotion, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by YearsSinceLastPromotion, Attrition")
YearsSinceLastPromotion_Attrition$Percent_Employees <- YearsSinceLastPromotion_Attrition$number_of_employees/sum(YearsSinceLastPromotion_Attrition$number_of_employees)
ggplot(YearsSinceLastPromotion_Attrition, aes(x=YearsSinceLastPromotion, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Years Since Last Promotion")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-9.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ YearsSinceLastPromotion,casestudy))
```

```
##          YearsSinceLastPromotion
## Attrition      0      1      2      3      4      5      6      7      8
##       No   38.20  24.98  10.71   3.49   4.54   3.49   2.11   4.87   1.46
##       Yes  46.41  20.68  11.39   3.80   2.11   0.84   2.53   6.75   0.00
##          YearsSinceLastPromotion
## Attrition      9     10     11     12     13     14     15  Total
##       No    1.05   0.41   1.78   0.81   0.65   0.65   0.81 100.00
##       Yes   1.69   0.42   0.84   0.00   0.84   0.42   1.27 100.00
```

```r
colPerc(xtabs(~Attrition+ YearsSinceLastPromotion,casestudy))
```

```
##          YearsSinceLastPromotion
## Attrition      0      1      2      3     4      5      6      7   8
##     No     81.07  86.27  83.02  82.69  91.8  95.56  81.25  78.95 100
##     Yes    18.93  13.73  16.98  17.31   8.2   4.44  18.75  21.05   0
##     Total 100.00 100.00 100.00 100.00 100.0 100.00 100.00 100.00 100
##          YearsSinceLastPromotion
## Attrition      9     10     11  12  13     14     15
##     No     76.47  83.33  91.67 100  80  88.89  76.92
##     Yes    23.53  16.67   8.33   0  20  11.11  23.08
##     Total 100.00 100.00 100.00 100 100 100.00 100.00
```

```r
#Years in Current Role
YearsInCurrentRole_Attrition <-sqldf("select YearsInCurrentRole, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by YearsInCurrentRole, Attrition")
YearsInCurrentRole_Attrition$Percent_Employees <- YearsInCurrentRole_Attrition$number_of_employees/sum(YearsInCurrentRole_Attrition$number_of_employees)
ggplot(YearsInCurrentRole_Attrition, aes(x=YearsInCurrentRole, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Years in Current Role")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-10.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ YearsInCurrentRole,casestudy))
```

```
##          YearsInCurrentRole
## Attrition      0      1      2      3      4      5      6      7      8
##       No   13.87   3.73  24.66   9.65   7.22   2.84   2.84  15.49   6.65
##       Yes  30.80   4.64  28.69   6.75   6.33   0.42   0.84  13.08   2.95
##          YearsInCurrentRole
## Attrition      9     10     11     12     13     14     15     16     17
##       No    4.95   2.19   1.78   0.73   1.05   0.81   0.49   0.57   0.32
##       Yes   2.53   0.84   0.00   0.42   0.42   0.42   0.84   0.00   0.00
##          YearsInCurrentRole
## Attrition     18  Total
##       No    0.16 100.00
##       Yes   0.00 100.00
```

```r
colPerc(xtabs(~Attrition+ YearsInCurrentRole,casestudy))
```

```
##          YearsInCurrentRole
## Attrition      0     1      2      3      4      5      6      7      8
##     No     70.08  80.7  81.72  88.15  85.58  97.22  94.59  86.04  92.13
##     Yes    29.92  19.3  18.28  11.85  14.42   2.78   5.41  13.96   7.87
##     Total 100.00 100.0 100.00 100.00 100.00 100.00 100.00 100.00 100.00
##          YearsInCurrentRole
## Attrition      9    10  11  12     13     14  15  16  17  18
##     No     91.04  93.1 100  90  92.86  90.91  75 100 100 100
##     Yes     8.96   6.9   0  10   7.14   9.09  25   0   0   0
##     Total 100.00 100.0 100 100 100.00 100.00 100 100 100 100
```

```r
#Training in Last Year
TrainingTimesLastYear_Attrition <-sqldf("select TrainingTimesLastYear, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by TrainingTimesLastYear, Attrition")
TrainingTimesLastYear_Attrition$Percent_Employees <- TrainingTimesLastYear_Attrition$number_of_employees/sum(TrainingTimesLastYear_Attrition$number_of_employees)
ggplot(TrainingTimesLastYear_Attrition, aes(x=TrainingTimesLastYear, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Training in Last Year")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-11.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ TrainingTimesLastYear,casestudy))
```

```
##          TrainingTimesLastYear
## Attrition      0      1      2      3      4      5      6  Total
##       No    3.16   5.03  36.42  34.23   7.87   8.52   4.79 100.00
##       Yes   6.33   3.80  41.35  29.11  10.97   5.91   2.53 100.00
```

```r
colPerc(xtabs(~Attrition+ TrainingTimesLastYear,casestudy))
```

```
##          TrainingTimesLastYear
## Attrition      0      1      2      3      4      5      6
##     No     72.22  87.32  82.08  85.95  78.86  88.24  90.77
##     Yes    27.78  12.68  17.92  14.05  21.14  11.76   9.23
##     Total 100.00 100.00 100.00 100.00 100.00 100.00 100.00
```

```r
#Total Years Working
TotalWorkingYears_Attrition <-sqldf("select TotalWorkingYears, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by TotalWorkingYears, Attrition")
TotalWorkingYears_Attrition$Percent_Employees <- TotalWorkingYears_Attrition$number_of_employees/sum(TotalWorkingYears_Attrition$number_of_employees)
ggplot(TotalWorkingYears_Attrition, aes(x=TotalWorkingYears, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Years in Current Role")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-12.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ TotalWorkingYears,casestudy))
```

```
##          TotalWorkingYears
## Attrition      0      1      2      3      4      5      6      7      8
##       No    0.49   3.33   1.78   2.68   4.14   5.84   8.35   5.11   7.06
##       Yes   2.11  16.88   3.80   3.80   5.06   6.75   9.28   7.59   6.75
##          TotalWorkingYears
## Attrition      9     10     11     12     13     14     15     16     17
##       No    6.97  14.36   2.35   3.49   2.68   2.19   2.84   2.76   2.43
##       Yes   4.22  10.55   2.95   2.11   1.27   1.69   2.11   1.27   1.27
##          TotalWorkingYears
## Attrition     18     19     20     21     22     23     24     25     26
##       No    1.87   1.54   2.27   2.68   1.54   1.62   1.22   1.05   1.05
##       Yes   1.69   1.27   0.84   0.42   0.84   0.84   1.27   0.42   0.42
##          TotalWorkingYears
## Attrition     27     28     29     30     31     32     33     34     35
##       No    0.57   1.05   0.81   0.57   0.65   0.73   0.49   0.32   0.24
##       Yes   0.00   0.42   0.00   0.00   0.42   0.00   0.42   0.42   0.00
##          TotalWorkingYears
## Attrition     36     37     38     40  Total
##       No    0.49   0.32   0.08   0.00 100.00
##       Yes   0.00   0.00   0.00   0.84 100.00
```

```r
colPerc(xtabs(~Attrition+ TotalWorkingYears,casestudy))
```

```
##          TotalWorkingYears
## Attrition      0      1      2      3      4      5     6      7      8
##     No     54.55  50.62  70.97  78.57  80.95  81.82  82.4  77.78  84.47
##     Yes    45.45  49.38  29.03  21.43  19.05  18.18  17.6  22.22  15.53
##     Total 100.00 100.00 100.00 100.00 100.00 100.00 100.0 100.00 100.00
##          TotalWorkingYears
## Attrition      9     10     11     12     13    14    15     16     17
##     No     89.58  87.62  80.56  89.58  91.67  87.1  87.5  91.89  90.91
##     Yes    10.42  12.38  19.44  10.42   8.33  12.9  12.5   8.11   9.09
##     Total 100.00 100.00 100.00 100.00 100.00 100.0 100.0 100.00 100.00
##          TotalWorkingYears
## Attrition     18     19     20     21     22     23     24     25     26
##     No     85.19  86.36  93.33  97.06  90.48  90.91  83.33  92.86  92.86
##     Yes    14.81  13.64   6.67   2.94   9.52   9.09  16.67   7.14   7.14
##     Total 100.00 100.00 100.00 100.00 100.00 100.00 100.00 100.00 100.00
##          TotalWorkingYears
## Attrition  27     28  29  30     31  32     33  34  35  36  37  38  40
##     No    100  92.86 100 100  88.89 100  85.71  80 100 100 100 100   0
##     Yes     0   7.14   0   0  11.11   0  14.29  20   0   0   0   0 100
##     Total 100 100.00 100 100 100.00 100 100.00 100 100 100 100 100 100
```

```r
#Years at Company
YearsAtCompany_Attrition <-sqldf("select YearsAtCompany, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by YearsAtCompany, Attrition")
YearsAtCompany_Attrition$Percent_Employees <- YearsAtCompany_Attrition$number_of_employees/sum(YearsAtCompany_Attrition$number_of_employees)
ggplot(YearsAtCompany_Attrition, aes(x=YearsAtCompany, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Years at Company")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-13.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ YearsAtCompany,casestudy))
```

```
##          YearsAtCompany
## Attrition      0      1      2      3      4      5      6      7      8
##       No    2.27   9.08   8.11   8.76   7.38  14.19   5.43   6.41   5.76
##       Yes   6.75  24.89  11.39   8.44   8.02   8.86   3.80   4.64   3.80
##          YearsAtCompany
## Attrition      9     10     11     12     13     14     15     16     17
##       No    6.00   8.27   2.43   1.14   1.78   1.30   1.54   0.89   0.65
##       Yes   3.38   7.59   0.84   0.00   0.84   0.84   0.42   0.42   0.42
##          YearsAtCompany
## Attrition     18     19     20     21     22     23     24     25     26
##       No    0.97   0.81   2.11   1.05   1.14   0.08   0.41   0.32   0.32
##       Yes   0.42   0.42   0.42   0.42   0.42   0.42   0.42   0.00   0.00
##          YearsAtCompany
## Attrition     27     29     30     31     32     33     34     36     37
##       No    0.16   0.16   0.08   0.16   0.16   0.32   0.08   0.16   0.08
##       Yes   0.00   0.00   0.00   0.42   0.42   0.42   0.00   0.00   0.00
##          YearsAtCompany
## Attrition     40  Total
##       No    0.00 100.00
##       Yes   0.42 100.00
```

```r
colPerc(xtabs(~Attrition+ YearsAtCompany,casestudy))
```

```
##          YearsAtCompany
## Attrition      0     1      2      3      4      5      6      7      8
##     No     63.64  65.5  78.74  84.38  82.73  89.29  88.16  87.78  88.75
##     Yes    36.36  34.5  21.26  15.62  17.27  10.71  11.84  12.22  11.25
##     Total 100.00 100.0 100.00 100.00 100.00 100.00 100.00 100.00 100.00
##          YearsAtCompany
## Attrition      9  10     11  12     13     14  15     16     17     18
##     No     90.24  85  93.75 100  91.67  88.89  95  91.67  88.89  92.31
##     Yes     9.76  15   6.25   0   8.33  11.11   5   8.33  11.11   7.69
##     Total 100.00 100 100.00 100 100.00 100.00 100 100.00 100.00 100.00
##          YearsAtCompany
## Attrition     19    20     21     22  23     24  25  26  27  29  30     31
##     No     90.91  96.3  92.86  93.33  50  83.33 100 100 100 100 100  66.67
##     Yes     9.09   3.7   7.14   6.67  50  16.67   0   0   0   0   0  33.33
##     Total 100.00 100.0 100.00 100.00 100 100.00 100 100 100 100 100 100.00
##          YearsAtCompany
## Attrition     32  33  34  36  37  40
##     No     66.67  80 100 100 100   0
##     Yes    33.33  20   0   0   0 100
##     Total 100.00 100 100 100 100 100
```

```r
#Performance Rating
PerformanceRating_Attrition <-sqldf("select PerformanceRating, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by PerformanceRating, Attrition")
PerformanceRating_Attrition$Percent_Employees <- PerformanceRating_Attrition$number_of_employees/sum(PerformanceRating_Attrition$number_of_employees)
ggplot(PerformanceRating_Attrition, aes(x=PerformanceRating, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Performance Rating")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-14.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+PerformanceRating,casestudy))
```

```
##          PerformanceRating
## Attrition      3      4  Total
##       No   84.67  15.33 100.00
##       Yes  84.39  15.61 100.00
```

```r
colPerc(xtabs(~Attrition+PerformanceRating,casestudy))
```

```
##          PerformanceRating
## Attrition      3      4
##     No     83.92  83.63
##     Yes    16.08  16.37
##     Total 100.00 100.00
```

```r
#Percent Salary Hike
PercentSalaryHike_Attrition <-sqldf("select PercentSalaryHike, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by PercentSalaryHike, Attrition")
PercentSalaryHike_Attrition$Percent_Employees <- PercentSalaryHike_Attrition$number_of_employees/sum(PercentSalaryHike_Attrition$number_of_employees)
ggplot(PercentSalaryHike_Attrition, aes(x=PercentSalaryHike, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Percent Salary Hike")+theme(plot.title = element_text(hjust = 0.5,size=22)) 
```

![](CaseStudy2Final_files/figure-html/other_plots-15.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ PercentSalaryHike,casestudy))
```

```
##          PercentSalaryHike
## Attrition     11     12     13     14     15     16     17     18     19
##       No   13.71  13.38  14.19  14.36   6.73   5.19   5.52   6.16   5.43
##       Yes  17.30  13.92  14.35  10.13   7.59   5.91   5.91   5.49   3.80
##          PercentSalaryHike
## Attrition     20     21     22     23     24     25  Total
##       No    3.89   3.49   3.57   1.78   1.22   1.38 100.00
##       Yes   2.95   2.11   5.06   2.53   2.53   0.42 100.00
```

```r
colPerc(xtabs(~Attrition+ PercentSalaryHike,casestudy))
```

```
##          PercentSalaryHike
## Attrition     11     12     13     14     15     16     17     18     19
##     No     80.48  83.33  83.73  88.06  82.18  82.05  82.93  85.39  88.16
##     Yes    19.52  16.67  16.27  11.94  17.82  17.95  17.07  14.61  11.84
##     Total 100.00 100.00 100.00 100.00 100.00 100.00 100.00 100.00 100.00
##          PercentSalaryHike
## Attrition     20     21     22     23     24     25
##     No     87.27  89.58  78.57  78.57  71.43  94.44
##     Yes    12.73  10.42  21.43  21.43  28.57   5.56
##     Total 100.00 100.00 100.00 100.00 100.00 100.00
```

```r
#Job Satisfaction
JobSatisfaction_Attrition <-sqldf("select JobSatisfaction, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by JobSatisfaction, Attrition")
JobSatisfaction_Attrition$Percent_Employees <- JobSatisfaction_Attrition$number_of_employees/sum(JobSatisfaction_Attrition$number_of_employees)
ggplot(JobSatisfaction_Attrition, aes(x=JobSatisfaction, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Job Satisfaction")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-16.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ JobSatisfaction,casestudy))
```

```
##          JobSatisfaction
## Attrition      1      2      3      4  Total
##       No   18.09  18.98  29.93  33.01 100.00
##       Yes  27.85  19.41  30.80  21.94 100.00
```

```r
colPerc(xtabs(~Attrition+ JobSatisfaction,casestudy))
```

```
##          JobSatisfaction
## Attrition      1      2      3      4
##     No     77.16  83.57  83.48  88.67
##     Yes    22.84  16.43  16.52  11.33
##     Total 100.00 100.00 100.00 100.00
```

```r
#Business Travel
BusinessTravel_Attrition <-sqldf("select BusinessTravel, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by BusinessTravel, Attrition")
BusinessTravel_Attrition$Percent_Employees <- BusinessTravel_Attrition$number_of_employees/sum(BusinessTravel_Attrition$number_of_employees)
ggplot(BusinessTravel_Attrition, aes(x=BusinessTravel, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Business Travel")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-17.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ BusinessTravel,casestudy))
```

```
##          BusinessTravel
## Attrition Non-Travel Travel_Frequently Travel_Rarely  Total
##       No       11.19             16.87         71.94 100.00
##       Yes       5.06             29.11         65.82 100.00
```

```r
colPerc(xtabs(~Attrition+ BusinessTravel,casestudy))
```

```
##          BusinessTravel
## Attrition Non-Travel Travel_Frequently Travel_Rarely
##     No            92             75.09         85.04
##     Yes            8             24.91         14.96
##     Total        100            100.00        100.00
```

```r
#Relationship Satisfaction
RelationshipSatisfaction_Attrition <-sqldf("select RelationshipSatisfaction, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by RelationshipSatisfaction, Attrition")
RelationshipSatisfaction_Attrition$Percent_Employees <- RelationshipSatisfaction_Attrition$number_of_employees/sum(RelationshipSatisfaction_Attrition$number_of_employees)
ggplot(RelationshipSatisfaction_Attrition, aes(x=RelationshipSatisfaction, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Relationship Satisfaction")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-18.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ RelationshipSatisfaction,casestudy))
```

```
##          RelationshipSatisfaction
## Attrition      1      2      3      4  Total
##       No   17.76  20.92  31.47  29.85 100.00
##       Yes  24.05  18.99  29.96  27.00 100.00
```

```r
colPerc(xtabs(~Attrition+ RelationshipSatisfaction,casestudy))
```

```
##          RelationshipSatisfaction
## Attrition      1      2      3      4
##     No     79.35  85.15  84.53  85.19
##     Yes    20.65  14.85  15.47  14.81
##     Total 100.00 100.00 100.00 100.00
```

```r
#OverTime
OverTime_Attrition <-sqldf("select OverTime, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by OverTime, Attrition")
OverTime_Attrition$Percent_Employees <- OverTime_Attrition$number_of_employees/sum(OverTime_Attrition$number_of_employees)
ggplot(OverTime_Attrition, aes(x=OverTime, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by OverTime")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-19.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ OverTime,casestudy))
```

```
##          OverTime
## Attrition     No    Yes  Total
##       No   76.56  23.44 100.00
##       Yes  46.41  53.59 100.00
```

```r
colPerc(xtabs(~Attrition+ OverTime,casestudy))
```

```
##          OverTime
## Attrition     No    Yes
##     No     89.56  69.47
##     Yes    10.44  30.53
##     Total 100.00 100.00
```

```r
#Job Level
JobLevel_Attrition <-sqldf("select JobLevel, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by JobLevel, Attrition")
JobLevel_Attrition$Percent_Employees <- JobLevel_Attrition$number_of_employees/sum(JobLevel_Attrition$number_of_employees)
ggplot(JobLevel_Attrition, aes(x=JobLevel, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Stock Option Level")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-20.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ JobLevel,casestudy))
```

```
##          JobLevel
## Attrition      1      2      3      4      5  Total
##       No   32.44  39.09  15.09   8.19   5.19 100.00
##       Yes  60.34  21.94  13.50   2.11   2.11 100.00
```

```r
colPerc(xtabs(~Attrition+ JobLevel,casestudy))
```

```
##          JobLevel
## Attrition      1      2      3      4      5
##     No     73.66  90.26  85.32  95.28  92.75
##     Yes    26.34   9.74  14.68   4.72   7.25
##     Total 100.00 100.00 100.00 100.00 100.00
```

```r
#NumberCompaniesWorked
NumCompaniesWorked_Attrition <-sqldf("select NumCompaniesWorked, Attrition, sum(EmployeeCount) as number_of_employees from casestudy group by NumCompaniesWorked, Attrition")
NumCompaniesWorked_Attrition$Percent_Employees <- NumCompaniesWorked_Attrition$number_of_employees/sum(NumCompaniesWorked_Attrition$number_of_employees)
ggplot(NumCompaniesWorked_Attrition, aes(x=NumCompaniesWorked, y=Percent_Employees, fill=Attrition)) + geom_bar(stat="identity") +
    theme_minimal()+ggtitle("Attrition of Employees by Number of Companies Worked")+theme(plot.title = element_text(hjust = 0.5,size=22))
```

![](CaseStudy2Final_files/figure-html/other_plots-21.png)<!-- -->

```r
rowPerc(xtabs(~Attrition+ NumCompaniesWorked,casestudy))
```

```
##          NumCompaniesWorked
## Attrition      0      1      2      3      4      5      6      7      8
##       No   14.11  34.31  10.54  11.60   9.89   3.81   4.38   4.62   3.49
##       Yes   9.70  41.35   6.75   6.75   7.17   6.75   6.75   7.17   2.53
##          NumCompaniesWorked
## Attrition      9  Total
##       No    3.24 100.00
##       Yes   5.06 100.00
```

```r
colPerc(xtabs(~Attrition+ NumCompaniesWorked,casestudy))
```

```
##          NumCompaniesWorked
## Attrition      0      1      2      3      4     5      6      7      8
##     No     88.32  81.19  89.04  89.94  87.77  74.6  77.14  77.03  87.76
##     Yes    11.68  18.81  10.96  10.06  12.23  25.4  22.86  22.97  12.24
##     Total 100.00 100.00 100.00 100.00 100.00 100.0 100.00 100.00 100.00
##          NumCompaniesWorked
## Attrition      9
##     No     76.92
##     Yes    23.08
##     Total 100.00
```

