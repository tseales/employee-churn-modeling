# HR Employee Churn ML Modeling
Nantucket Motors is an automotive company with appx. 15k employees worldwide. I analyzed [gathered employee data](https://www.kaggle.com/datasets/mfaisalqureshi/hr-analytics-and-job-prediction?select=HR_comma_sep.csv) and built a predictive model that identifies employees likely to quit. By pinpointing key factors that influence turnover — such as job satisfaction, workload, and hours-worked — the HR department can implement targeted retention strategies. Ultimately, this data-driven approach will enhance employee satisfaction and reduce the costs associated with recruiting and onboarding new talent.

## Summary of Insights
1. Employees may be overworked.
   - Observed in the data, there is a strong correlation with employee churn and large amounts of hours worked. This is also noticed in lower satisfaction scores among employees with higher-than-average monthly hours.
   - 160 hours is a typical month for 40hrs/week. There was a sizeable group of employees who worked appx. 240–315 hours per month, ultimately leaving the company; 315 hours per month is over 75 hours per week. It's likely this population's satisfaction levels being close to 0 is related.
   
2. Employees are not consistently being promoted.
   - This is evident by a large population of employees leaving the company after not having been promoted within the last 5 years, contrasted with employees that stayed & were promoted within the last 5 years.
   - Employees that left the company after 4 years were observed as being extremely dissatisfied. This could be associated with having worked long hours with no promotion, and expecting to continue working long hours for the foreseeable future.
   - Employee churn may be high due to employees not feeling rewarded for the long hours they are working.
   
3. There are employees with the same amount of projects, that work longer hours than others - contributing to employee churn.
   - A population of employees that left, with more "normal" working hours, have been observed as recording lower satisfaction levels around 0.4. It's difficult to speculate why they might have left without further investigation. It's possible they felt pressured to work more, considering so many of their peers did the same - that pressure could have lowered their satisfaction levels & enforced a decision to leave.
   - A population of employees that stayed, when working above-average-hours (200+) per month, had satisfaction levels ranging above .4; this population of employees largely having been promoted within the last 5 years. 

## Technical Analysis
### **Churn Contributors:** 
While examining the 'Avg. Monthly Hours by Number of Projects', it is evident that for the majority of employees with the same number of projects (3-7), employees that left the company worked longer hours than those that stayed. It is interesting to note, that in the 'Distribution of Satisfaction Level', employees that stayed scored their satisfaction higher than those that left; indicated by the heatmap, a (seemingly small, but apparently existing) negative coorelation being observed between an employee's avg. monthly hours & their satisfaction level. This can possibly be due to employees that provided higher satisfaction levels, being assigned to less projects. A further observation of 100% employees with 7 projects leaving the company (and working the most avg. monthly hours out of the two employee groups) lends to the path that a large number of projects & hours-worked are key factors in churn.

![churn contributor1](https://github.com/user-attachments/assets/2b7af5ad-2269-446a-94a1-8d66df43550e)
</br></br>

### **Variable Correlations:** 
There are a number of notable observations that provided a foundation for further investigation - the number of projects to avg. monthly hours being positively correlated to a notable degree; the number of employees that left being negatively correlated with satisfaction level; an employee's number of projects being negatively correlated with satisfaction level.

![correlation_heatmap](https://github.com/user-attachments/assets/5252125b-2273-42aa-b8c3-ae41e8b8ac96)
</br></br>

### **Champion Model:**
There were 3 models considered for modeling whether or not an employee is likely to leave the company - Logistic Regression, Boosted Decision Tree, Random Forest. The overall dataset was split into *training* & *testing* sets - with 25% being held for testing. The training set was further split into a *validation* set - with 20% being held for validation. The Boosted Decision Tree and Random Forest were cross-validated for the most likely best parameters. As the company wants to both accurately identify employees that may leave the company & reliably be consistent in its predictions, F1 score was chosen as the main comparative measure. The Random Forest model returned the highest F1 score of `.9763`, with the Boosted Decision Tree returning an F1 of `.9476` and the Logistic Regression returning `.4291`. After crowning the Random Forest champion, and re-training it with the *validation* set included in training, it returned an F1 score of `.9752`. 

![champion-classificationmatrix](https://github.com/user-attachments/assets/9fcc8bd4-f786-44ca-a653-c16165759f86)
</br></br>

## Recommendations
1. Reduce/cap the number of projects assigned to employees. 
    * There is notable evidence that employees with a large number of projects leads to churn. Further investigation into why there are certain employees with a large number of projects may be warranted - an initial area for investigation being if this is due to employees with longer tenure undertaking more responsibility. 
2. Further investigation into why there are certain employees who work longer monthly hours for the same number of projects as other employees.
    * Are there common factors in Projects resulting in increased workload; common/consistent hindrances in certain Projects; high-complexity? It may be worth conducting user interviews and depending on results, reconstructing how projects are assigned to employees - e.g., accounting for the number of projects an employee has based on the complexity of projects. 
3. Promoting employees more frequently (data suggests within 3 years); reviewing the process/criteria for promotion; investigating employee-familiarity with overtime & time-off policy.
    * Employees should be familiar with overtime and PTO policies to avoid burnout, decreased satisfaction levels, and enticement to leave the company. Increasing the frequency of promotion may also aid in validating employees for the long hours they work - further investigation into correlations with employee tenure & likelihood to leave is advantageous. We'd also recommend further investigation into salary and tenure correlation.


## Contact
Feel free to contact me on [LinkedIn](https://linkedin.com/in/takaris-seales)!



