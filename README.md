# 1/32-days-Data-Analysts
Daily Data analyst Projects
DAY-1
SQL MINI Project

Identified Top 2 highest revenue-generating patients using Window Functions

SELECT *FROM (SELECT 
        p.patient_name,
        SUM(b.total_amount) AS total_spent,
        RANK() OVER (ORDER BY SUM(b.total_amount) DESC) AS rnk
    FROM patien p  
    JOIN appoint a ON p.patient_id = a.patient_id  
    JOIN bill b ON a.appointment_id = b.appointment_id
    GROUP BY p.patient_name
) ranked_data
WHERE rnk <= 2;

#Joined 3 tables using INNER JOIN
#Used GROUP BY to calculate total spending per patient
#Applied Window Function (RANK) to rank patients by revenue
#Filtered top 2 using outer query
