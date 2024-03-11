Farmers Table
CREATE TABLE Farmers (
    farmer_id INT PRIMARY KEY,
    farmer_name VARCHAR(100),
    farmer_address VARCHAR(255),
    farmer_contact VARCHAR(20)
);

Cattle Breed Table
CREATE TABLE CattleBreed (
    breed_id INT PRIMARY KEY,
    breed_name VARCHAR(100),
    average_weight DECIMAL(10, 2),
    average_milk_production DECIMAL(10, 2)
);

Cattle Table
CREATE TABLE Cattle (
    cattle_id INT PRIMARY KEY,
    cattle_name VARCHAR(100),
    breed_id INT,
    gender VARCHAR(10),
    date_of_birth DATE,
    color VARCHAR(50),
    FOREIGN KEY (breed_id) REFERENCES CattleBreed(breed_id)
);

 Cattle Health Record Table
CREATE TABLE CattleHealthRecord (
    health_record_id INT PRIMARY KEY,
    cattle_id INT,
    veterinarian VARCHAR(100),
    diagnosis VARCHAR(255),
    treatment VARCHAR(255),
    date DATE,
    FOREIGN KEY (cattle_id) REFERENCES Cattle(cattle_id)
);

 Cattle Feeding Table
CREATE TABLE CattleFeeding (
    feeding_id INT PRIMARY KEY,
    cattle_id INT,
    food_type VARCHAR(100),
    quantity DECIMAL(10, 2),
    feeding_time DATETIME,
    FOREIGN KEY (cattle_id) REFERENCES Cattle(cattle_id)
);

 Cattle Vaccination Table
CREATE TABLE CattleVaccination (
    vaccination_id INT PRIMARY KEY,
    cattle_id INT,
    vaccine_name VARCHAR(100),
    date_administered DATE,
    next_due_date DATE,
    FOREIGN KEY (cattle_id) REFERENCES Cattle(cattle_id)
);

Milk Production Table
CREATE TABLE MilkProduction (
    production_id INT PRIMARY KEY,
    cattle_id INT,
    production_date DATE,
    quantity DECIMAL(10, 2),
    FOREIGN KEY (cattle_id) REFERENCES Cattle(cattle_id)
);

 Cattle Breeding Record Table
CREATE TABLE CattleBreedingRecord (
    breeding_id INT PRIMARY KEY,
    sire_id INT,
    dam_id INT,
    breeding_date DATE,
    calf_name VARCHAR(100),
    calf_gender VARCHAR(10),
    FOREIGN KEY (sire_id) REFERENCES Cattle(cattle_id),
    FOREIGN KEY (dam_id) REFERENCES Cattle(cattle_id)
);

 Cattle Expenses Table
CREATE TABLE CattleExpenses (
    expense_id INT PRIMARY KEY,
    cattle_id INT,
    expense_type VARCHAR(100),
    amount DECIMAL(10, 2),
    expense_date DATE,
    FOREIGN KEY (cattle_id) REFERENCES Cattle(cattle_id)Cattle Sales Table
CREATE TABLE CattleSales (
    sale_id INT PRIMARY KEY,
    cattle_id INT,
    buyer_name VARCHAR(100),
    sale_price DECIMAL(10, 2),
    sale_date DATE,
    FOREIGN KEY (cattle_id) REFERENCES Cattle(cattle_id)
);
