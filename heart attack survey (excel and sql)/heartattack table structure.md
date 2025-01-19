
CREATE TABLE DEMOGRAPHICS (age TINYINT null , gender enum ('Male','Female','other') null,
region enum('East','North','West','North-East','Central','South') null , `urban/rural` enum('urban','rural')
null , ses enum('High','Middle','Low') null, subject_id int primary key auto_increment )

CREATE table `lifestyle factors`(`Smoking status` ENUM('Occasionally','Never','Regularly') NULL,
`alcohol consumption` ENUM('Occasionally','Never','Regularly') NULL,
`Diet type` ENUM('Non-Vegetarian','Vegan','Vegetarian') NULL,
`Physical Activity level` ENUM('Sedentary','High','Moderate') NULL,
`Screen Time hrs/day` TINYINT NULL,
`Sleep Duration` TINYINT NULL,subject_id INT pimary key auto_increment,Constraint fk_subject 
FOREIGN KEY (subject_id) 
references demographics(subject_id)
)

CREATE TABLE `medical history` (`family history` ENUM('yes','no') NULL, diabetes ENUM('yes','no') NULL,
hypertension ENUM('yes','no') NULL, `Cholesterol Levels (mg/dL` SMALLINT NULL, `BMI (kg/mÂ²)` FLOAT NULL,
`Stress Level` ENUM('high','low','medium')null,subject_id INT pimary key auto_increment,Constraint fk_subject4 
FOREIGN KEY (subject_id) 
references demographics(subject_id)
)

CREATE TABLE `clinic test results` (`blood pressure` VARCHAR(15) NULL, `heart rate` SMALLINT NULL,
`ecg result` ENUM('normal','abnormal') NULL, `chest pain type` ENUM('Non-anginal','Typical','Atypical','Asymptomatic') NULL,
`max heart rate` SMALLINT NULL, `excercise induced angina` ENUM('yes','no')null, `blood oxy levels` FLOAT NULL,
`triglyceride level mg/dl` SMALLINT NULL,`heart attack likelihood` ENUM('yes','no') NULL,subject_id INT pimary key atro_increment,Constraint fk_subject2 
FOREIGN KEY (subject_id) 
references demographics(subject_id)
)
