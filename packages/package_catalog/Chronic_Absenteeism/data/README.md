
# Data Sources

This package combines multiple data sources which were identified through [research](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Chronic_Absenteeism/docs/OEA%20Chronic%20Abs%20Package%20-%20Use%20Case%20Doc.pdf) as strongly related to absenteeism: 
* **School Information System (SIS)**: Student school, grade, and roster data
* **Barriers to students**: Transportation data, distance from school, school changes, student illness
* **School experiences**: School suspension, disciplinary, behavior, and learning outcome data
* **Engagement data**: School attendance, digital engagement

## Digital Engagement Data

To quanity a student involvment in school, three digital signals were considered. Values were normalized by grade and teacher to account for various uses of these technologies in the classroom.
* **M365 [Education Insights](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights)**: Digital activity related to M365 applications
* **[Clever](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Clever)**: Learning app activity
* **[i-Ready](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/iReady)**: Math and english learning activity

## Predictive Model Results

Predictive models developed for this package use [Azure Machine Learning Studio](https://docs.microsoft.com/en-us/azure/machine-learning/overview-what-is-machine-learning-studio) and [AutoML](https://www.automl.org/automl/). Models were trained an assessed using [Azure Machine Learning Studio](https://docs.microsoft.com/en-us/azure/machine-learning/overview-what-is-machine-learning-studio). Model predictions were explained using [Interpret ML](https://interpret.ml/). PowerBI dashboards were used to assess model fairness. Specifically, the following data signals were generated by models used.
* **Predictions**: Probability (0-100%) and class predictions (chronic absent or not) were stored and used for dashboard visualizations.
* **Explanations**: Model expanations were generated for all predictions. That is, for each predition, model variable importance was assessed and scored. These explanations help identify which model variables are most important for predictions of chronic absense. 
* **Accuracies**: To assess model quality, model predictions were made where true outcomes of chornic absense were already known. Model accuracy can then be computed.

## Power BI Data Model

Below is a view of the data model used in Power BI visualizations. The primary tables and relationships can be seen.
* **model_pbi Table**: Data used to train predictive model and model results.
* **studentattendanceaggregate Table**: Time dependent records of student attendance.
* **model_log Table**: Log of all model assessment results used for model development.
* **attendancegroups Table**: Grouping of attendance codes.
* **school_location Table**: School locations for visualizations.
* Various order and recoding tables.

![](https://github.com/microsoft/OpenEduAnalytics/blob/main/packages/package_catalog/Chronic_Absenteeism/docs/images/powerBiDataModel.png)

## Additional Data Sources

Implementations of this package can use several [OEA Modules](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules) to help ingest data sources that are typically used to understand patterns of chronic absenteeism (see below for list of relevant OEA modules).  

| OEA Module | Description |
| --- | --- |
| [Ed-Fi Data Standards](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Ed-Fi) | For typical Student Information System (SIS) data, including detailed student attendance, demographic, digital activity, and academic data. |
| Microsoft Digital Engagement | Such as M365 [Education Insights](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Education_Insights), or [Microsoft Graph](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Microsoft_Graph) data. |
| Other Digital Learning Apps and Platforms | [Clever](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/Clever) for learning app data and [i-Ready](https://github.com/microsoft/OpenEduAnalytics/tree/main/modules/module_catalog/iReady) for language and math assessments and learning activities. |