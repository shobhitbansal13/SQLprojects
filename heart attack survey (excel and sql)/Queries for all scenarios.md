## scenario 1

-- task 1

SELECT `heart attack likelihood`,Round(avg(`BMI (kg/mÂ²)`),2)as avgbmi,round(avg(`Cholesterol Levels (mg/dL`),2)as avgchlo from `medical history`
JOIN`clinic test results` ON `medical history`.subject_id= `clinic test results`.subject_id
WHERE `heart attack likelihood`= 'Yes'

-- task 2

SELECT `heart attack likelihood`,count(`heart attack likelihood`) as countt from `medical history`
JOIN`clinic test results` ON `medical history`.subject_id= `clinic test results`.subject_id
WHERE `BMI (kg/mÂ²)` > 30 AND `stress level` = 'high'
GROUP BY `heart attack likelihood`

## scenario 2

-- task 1

SELECT `heart attack likelihood`,count(`heart attack likelihood`),Round(avg(`Cholesterol Levels (mg/dL`),2),
`Physical Activity level` from `medical history`
JOIN`clinic test results` ON `medical history`.subject_id= `clinic test results`.subject_id
JOIN `lifestyle factors` ON `medical history`.subject_id= `lifestyle factors`.subject_id
WHERE `Physical Activity level` = 'moderate'
GROUP BY `heart attack likelihood`

-- task 2

SELECT `Physical Activity level`,count(`Physical Activity level`),`Cholesterol Levels (mg/dL` FROM `medical history`
JOIN `lifestyle factors` ON `medical history`.subject_id= `lifestyle factors`.subject_id
WHERE `Cholesterol Levels (mg/dL` > 240 GROUP BY `Physical Activity level`,`Cholesterol Levels (mg/dL`

## scenario 3

-- task 1

SELECT ses,`stress level`,count(`stress level`) as 'stress count' FROM `medical history`
JOIN demographics ON `medical history`.subject_id= demographics.subject_id GROUP BY ses,`stress level`

-- task 2

SELECT ses,`stress level`,count(`stress level`) as 'stress count' FROM `medical history`
JOIN demographics ON `medical history`.subject_id= demographics.subject_id WHERE `stress level`= 'high' GROUP BY ses,`stress level`

## scenario 4

-- task 1

SELECT region,`heart attack likelihood`,count(`heart attack likelihood`) FROM demographics
JOIN`clinic test results` ON demographics.subject_id= `clinic test results`.subject_id
GROUP BY region,`heart attack likelihood` ORDER BY region

-- task 2

SELECT region,round(avg(age),2) as 'avg age' FROM demographics
JOIN`clinic test results` ON demographics.subject_id= `clinic test results`.subject_id
WHERE `heart attack likelihood` = 'yes'
GROUP BY region ORDER BY region

## scenario 5

-- task 1

WITH IndividualDetails AS (
-- Retrieve raw data for individuals with high or low stress levels
SELECT
demographics.subject*id,
CASE
WHEN age BETWEEN 18 AND 25 THEN '18-25'
WHEN age BETWEEN 26 AND 30 THEN '26-30'
ELSE '31-35'
END AS age_group,
gender,
`stress level`
FROM
demographics
JOIN
`clinic test results`
ON demographics.subject_id = `clinic test results`.subject_id
JOIN
`medical history`
ON demographics.subject_id = `medical history`.subject_id
WHERE
`stress level` IN ('high', 'low')
),
StressCounts AS (
-- Aggregate counts of stress levels by age group and gender
SELECT
age_group,
gender,
`stress level`,
COUNT(*) AS count
FROM
IndividualDetails
GROUP BY
age*group, gender, `stress level`
),
StressPercentages AS (
-- Calculate percentages of stress levels within each group
SELECT
age_group,
gender,
`stress level`,
count,
ROUND(count * 100.0 / SUM(count) OVER (PARTITION BY age_group, gender), 2) AS percentage
FROM
StressCounts
)
-- Final SELECT to output the data
SELECT
age_group,
gender,
`stress level`,
count,
percentage
FROM
StressPercentages
ORDER BY
age_group, gender, `stress level`;

-- task 2

WITH highstresslvl AS(
SELECT CASE
WHEN age BETWEEN 18 AND 25 THEN '18-25'
WHEN age BETWEEN 26 AND 30 THEN '26-30'
ELSE '31-35'
END AS age*group,gender,`heart attack likelihood`,`stress level`,
count(*) as 'countt'
FROM `medical history`
JOIN demographics ON demographics.subject*id= `medical history`.subject_id
JOIN `clinic test results` ON `medical history`.subject_id= `clinic test results`.subject_id
WHERE `stress level`= 'high' GROUP BY
age_group, gender, `heart attack likelihood`
),
stresspercent AS(
SELECT age_group,gender,`heart attack likelihood`,countt,
ROUND(countt * 100 / sum(countt) OVER(PARTITION BY age_group),2) as percentage
FROM highstresslvl
)
SELECT age_group,gender,`heart attack likelihood`,countt,percentage FROM stresspercent
ORDER BY age_group, gender, `heart attack likelihood`;

## scenario 6

-- task 1

SELECT CASE
WHEN age BETWEEN 18 AND 25 THEN '18-25'
WHEN age BETWEEN 26 AND 30 THEN '26-30'
ELSE '31-35'
END AS age_group,gender,avg(`BMI (kg/mÂ²)`) , avg(`Cholesterol Levels (mg/dL`),
    (COUNT(*) * SUM(`BMI (kg/mÂ²)` * `Cholesterol Levels (mg/dL`) - SUM(`BMI (kg/mÂ²)`) * SUM(`Cholesterol Levels (mg/dL`)) / 
    (SQRT((COUNT(*) * SUM(POWER(`BMI (kg/mÂ²)`, 2)) - POWER(SUM(`BMI (kg/mÂ²)`), 2)) * 
          (COUNT(*) * SUM(POWER(`Cholesterol Levels (mg/dL`, 2)) - POWER(SUM(`Cholesterol Levels (mg/dL`), 2)))) AS correlation_coefficient
FROM demographics
JOIN `medical history` ON demographics.subject_id= `medical history`.subject_id
JOIN `clinic test results` ON demographics.subject_id= `clinic test results`.subject_id
WHERE `heart attack likelihood`= 'yes' GROUP BY age_group,gender
ORDER BY age_group

-- task 2

WITH gender_stats AS (
    SELECT 
        d.subject_id AS id,
        d.gender,
        mh.`BMI (kg/mÂ²)`,
        mh.`Cholesterol Levels (mg/dL`,
        d.age,
        CASE
            WHEN d.age BETWEEN 18 AND 25 THEN '18-25'
            WHEN d.age BETWEEN 26 AND 30 THEN '26-30'
            ELSE '31-35'
        END AS age_group,
        CASE 
            WHEN d.gender = 'male' THEN
                CASE
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 15.0 AND 30.0 AND d.age BETWEEN 18 AND 25 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 100 AND 150 THEN 'low risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 30.1 AND 40.0 AND d.age BETWEEN 26 AND 35 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 151 AND 300 THEN 'high risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 15.0 AND 30.0 AND d.age BETWEEN 26 AND 35 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 100 AND 150 THEN 'low risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 30.1 AND 40.0 AND d.age BETWEEN 18 AND 25 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 151 AND 300 THEN 'high risk'
                    ELSE 'medium risk'
                END
            WHEN d.gender = 'female' THEN
                CASE
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 15.0 AND 35.0 AND d.age BETWEEN 18 AND 25 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 100 AND 150 THEN 'low risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 35.1 AND 40.0 AND d.age BETWEEN 26 AND 35 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 151 AND 300 THEN 'high risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 15.0 AND 35.0 AND d.age BETWEEN 26 AND 35 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 100 AND 150 THEN 'low risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 35.1 AND 40.0 AND d.age BETWEEN 18 AND 25 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 151 AND 300 THEN 'high risk'
                    ELSE 'medium risk'
                END
                  WHEN d.gender = 'other' THEN
                CASE
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 15.0 AND 35.0 AND d.age BETWEEN 18 AND 25 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 100 AND 150 THEN 'low risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 35.1 AND 40.0 AND d.age BETWEEN 26 AND 35 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 151 AND 300 THEN 'high risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 15.0 AND 35.0 AND d.age BETWEEN 26 AND 35 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 100 AND 150 THEN 'low risk'
                    WHEN mh.`BMI (kg/mÂ²)` BETWEEN 35.1 AND 40.0 AND d.age BETWEEN 18 AND 25 AND mh.`Cholesterol Levels (mg/dL` BETWEEN 151 AND 300 THEN 'high risk'
                    ELSE 'medium risk'
         END
         END AS risk_status
    FROM demographics d
    JOIN `medical history` mh ON d.subject_id = mh.subject_id
),
risk_counts AS (
    SELECT 
        age_group,
        gender,
        risk_status,
        COUNT(*) AS risk_count
    FROM gender_stats
    GROUP BY age_group, gender, risk_status
)
SELECT 
    rc.age_group,
    rc.gender,
    rc.risk_status,
    rc.risk_count
FROM risk_counts rc
ORDER BY rc.age_group, rc.gender, rc.risk_status;

## scenario 7

-- task 1

WITH category AS (
    SELECT 
        `lifestyle factors`.subject_id AS id,
        CASE 
            WHEN `screen time hrs/day` <= 3 THEN 'low'
            WHEN `screen time hrs/day` >= 8 THEN 'high'
            ELSE 'moderate'
        END AS stcategory
    FROM 
        `lifestyle factors`
),
categorycount AS (
    SELECT 
        category.id AS id,
        category.stcategory AS stcategory,
        COUNT(category.stcategory) AS catcount
    FROM 
        category 
    JOIN `clinic test results` 
        ON category.id = `clinic test results`.subject_id
    WHERE 
        `heart attack likelihood` = 'yes'
    GROUP BY 
        category.stcategory, category.id
)
SELECT 
    categorycount.stcategory,
    COUNT(categorycount.id) AS num_individuals,
    STDDEV(`lifestyle factors`.`screen time hrs/day`) AS standdev
FROM 
    categorycount
JOIN `lifestyle factors` 
    ON categorycount.id = `lifestyle factors`.subject_id
GROUP BY 
    categorycount.stcategory;

-- task 2

With segments AS(
SELECT  `medical history`.subject_id as id,CASE
WHEN age BETWEEN 18 AND 25 THEN '18-25'
WHEN age BETWEEN 26 AND 30 THEN '26-30'
ELSE '31-35'
END AS age_group
FROM `medical history` JOIN demographics ON demographics.subject_id= `medical history`.subject_id
)
SELECT age_group,`heart attack likelihood`,avg(`Cholesterol Levels (mg/dL`) as avgchl,
VARIANCE(`Cholesterol Levels (mg/dL`)
 FROM segments
JOIN `lifestyle factors` ON `lifestyle factors`.subject_id= segments.id
JOIN `clinic test results` ON segments.id= `clinic test results`.subject_id
JOIN `medical history` ON segments.id= `medical history`.subject_id
WHERE `physical activity level`= 'high' GROUP BY age_group,`heart attack likelihood`
ORDER BY age_group


## scenario 8

-- task 1 

WITH segments AS (
    SELECT demographics.subject_id AS id,
           CASE
               WHEN age BETWEEN 18 AND 25 THEN '18-25'
               WHEN age BETWEEN 26 AND 30 THEN '26-30'
               ELSE '31-35'
           END AS age_group
    FROM demographics
),
filterr AS (
    SELECT age_group, `family history`, COUNT(`family history`) AS famcount
    FROM segments 
    JOIN `medical history` ON segments.id = `medical history`.subject_id
    WHERE `family history` = 'yes'
    GROUP BY age_group, `family history`
    ORDER BY age_group
),
total_famcount AS (
    -- Calculate the total number of people with a family history across all age groups
    SELECT SUM(famcount) AS total_famcount
    FROM filterr
),
chlfilter AS(
    SELECT age_group,`Cholesterol Levels (mg/dL`,count(`Cholesterol Levels (mg/dL`) AS chlcount
    FROM segments JOIN `medical history` ON segments.id= `medical history`.subject_id
    WHERE `Cholesterol Levels (mg/dL` >= 240
    GROUP BY age_group,`Cholesterol Levels (mg/dL`
    ORDER BY age_group
),
total_chlcount AS(
    SELECT SUM(chlcount) as total_chlcount FROM chlfilter
)
SELECT 
    filterr.age_group,
    filterr.`family history`,
    filterr.famcount,
    chlfilter.chlcount,
    (filterr.famcount / total_famcount.total_famcount) * 100 AS percent,
    (chlfilter.chlcount / total_chlcount) * 100 as cpercent
FROM filterr
JOIN chlfilter ON filterr.age_group= chlfilter.age_group
JOIN total_famcount ON 1=1    -- This is a cross join to bring the total_famcount into the main query
JOIN total_chlcount ON 1=1  -- This is a cross join to bring the total_chlcount into the main query

-- task 2

WITH malepos AS(
SELECT count(*) as maleposs FROM `medical history` JOIN demographics ON
demographics.subject_id= `medical history`.subject_id WHERE gender= 'male' AND `family history`= 'yes' ),

maleneg AS(
    SELECT count(*) as malenegg FROM `medical history` JOIN demographics ON
demographics.subject_id= `medical history`.subject_id WHERE gender= 'male' AND `family history`= 'no' ),

femalepos AS(
    SELECT count(*) as femaleposs FROM `medical history` JOIN demographics ON
demographics.subject_id= `medical history`.subject_id WHERE gender= 'female' AND `family history`= 'yes' ),

femaleneg AS(
    SELECT count(*) as femalenegg FROM `medical history` JOIN demographics ON
demographics.subject_id= `medical history`.subject_id WHERE gender= 'female' AND `family history`= 'no'
)

SELECT maleposs * 1.0 /malenegg AS 'odds for men',femaleposs * 1.0 / femalenegg AS 'odds for women'
FROM malepos,maleneg,femalepos,femaleneg


## scenario 9

-- task 1

WITH agegroup as(Select demographics.subject_id as id,
 CASE
               WHEN age BETWEEN 18 AND 25 THEN '18-25'
               WHEN age BETWEEN 26 AND 30 THEN '26-30'
               ELSE '31-35'
           END AS age_group FROM demographics),

           avgbp as(
    SELECT age_group,avg(substring_index(`blood pressure`,'/',1)) as avgsyst,                 -- systolic is first three numbers of a bp
    avg(substring_index(`blood pressure`,'/',-1)) as avgdias                                  -- diastolic is rest two numbers of a bp
    FROM `clinic test results` JOIN agegroup ON agegroup.id= `clinic test results`.subject_id
    WHERE `heart attack likelihood`= 'yes' GROUP BY age_group),

            bprange as(
                SELECT age_group,CONCAT(min(`blood pressure`),'-',max(`blood pressure`)) as 'bprange'
                FROM `clinic test results` JOIN agegroup ON agegroup.id= `clinic test results`.subject_id
                GROUP BY age_group
            )
  

            SELECT avgbp.age_group,avgsyst,avgdias,bprange FROM avgbp JOIN bprange ON avgbp.age_group = bprange.age_group
            ORDER BY age_group
            
          
           

-- task 2


WITH agegroup as(Select demographics.subject_id as id,gender,
 CASE
               WHEN age BETWEEN 18 AND 25 THEN '18-25'
               WHEN age BETWEEN 26 AND 30 THEN '26-30'
               ELSE '31-35'
           END AS age_group FROM demographics),

           totalblood as(
            SELECT count(`blood pressure`) as totalbp FROM `clinic test results`
           ),

           highblood as(
            SELECT age_group,gender,count(substring_index(`blood pressure`,'/',1)) as highbp
            FROM `clinic test results` JOIN agegroup ON agegroup.id= `clinic test results`.subject_id
            WHERE `blood pressure` >= 140 GROUP BY age_group,gender),


                   lowblood as(
            SELECT age_group,gender,count(substring_index(`blood pressure`,'/',1)) as lowbp
            FROM `clinic test results` JOIN agegroup ON agegroup.id= `clinic test results`.subject_id
            WHERE `blood pressure` < 140 GROUP BY age_group,gender)

            SELECT highblood.age_group,highblood.gender,(highbp * 1.0 / totalbp) / (lowbp * 1.0 / totalbp) as relativerisk ,
            highblood.highbp as 'count of highbp'
            FROM highblood 
            JOIN lowblood ON highblood.age_group= lowblood.age_group AND highblood.gender= lowblood.gender
            JOIN totalblood ON 1=1
            ORDER BY age_group,gender


## scenario 10

-- task 1

WITH agegroup AS (
    SELECT demographics.subject_id AS id, gender,
        CASE
            WHEN age BETWEEN 18 AND 25 THEN '18-25'
            WHEN age BETWEEN 26 AND 30 THEN '26-30'
            ELSE '31-35'
        END AS age_group
    FROM demographics
),

wd AS (
    SELECT 
        age_group, 
        gender, 
        STDDEV(`BMI (kg/mÂ²)`) AS standev, 
        VARIANCE(`BMI (kg/mÂ²)`) AS variancee,
        MIN(`BMI (kg/mÂ²)`) AS minn, 
        MAX(`BMI (kg/mÂ²)`) AS maxx,
        SUM(`BMI (kg/mÂ²)`) * 1.0 / COUNT(`BMI (kg/mÂ²)`) AS mean
    FROM agegroup
    JOIN `medical history` ON agegroup.id = `medical history`.subject_id
    JOIN `clinic test results` ON agegroup.id = `clinic test results`.subject_id
    WHERE `heart attack likelihood` = 'yes'
    GROUP BY age_group, gender
),

modee AS (
    SELECT 
        age_group, 
        gender, 
        `BMI (kg/mÂ²)` AS bmi_value, 
        COUNT(`BMI (kg/mÂ²)`) AS modecal
    FROM agegroup
    JOIN `medical history` ON agegroup.id = `medical history`.subject_id
    GROUP BY age_group, gender, `BMI (kg/mÂ²)`
),

moderesult AS (
    SELECT 
        modee.age_group, 
        modee.gender, 
        MAX(modecal) AS maxmode
    FROM modee
    GROUP BY age_group, gender
)

SELECT 
    wd.age_group, 
    wd.gender, 
    standev, 
    variancee, 
    minn, 
    maxx, 
    mean, 
    moderesult.maxmode AS mode_frequency, 
    modee.bmi_value AS mode_bmi
FROM wd
JOIN moderesult 
ON moderesult.age_group = wd.age_group AND moderesult.gender = wd.gender
JOIN modee 
ON modee.age_group = wd.age_group 
   AND modee.gender = wd.gender 
   AND modee.modecal = moderesult.maxmode
ORDER BY age_group, gender;


-- task 2

SELECT demographics.gender,`heart attack likelihood`,avg(`Cholesterol Levels (mg/dL`) FROM
`medical history` JOIN demographics ON `medical history`.subject_id= demographics.subject_id
JOIN `clinic test results` ON `clinic test results`.subject_id = `medical history`.subject_id
WHERE `BMI (kg/mÂ²)` >= 30.0 GROUP BY demographics.gender,`heart attack likelihood`
ORDER BY gender 


## senario 11

-- task 1

SELECT  CASE
            WHEN age BETWEEN 18 AND 25 THEN '18-25'
            WHEN age BETWEEN 26 AND 30 THEN '26-30'
            ELSE '31-35'
        END AS age_group,`heart attack likelihood`,count(*) as countt
        FROM demographics JOIN `clinic test results` ON
        demographics.subject_id= `clinic test results`.subject_id
        GROUP BY age_group,`heart attack likelihood`
        ORDER BY age_group


-- task 2

SELECT  CASE
            WHEN age BETWEEN 18 AND 25 THEN '18-25'
            WHEN age BETWEEN 26 AND 30 THEN '26-30'
            ELSE '31-35'
        END AS age_group,`heart attack likelihood`,count(*)as countt,avg(`Cholesterol Levels (mg/dL` ) as avgchlo
        FROM demographics JOIN `clinic test results` ON
        demographics.subject_id= `clinic test results`.subject_id
        JOIN `medical history` ON demographics.subject_id= `medical history`.subject_id
        GROUP BY age_group,`heart attack likelihood`
        ORDER BY age_group


## scenario 12    

-- task 1

SELECT  CASE
            WHEN age BETWEEN 18 AND 25 THEN '18-25'
            WHEN age BETWEEN 26 AND 30 THEN '26-30'
            ELSE '31-35'
        END AS age_group,gender,`stress level`,count(*) as countt
        FROM demographics 
        JOIN `medical history` ON demographics.subject_id= `medical history`.subject_id
        GROUP BY age_group,gender,`stress level`
        ORDER BY age_group


-- task 2

SELECT  CASE
            WHEN age BETWEEN 18 AND 25 THEN '18-25'
            WHEN age BETWEEN 26 AND 30 THEN '26-30'
            ELSE '31-35'
        END AS age_group,gender,`stress level`,count(*) as countt
        FROM demographics 
        JOIN `medical history` ON demographics.subject_id= `medical history`.subject_id
        WHERE `stress level`= 'high'
        GROUP BY age_group,gender,`stress level`
        ORDER BY age_group







            


            
  

          
           


​
 












