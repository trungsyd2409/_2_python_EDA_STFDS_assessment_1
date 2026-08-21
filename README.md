-----------------------------------TASKS--------------------------------------------------------
1. Understand the problem
2. Load and inspect data
3. Identify data issues
4. Clean and preprocess data
5. Univariate EDA
6. Bivariate EDA
7. Compare customer segments
8. Identify important insights
9. Form conclusions related to marketing campaign
10. Write 7-page report




--------------------------1. PROBLEM FORMULATION----------------------------------------
1.1. Identify objectives
    Requirement: A telecommunication company recently launched a marketing campaign to promote the adoption of their new subscription plan among customers. The company seeks assistance in gaining a comprehensive understanding of their customers and identifying the customer segments that display the highest responsiveness to marketing campaigns.
    Objective: Identify customer charecteristics and segments associated with higher likelihood of subscribing to the new telecommunication plan
1.2. Raise research question (how to think about it?, how to raise the appropriate questions related to the problem?)
    RQ1: What proportion of customers subcribed to the new plan?
    RQ2: Which demographic and socioeconomic characteristics are associated with subscription?
    RQ3: Are customers with different financial/loan characteristics more or less likely to subscribe?
    RQ4: Does the method and timing of contact affect subscription outcomes?
    RQ5: Which customer segments appear to be the most responsive to the marketing campaign?:(Most important) 




--------------------------2. FORMULATE HYPOTHESES----------------------------------------
2.1. Put the hypotheses for check EDA
    H1: Cusomers contacted through cellular communication have a higher subscription rate than customers contacted through telephone communication
    H2: Customers with previous successful campaign outcomes are more likely to subscribe
    H3: Subscription rates differ across occupational groups
    H4: Customers who have been contacted fewer times during the current campaign are more likely to subscribe
    Most Important: Does the EDA prove evidence supporting ot contradicting hypothesis?




------------------------------3. LOAD DATASET----------------------------------------




----------------------4. INITIAL DATA INSPECTION----------------------------------------
4.1. Answer some questions
    Q1: How many rows are there in the dataset?
    Q2: What about columns?
    Q3: What is the target variable?
    Q4: Which are numeric variables?
    Q5: Which are categorical variables?




-----------------------------------5. CHECK DATA QUALITY----------------------------------------
5.1. Check missing values
5.2. Check special values like unknown, noexistance




-------------------------6. CHECK DUPLICATE DATA----------------------------------------
Sau đó bạn phải quyết định:
    Có nên remove hay không?
    Không phải duplicate nào cũng nhất thiết là error.
    Nếu toàn bộ record giống hệt nhau và không có identifier để phân biệt customer, bạn có thể cân nhắc loại bỏ duplicate.




---------------------------7. CHECK INVALID VALUES/DATA ERRORS---------------------------   
Bạn cần tìm:
    impossible values
    suspicious values
    inconsistent categories
    wrong data types
    outliers




--------------------------8. FIX DATA TYPES----------------------------------------
Đây là một preprocessing rất quan trọng.
Hiện tại khi đọc file, các numerical columns có thể bị đọc thành object.





-----------------------------9. CLEAN CATEGORICAL VARIABLES---------------------------------------------
chuẩn hóa "yes" "yes " và "YES"





-------------------------10. DECIDE HOW TO HANDLE MISSING/UNKOWN VALUE----------------------------------------
Giải quyết null value và giải thích được tại sao
    Case 1 — NaN
    Case 2 — unknown
Không nên tự động biến tất cả unknown thành NaN rồi xóa.
Đây chính là chỗ bạn cần có reasoning trong report.




-------------------------------11. CHECK TARGET VARIABLE-------------------------------------------------
Dataset của bạn có:
    no: 36,542
    yes: 4,638
    Tức subscription rate khoảng: 11.3%
Điều này rất quan trọng.
Bạn nên ghi nhận:
    The target variable is highly imbalanced, with approximately 11.3% of customers subscribing to the new plan.




--------------------------12. EDA TACHNIQUE 1 - UNIVARIATE ANALYSIS----------------------------------------
Numerical
    mean
    median
    standard deviation
    min
    max
    quartiles
    distribution
-> vẽ histplot, boxplot
Categorical -> vẽ countplot





---------------------------13. EDA TACHNIQUE 2 - BIVARIATE ANALYSIS----------------------------------------
Đây là phần rất quan trọng.
    Bạn không chỉ hỏi:
        "Customer có đặc điểm gì?"
    mà phải hỏi:
        "Customer có đặc điểm gì liên quan đến việc subscribe?"





---------------------------14. EDA TECHNIQUE 3 - NUMERICAL AND TARGET----------------------------------------





--------------------------15. EDA TECHNIQUE 4 - CORRELATION ANALYSIS----------------------------------------
Bạn cần chú ý:
    variables highly correlated
    potential multicollinearity
    relationships between economic indicators




-------------------------16. EDA TECHNIQUE 5 - SEGMENT ANALYSIS----------------------------------------
Đây là phần mình khuyên bạn nhất định nên làm, vì nó trả lời trực tiếp business problem.
Bạn muốn tìm:
    Which customer segments are most responsive?




---------------------------17. FIND CUSTOMER SEGMENTS----------------------------------------
Bạn có thể phát hiện một segment như:
    Customers with a previous successful campaign outcome and contacted via cellular communication show a substantially higher subscription rate.
Đây mới là insight có giá trị cho công ty.




--------------------------18. DONT JUST REPORT NUMBERS----------------------------------------
Đây là điều rất quan trọng để đạt 50% của Criterion 2.

Đừng viết:
    The subscription rate for cellular customers is 15%.
    Câu đó chỉ là observation.

Bạn cần viết theo format:
    Observation:
        Customers contacted via cellular communication have a higher subscription rate than those contacted via telephone.
    Interpretation:
        This suggests that the communication channel may be associated with campaign responsiveness.
    Business implication:
        The company could investigate whether cellular communication should receive greater priority in future campaigns.
Đây mới là insight.





---------------------------19. EDA FOR GROUPS OF VARIABLE----------------------------------------
Bạn có thể chia dataset thành:
    Demographic:
        age
        job
        marital
        education
    Financial / household:
        default
        housing
        loan
    Campaign/contact:
        contact
        month
        day_of_week
        duration
        campaign
        previous
        pdays
        poutcome
    Economic context:
        emp.var.rate
        cons.price.idx
        cons.conf.idx
        euribor3m
        nr.employed


Sau đó phân tích:
    Demographic → subscription
    Financial → subscription
    Campaign → subscription
    Economic → subscription





--------------------------20. THINK ABOUT LEAKAGE----------------------------------------
Một số variables có thể không phù hợp để sử dụng trong một future predictive model, mặc dù chúng rất hữu ích cho EDA.
    Đặc biệt: duration
        Duration là thời lượng cuộc gọi.

    Nếu mục tiêu là:
        predict whether customer will subscribe before/during campaign targeting
        thì duration có thể gây data leakage, bởi vì duration chỉ biết được sau khi cuộc gọi đã diễn ra.

    Bạn nên ghi chú:
        Although call duration may show a strong association with subscription, it may not be suitable as a predictor for pre-campaign targeting because the duration is only known after the contact occurs.

Đây là một insight khá tốt về model development.





---------------------------21. OUTLIERS----------------------------------------
Outlier ≠ error.
Bạn phải phân biệt:
    unusual observation
với:
    impossible observation.




---------------------------22. FINAL EDA CONCLUSIONS----------------------------------------
Sau khi làm tất cả, bạn cần trả lời câu hỏi lớn:
    Who are the customers most responsive to the campaign?
    Bạn nên đưa ra khoảng 3–5 key findings.

Ví dụ structure:
    Finding 1: Một nhóm demographic có subscription rate cao hơn.
    Finding 2: Một communication channel có response rate cao hơn.
    Finding 3: Previous campaign success là một strong indicator.
    Finding 4: Một số variables có distribution/outliers cần lưu ý.
    Finding 5: Target imbalance cần được consideration cho future modelling.






---------------------------23. Report structure ≤ 7 pages----------------------------------------
1. Introduction / Problem Formulation ~0.75 page
    Nội dung:
        business context
        objective
        research questions
        hypotheses

2. Data Description & Preprocessing ~1.5 pages
    Nội dung:
        dataset size
        variables
        data types
        missing values
        unknown values
        duplicates
        invalid values
        data formatting issue
        preprocessing decisions
    Có thể dùng 1 bảng tổng hợp.

3. Exploratory Data Analysis ~3 pages
    Chia thành:
        3.1 Target variable
        3.2 Demographic characteristics
        3.3 Campaign/contact characteristics
        3.4 Numerical variables
        3.5 Customer segmentation
    Không cần nhét tất cả biểu đồ vào report.
    Chọn những biểu đồ thực sự giúp trả lời research questions.

4. Key Findings & Business Implications ~1 page
    Đây là phần rất quan trọng.
        Không chỉ: X is 20%.
        Mà: X is 20%, which suggests...
        và: This may imply that the company should...

5. Conclusion ~0.5 page
    Tóm tắt:
        data quality
        major EDA findings
        responsive segments
        implications
        limitations / future modelling

---------------------------24. Minimum 3 EDA techniques----------------------------------------
Technique 	                Bạn làm gì?                        Mục đích
Univariate analysis	        Histogram, boxplot, frequency	    Hiểu distribution
Bivariate analysis	        Category/numerical vs y	            Tìm association
Correlation analysis	    Correlation matrix	                Tìm relationship giữa numerical variables
Segment analysis	        Group customers	                    Tìm responsive segments
Descriptive statistics	    Mean, median, SD, proportions	    Quantify characteristics

---------------------------25. Important things----------------------------------------
Điều quan trọng nhất: đừng biến report thành "code dump"

Question → Analysis → Result → Interpretation → Business implication

Ví dụ:

    Question:
    Which contact method is associated with higher campaign response?

    Analysis:
    Calculate subscription rate by contact method.

    Result:
    Cellular customers show a higher subscription rate than telephone customers.

    Interpretation:
    This indicates that contact method is associated with campaign response.

    Business implication:
    Cellular communication may be worth prioritising in future campaigns, although this association does not by itself establish causation.

Đây là cách bạn hướng tới điểm cao ở Depth of insight.