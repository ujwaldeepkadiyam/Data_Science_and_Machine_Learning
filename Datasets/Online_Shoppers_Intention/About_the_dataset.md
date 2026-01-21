# Introduction to the Dataset

**Online Shoppers Purchasing Intention Dataset (UCI)**

This dataset captures the **behavior of users during individual browsing sessions on an e-commerce website**.
Each row corresponds to **one complete user session**, starting from the moment a visitor lands on the site and ending when they either **leave the site or complete a purchase**.

The purpose of the dataset is to **understand and predict purchasing intention** based on **how users interact with different types of web pages** during their visit.

From a business perspective, the dataset models the **online purchase funnel**:

> Entry → Exploration → Evaluation → Decision → Exit or Purchase

The variables describe **what kind of pages were visited**, **how many**, and **how long users stayed**, which together provide strong signals about **customer intent, engagement, hesitation, and conversion likelihood**.

This dataset is widely used in:

* E-commerce analytics
* Conversion rate optimization
* Customer behavior modeling
* Purchase prediction systems

---

# Feature-Wise Business Explanation

## 1. **Administrative**

This feature represents the **number of administrative pages visited** during the session.

Administrative pages include actions such as:

* Login or logout
* Account profile
* Order history
* Account settings

**Business meaning:**
Most shopping sessions involve little or no administrative activity. A higher value usually indicates a **returning customer** managing their account or checking previous orders rather than actively browsing products.

---

## 2. **Administrative_Duration**

This measures the **total time spent on administrative pages** during the session.

**Business meaning:**
Administrative actions are typically quick. Long durations often indicate:

* Login or authentication problems
* Account issues
* Pages left open without interaction

This feature helps businesses identify **friction points** that may negatively affect conversion.

---

## 3. **Informational**

This represents the **number of informational pages viewed**, such as:

* FAQs
* Shipping information
* Return and refund policies
* About or contact pages

**Business meaning:**
Informational page visits signal **trust-seeking behavior**, which is common among:

* First-time visitors
* Cautious buyers
* Users comparing policies before purchasing

A moderate number of informational visits is usually a **positive signal**.

---

## 4. **Informational_Duration**

This captures the **time spent reading informational pages**.

**Business meaning:**
Time spent here reflects how carefully a user is evaluating the business’s policies.
Very long durations often suggest hesitation or that the page was left open unintentionally.

This feature helps distinguish between **genuine evaluation** and **inactive sessions**.

---

## 5. **ProductRelated**

This feature counts the **number of product pages viewed** during the session.

**Business meaning:**
This is one of the **strongest indicators of shopping intent**.

* Low values → casual browsing
* Moderate values → product comparison
* Higher values → strong interest and buying intent

Businesses closely track this feature to understand **engagement depth**.

---

## 6. **ProductRelated_Duration**

This measures the **total time spent on product pages**.

**Business meaning:**
Longer time spent on product pages usually indicates:

* Careful evaluation
* Reading specifications
* Comparing alternatives

However, extremely long durations may not always increase purchase probability and can reflect indecision or distraction.

---

## 7. **BounceRates**

Bounce rate represents the **probability that a visitor leaves the website after viewing only one page**.

**Business meaning:**
High bounce rates indicate:

* Poor landing page relevance
* Misaligned traffic sources
* Weak first impression

Reducing bounce rate is a key objective in **conversion optimization**.

---

## 8. **ExitRates**

Exit rate measures the **probability that a visitor leaves the website from a specific page**, regardless of how many pages were visited earlier.

**Business meaning:**
Exit rates help identify **where users drop out of the funnel**.

For example:

* High exit rate on product pages → pricing or trust issues
* High exit rate on checkout → payment or UX problems

---

## 9. **PageValues**

This feature represents the **average monetary value attributed to a page**, based on sessions that resulted in purchases.

**Business meaning:**
PageValues directly connect **user behavior to revenue**.

* Pages near checkout tend to have high values
* Informational or landing pages usually have zero value

This feature is especially useful for **revenue attribution and funnel optimization**.

---

## 10. **SpecialDay**

SpecialDay indicates how **close the session occurred to a special shopping event**, such as holidays or promotional days.

**Business meaning:**
As special days approach:

* Shopping urgency increases
* Conversion rates tend to rise

This feature captures **seasonal and event-driven buying behavior**.

---

# Business Interpretation Summary

This dataset allows businesses to answer questions such as:

* Which behaviors indicate high purchase intent?
* Where do customers hesitate or drop out?
* How do engagement depth and time affect conversions?
* How does shopping behavior change near special events?

In short:

> **The dataset models how user behavior translates into revenue outcomes in online retail.**

---

## Thresholds for data cleaning


| Feature                           | Lower Limit | Upper Limit | Business Justification                                           |
| --------------------------------- | ----------- | ----------- | ---------------------------------------------------------------- |
| **Administrative**                | 0           | **15**      | Users rarely visit account/admin pages repeatedly in one session |
| **Administrative_Duration (sec)** | 0           | **1200**    | Login/profile actions should not exceed ~20 minutes              |
| **Informational**                 | 0           | **15**      | FAQ/policy browsing beyond this is unrealistic                   |
| **Informational_Duration (sec)**  | 0           | **1800**    | Reading help pages >30 min usually means tab left open           |
| **ProductRelated**                | 0           | **100**     | Viewing >100 products in one session is unlikely for humans      |
| **ProductRelated_Duration (sec)** | 0           | **7200**    | More than 2 hours on product pages is not meaningful             |
| **BounceRates**                   | **0.01**    | **0.99**    | Exact 0 or 1 suggests abnormal aggregation or tracking           |
| **ExitRates**                     | **0.01**    | **0.99**    | Same reasoning as bounce rate                                    |
| **PageValues**                    | 0           | **200**     | Extremely high page value indicates unstable revenue attribution |
| **SpecialDay**                    | 0           | **1**       | Defined by design — values outside impossible                    |
**Revenue** is the target variable:
* `True` means the customer completed a purchase during the session. 
* `False` means the customer did not complete a purchase during the session.
