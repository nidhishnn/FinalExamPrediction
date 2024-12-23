# Final Exam Score Prediction

Predict Final Exam Scores for Students.

Nidhish Nerur, Angel Xie, James Pinter, Brimar Olafsson, and Yuki Yu

Advanced Analytics Edge Final Project (MIT 15.072)

**Introduction**: Education is crucial to shaping future opportunities, making it vital to understand factors influencing student performance. Our project focuses on predicting academic success for the early identification of struggling students. With these predictions, targeted interventions, such as tutoring or counseling, can improve out- comes and help students reach their potential. By identifying key factors for academic success and challenges, we aim to guide resource allocation and educational policies. Ultimately, this project seeks to provide data- driven recommendations to foster equitable and successful learning environments. Specifically, we divided this problem into two separate Regression and Classification tasks. For the Regression part, we aim to predict the raw numeric final exam score while in the Classification portion, we bin the final exam scores and predict the students' score range.  

**Data Description**: We have a dataset from Kaggle, comprising 6,607 student records with 20 features. These features encompass various aspects of student life, including classroom discipline (e.g., Hours Studied, Attendance), home environment (e.g., Parental Involvement, Family Income, Internet Access), and extracurricular activities (e.g., Extracurricular Activities, Physical Activity). The target variable for our predictive models is the student’s final exam score, providing a quantitative measure of academic performance.

Dataset Source: https://www.kaggle.com/datasets/lainguyn123/student-performance-factors

**Key Results**: The baseline regression model results are shown below:

<img width="676" alt="Screenshot 2024-12-22 at 6 47 13 PM" src="https://github.com/user-attachments/assets/f96122e2-2f4d-4ea3-a292-6dd397b96c86" />

Then, we fine-tuned various hyperparameters associated with each model and experimented with regularization techniques. We further ensembled our top models to see if performance would improve. Subsequently, we visualized the in-sample and out-of-sample R-squared scores for the tuned and ensemble models:

<img width="572" alt="Screenshot 2024-12-22 at 6 49 04 PM" src="https://github.com/user-attachments/assets/ba6e5370-7764-468d-afa3-a39c0387ed91" />

<img width="639" alt="Screenshot 2024-12-22 at 6 49 15 PM" src="https://github.com/user-attachments/assets/dab42005-de3a-44e0-b2a1-e8fcc5848c8f" />

The optimal model is Elastic Net Regression which combines L1 and L2 regularization. This model achieved an out-of-sample R-squared score around 77%, and we wanted to  understand the key features driving the final exam score prediction:

<img width="523" alt="Screenshot 2024-12-22 at 6 51 28 PM" src="https://github.com/user-attachments/assets/515ac50a-191f-4121-8908-b454179dba1b" />

Logically, attendance rates, number of hours studied, and positive peer influence make sense in determining a student’s exam score. It appears that attendance is the most notable feature by quite a large margin, and we expect students who attend class more often are likely understanding the course material better than those who do not. Elastic Net balances interpretability of coefficients with the strongest performance.

As for the classification task, we binned the final exam scores into roughly even bins representing the lowest 25%, 25th to 50th percentile, 50th to 75th percentile, and top 25%. We showcase the Receiver Operating Characteristic Curves for the baseline and tuned models below:

<img width="601" alt="Screenshot 2024-12-22 at 6 53 48 PM" src="https://github.com/user-attachments/assets/8d2982a8-a866-477a-9c30-055696666308" />

<img width="569" alt="Screenshot 2024-12-22 at 6 53 58 PM" src="https://github.com/user-attachments/assets/a49330d4-4267-44e7-a6c5-d23714c9cff8" />

After fine-tuning, nearly all models exhibit substantial performance gains, with Logistic Regression and SVM attaining near-optimal AUC scores of 0.99. However, CART remains an underperformer even after hyperparameter tuning, suggesting inherent limitations in its suitability for this classification task. We recommend Logistic Regression as the primary model for schools to predict student exam score ranges. This model achieves an out-of-sample accuracy of 95.5% and offers a strong balance
between performance and interpretability. Its ability to provide probabilities for outcome categories allows for granular assessments of student performance, making it highly practical for identifying at-risk students. While the SVM model performed similarly, it lacks the same level of interpretability. Models like XGBoost and Random Forest seemed to overfit while CART underperformed significantly. Schools can use logistic regression predictions to guide interventions such as tutoring, counseling, or study groups, ensuring resources are effectively directed to improve outcomes and foster equitable learning opportunities.
