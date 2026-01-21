# 1. Introduction to the Dataset

**Online Shoppers Purchasing Intention Dataset (UCI)**

The *Online Shoppers Purchasing Intention* dataset records **how users behave during a single visit (session) to an e-commerce website**.

Each row corresponds to **one user session**, not one user.
A single user may appear multiple times across different sessions, but **each session is independent**.

The dataset is designed to answer a fundamental business question:

> **Can we predict whether a visitor will make a purchase based on their browsing behavior?**

To do this, the dataset captures:

* **Which types of pages the user visited**
* **How many pages they visited**
* **How long they spent on those pages**
* **How they exited the website**
* **Contextual information such as timing and traffic source**

The variable **Revenue** indicates whether the session resulted in a purchase and serves as the **target variable**.
All other variables are **behavioral or contextual features** that attempt to explain this outcome.

---

# 2. Detailed Feature-Wise Explanation (Business Context)

---

## 1. Administrative

**What it measures:**
The number of administrative or account-related pages visited during the session.

**Examples of administrative pages:**

* Login / logout
* Account profile
* Order history
* Address or payment settings

**Business interpretation:**
Most shopping sessions involve **very few or no administrative actions**.
Higher values often indicate:

* Returning customers checking past orders
* Users having account issues
* Sessions focused on account management rather than shopping

Administrative activity alone does **not strongly indicate purchase intent**, but it provides context.

---

## 2. Administrative_Duration

**What it measures:**
Total time (in seconds) spent on administrative pages.

**Business interpretation:**
Administrative actions are usually quick.
Long durations can suggest:

* Login or authentication problems
* Confusion with account settings
* Pages left open without active interaction

This feature helps businesses identify **friction points** that may reduce conversions.

---

## 3. Informational

**What it measures:**
Number of informational pages visited during the session.

**Examples:**

* Shipping details
* Return and refund policies
* FAQs
* Contact or “About us” pages

**Business interpretation:**
Informational page visits reflect **trust-building behavior**.
They are common among:

* First-time visitors
* Risk-averse customers
* Users comparing policies before buying

Moderate values are often a **positive signal** for future purchase.

---

## 4. Informational_Duration

**What it measures:**
Total time spent on informational pages.

**Business interpretation:**
Some time spent here indicates careful evaluation.
Very long durations often mean:

* Indecision
* Overthinking
* Inactive tabs

Thus, this feature helps distinguish **healthy evaluation** from **non-productive sessions**.

---

## 5. ProductRelated

**What it measures:**
Number of product pages viewed during the session.

**Business interpretation:**
This is one of the **strongest behavioral indicators of shopping intent**.

* Low values → casual browsing
* Medium values → comparison shopping
* Higher values → strong buying interest

Businesses often use this metric to identify **high-engagement users**.

---

## 6. ProductRelated_Duration

**What it measures:**
Total time spent on product pages.

**Business interpretation:**
Longer durations suggest:

* Reading specifications
* Comparing products
* Evaluating reviews or pricing

However, extremely long durations may indicate indecision or distraction rather than increased intent.

---

## 7. BounceRates

**What it measures:**
The probability that a visitor leaves the website after viewing only one page.

**Business interpretation:**
A high bounce rate usually signals:

* Poor landing page relevance
* Mismatch between ads and content
* Low-intent or low-quality traffic

Reducing bounce rate is a key goal of **marketing and UX optimization**.

---

## 8. ExitRates

**What it measures:**
The probability that a visitor exits the website from a particular page.

**Business interpretation:**
Exit rate helps identify **where users abandon the shopping journey**.

For example:

* High exit rate on product pages → pricing or trust issues
* High exit rate during checkout → payment or UX problems

This feature is crucial for **funnel analysis**.

---

## 9. PageValues

**What it measures:**
Average monetary value of pages, based on sessions that resulted in purchases.

**Business interpretation:**
PageValues directly link **user navigation patterns to revenue**.

* Pages near checkout typically have high PageValues
* Informational pages usually have low or zero value

This feature is extremely useful for **revenue attribution and optimization**.

---

## 10. SpecialDay

**What it measures:**
How close the session is to a special shopping event (e.g., holiday or promotion).

**Business interpretation:**
As special days approach:

* Urgency increases
* Purchase probability rises

This feature captures **event-driven and seasonal buying behavior**.

---

## 11. Month

**What it measures:**
The month in which the session occurred.

**Business interpretation:**
Shopping behavior varies across months due to:

* Seasonal demand
* Holidays and festivals
* Marketing campaigns

Month helps model **seasonality effects**.

---

## 12. OperatingSystems

**What it measures:**
The operating system used by the visitor.

**Business interpretation:**
Acts as a proxy for:

* Device type (desktop vs mobile)
* User demographics
* Technical compatibility issues

Different operating systems often show different conversion patterns.

---

## 13. Browser

**What it measures:**
The web browser used during the session.

**Business interpretation:**
Browser choice can reflect:

* User tech awareness
* Compatibility or performance issues
* Demographic trends

It may indirectly affect user experience and conversion.

---

## 14. Region

**What it measures:**
Geographic region of the visitor.

**Business interpretation:**
Different regions have:

* Different purchasing power
* Different delivery constraints
* Different buying preferences

This feature supports **regional marketing and logistics planning**.

---

## 15. TrafficType

**What it measures:**
Source of the website visit (search, ads, referrals, etc.).

**Business interpretation:**
Not all traffic sources are equal.

* Some bring high-intent users
* Others bring large volumes with low conversion

This feature is essential for **marketing ROI analysis**.

---

## 16. VisitorType

**What it measures:**
Whether the visitor is new or returning.

**Business interpretation:**
Returning visitors generally:

* Trust the website more
* Convert at higher rates

This is one of the most important **contextual predictors** of purchase.

---

## 17. Weekend

**What it measures:**
Whether the session occurred on a weekend.

**Business interpretation:**
Weekend behavior differs from weekdays:

* Longer browsing sessions
* Different purchase patterns

This feature captures **temporal behavior differences**.

---

## 18. Revenue (Target Variable)

**What it measures:**
Whether the session resulted in a purchase.

* **True** → Purchase occurred
* **False** → No purchase

**Business interpretation:**
Revenue represents the **final business outcome** and is the variable that all other features attempt to explain or predict.

---

# 3. Business-Based Outlier Limits (All 18 Features)

If numeric outliers do **not make business sense**, they are marked as `–`.

| Feature                       | Lower | Upper | Business Reason                                |
| ----------------------------- | ----- | ----- | ---------------------------------------------- |
| Administrative                | 0     | 15    | Excessive account actions are unrealistic      |
| Administrative_Duration (sec) | 0     | 1200  | Admin tasks rarely exceed 20 minutes           |
| Informational                 | 0     | 15    | Excessive info browsing is unlikely            |
| Informational_Duration (sec)  | 0     | 1800  | >30 minutes usually means inactivity           |
| ProductRelated                | 0     | 100   | Viewing >100 products is unrealistic           |
| ProductRelated_Duration (sec) | 0     | 7200  | >2 hours is not meaningful                     |
| BounceRates                   | 0.01  | 0.99  | Extreme values suggest abnormal sessions       |
| ExitRates                     | 0.01  | 0.99  | Same reasoning as bounce rate                  |
| PageValues                    | 0     | 200   | Very high values indicate unstable attribution |
| SpecialDay                    | 0     | 1     | Defined by design                              |
| Month                         | –     | –     | Categorical/temporal                           |
| OperatingSystems              | –     | –     | Categorical                                    |
| Browser                       | –     | –     | Categorical                                    |
| Region                        | –     | –     | Categorical                                    |
| TrafficType                   | –     | –     | Categorical                                    |
| VisitorType                   | –     | –     | Categorical                                    |
| Weekend                       | –     | –     | Binary                                         |
| Revenue                       | –     | –     | Target variable                                |

---

## Final Conceptual Takeaway

> This dataset is a **behavioral snapshot of how intent forms in online shopping**.
> Each feature represents a small part of the customer’s decision-making process,
> and **Revenue captures the final outcome of that process**.


