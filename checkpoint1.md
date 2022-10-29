# Estimating potential employment of graduate students in academia
### Quantifying hiring bias for tenure-track faculty employments
### Project Checkpoint 1
##### 29 October 2022
##### Machine Learning Ninjas: Bhatia, Ghosh, Nwogu

## Outline
- Problem Statement
- Data Visualization
- Relevant Data Patterns
- Preliminary ML Pipeline
- Experimental Results
- Potential Issues
- ML Pipeline Improvement Plans

---

## Problem Statement

Develop a supervised learning model that can predict a professor's success based on their educational background and affiliations. 

ML Tasks: Classification

Notes:

A professor's success is defined in this project as the probability that they do not depart/leave the institution they are currently employed at. On the other hand, the educational background and affiliations consist of different variables pertaining not only to the professor, but also the institution they are employed at.


The study statistically analyzed the data but did not apply any machine learning algorithms for forecasting. We want to take 75% of the cleaned data as the training data and use the remaining 25% and remove certain features for forecasting and predicting potential success of professors at their current universities. 


--- 

## Data Visualization

INSERT GRAPHS HERE

Notes:

- Graphs/Charts of the data with some descriptions. We have some of this from the pitch that we didn't use. Additional ones would be nice.

---

## Data Patterns

### Features
- Domain <- transform Field and keep Academia as the 9th domain
- DegreeInstitutionID
- CurrentInstitutionID
- DegreeInstitutionPrestigeRank
- CurrentInstitutionPrestigeRank
- Gender
- AttritionRate <- calculate from AttritionEvents and NonAttritionEvents
- InstitutionRank

Notes:

- With the graphs we have above. We should easily be able to point out some patters we're noticing in the data which will lead to some of the experimental result conclusions we will make. I  mentioned some of these in the visualizations from the last assignment. However after looking at the data Github I think it will be nice to add more.

---

## Preliminary ML Pipeline 

A summary of the preliminary ML pipeline is as follows:
Study Data -> Attain relevant features -> Feature Engineering -> Model application for training/forecasting -> Forecasting Results
- The preliminary ML pipeline is presented in the diagram below

![Planned ML System Pipeline](https://mermaid.ink/img/pako:eNp1UstuwjAQ_BXLZ_iBHCqhhlaRKCBA7SHOwcRLsPADOWtahPj3OgaiQMCn9ezOrHfWJ1paATShG2V_yy13SMhkwQzDsahgImskw-EbyczeIzMknMzUKNGjtGaJHOt-PoQRHKnKOolb3ci1l5iaeYwEhrE8T63m0hAWJFKoHECnS5ZG_N07Bwb7iR5h7iDEFSy42b2g9ko-wQhwMRwhhoeGogVHiEiH2BCKu3lOARJWkw_baJ6b3GW6vBWaO7vma6kkHouLSTdz89bl0KdpteJ_1lh9_ObK95pn4hGZcg0vXBPP8ZaxsshVjL7g4vyP1WCK51vOe2u_Pvip9HWICRxAkedjTa1p_Rkfwnbqe_M7WLBP-PLm_hV62N_MCWm46uIFHVANLnwsEf73qZmLUdyCBkaTEArudowycw513KNdHk1JE3QeBtTvRVh-KnnluKbJhqsazv84TCqw?type=png)

Notes:

- As observed within the above diagram, the essential implementation of the solution is as follows:
    - Attain relevant features from the dataset that describes the faculty hiring network, also known as the `EdgeList`. These featueres include:
        - `TaxonomyValue`: String. The subscope of the faculty hiring network that this edge is a part of.
        - `InstitutionId`: Integer. A unique identifer for the institution that employed the faculty.
        - `InstitutionName`: String. The name of the institution that employed the faculty.
        - `DegreeInstitutionId`: Integer. A unique identifer for the institution that produced the faculty.
        - `DegreeInstitutionName`: String. The name of the institution that produced the faculty.
        - `Total`: Integer. The total number of faculty employed at `InstitutionName` who received their degree from `DegreeInstitutionName` within the particular the particular subset `TaxonomyValue`. The sum of `Women` and `Men` for the given row.
        - `Men`: Integer. The count of men faculty.
        - `Women`: Integer. The count of women faculty.

    - Attain relevant features from the dataset that describes relevant statistics pertaining to the institutions., also known as the `InstitutionStats`. These features include:
        - `InstitutionName`: String. The name of the institution that employed the faculty.
        - `TaxonomyLevel`: String. The scope of the faculty hiring network that this edge is a part of.
        - `TaxonomyValue`: String. The subscope of the faculty hiring network that this edge is a part of.
        - `NonAttritionEvents`: Integer. the number of faculty who graduated from the institution who did not leave the institution (across all years)
        - `AttritionEvents`: Integer. the number of faculty who graduated from the institution who left the institution (across all years)
        - `ProductionRank`: Integer. the ordinal rank of the institution, in terms of how many faculty they produced
        - `PrestigeRank`: Float. the SpringRank of the institution, scaled from 0-1. A rank of 0 indicates high prestige; a rank of 1 indicates low prestige.
        - `OrdinalPrestigeRank`: Integer. the ordinal version of `PrestigeRank`.
        
    - Perform dimensionality reduction, as well as binarization and discretization, on our initial set of features to extract new features which will represent the input variables. These new/input features are:
        - `Domain`: The academic domain of the faculty
        - `DegreeInstitutionID`: A unique identifer for the institution that produced the faculty.
        - `CurrentInstitutionID`: A unique identifer for the institution that employs the faculty.
        - `DegreeInstitutionPrestigeRank`:The SpringRank of the institution that produced the faculty. It is scaled from 0-1. A rank of 0 indicates high prestige; a rank of 1 indicates low prestige.
        - `CurrentInstitutionPrestigeRank`: The SpringRank of the institution that employs the faculty. It is scaled from 0-1. A rank of 0 indicates high prestige; a rank of 1 indicates low prestige.
        - `Gender`: The gender of the faculty
        - `AttritionRate`: The rate at which attrition occurs at an institution
        - `InstitutionRank`: 
    - Apply a random forest model/algorithm for training and forecasting
    - Attain `AttritionProbability` as the output from the random forest model. This variable represents what a professor's succes is defined by. A lower `AttritionProbability` value indicates greater/higher success while a lower value indicates otherwise.


---

## Experimental Results 

Notes:

- We have a lot of options for this one. We need to decide when we sync what we want to use and how many different results we would want to include. I think the information from the data patterns would help us narrow it down

---

## Potential Issues 

- Do not have access to the individual information
- Missing information that indicates merit, e.g. citations, h-index etc. 

Notes:
- This will be analysis of any potential issues we have. I can't think of any right now, but we may encounter some while looking at the data

---

## ML Pipeline Improvement

- [Requested data through AARC](https://aarcresearch.com/access-our-data)

Notes:

- Steps to improve our ML Pipeline 

---

## References

1. Wapman, K. H., Zhang, S., Clauset, A., & Larremore, D. B. (2022). Quantifying hierarchy and dynamics in US faculty hiring and retention. Nature. https://doi.org/10.1038/s41586-022-05222-x

2. Morgan, A. C., LaBerge, N., Larremore, D. B., Galesic, M., Brand, J. E., & Clauset, A. (2022). Socioeconomic roots of academic faculty. Nature Human Behaviour. https://doi.org/10.1038/s41562-022-01425-4

3. Blesch, K., Hauser, O. P., & Jachimowicz, J. M. (2022). Measuring inequality beyond the Gini coefficient may clarify conflicting findings. Nature Human Behaviour. https://doi.org/10.1038/s41562-022-01430-7

