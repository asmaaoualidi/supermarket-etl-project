  # Talend ETL Project: Supermarket Sales Data Integration

## 📜 Project Overview
This project demonstrates an ETL process designed to integrate sales data for a supermarket chain operating in multiple cities. Using **Talend**, the process extracts, transforms, and loads data from CSV files into a structured format for analysis of sales performance and trends.



## 📂 Project Structure
    ```bash
    supermarket-etl-project/
    │
    ├── data/
    │   ├── commandes.csv       # Sales data (orders)
    │   ├── clients.csv         # Customer data
    │
    ├── documentation/
    │   ├── Study_Case_Report.docx  # Detailed study case report
    │   └── Screenshots/            # Configuration screenshots from Talend
    │
    ├── workspace/                  # Talend workspace containing all jobs and configurations
    │
    ├── README.md                   # This file
    ```

## 🚀 ETL Process Description
  # Phase 1: Extraction
   - Data sources:
      - Commandes.csv: Contains sales order details (products, clients, prices, quantities).
    - Clients.csv: Contains customer details (company name and creation date).
   - Talend Components Used:
      - tFileInputDelimited for extracting CSV data.
  
  Key Configurations:

   1. File path: Specify the location of the CSV files in the component's settings.
   2. Separator character: Configure the delimiter (,).
   3. Define header: Enable headers for column names.
   4. Data types: Map each column to the appropriate type.
  
  # Phase 2: Transformation

  - Task 1: Data Type Conversion
     - Column requiring conversion: Prix_unitaire (convert from String to Float).
     - Component used: tMap for mapping and transformation.

  - Task 2: Data Joining
     - Join on: ID_Client between Commandes.csv and Clients.csv.
     - Component used: tJoin.

  - Task 3: Calculated Columns
    - Create a new column PrixTotal using the formula:
    PrixTotal = Prix_unitaire * Quantité.
    - Component used: tMap with an expression.

  - Task 4: Aggregation
    - Aggregate PrixTotal to calculate the sum of sales grouped by dimensions:
        Société (Company)
        Ville (City)
        Produit (Product)
        Commande (Order)
        Component used: tAggregateRow.

  - Task 5: Sorting
    - Sort aggregated data in descending order by total sales.
    - Component used: tSortRow.

  # Phase 3: Loading
  
  - Destination: Load the transformed data into a MySQL database.
  - Component used: tMySQLOutput.

  Key Configurations:

  1. Database connection details: Host, port, database name, username, password.
  2. Output table: Specify table name and schema.

## 🛠 How to Run the Project

 1. Clone the repository:

   ```bash
   git clone https://github.com/asmaaoualidi/supermarket-etl-project.git 
   cd supermarket-etl-project  
   ```
 2. Open Talend Studio:

   - Import the workspace located in the workspace/ directory.

 3. Run the ETL Job:

   - Execute each phase to extract, transform, and load the data.
   - View outputs in Talend’s debug console or database tables.


## 📊 Additional Analysis
Duplicate the primary ETL job to perform specific analyses:

 - Sales by City: VentesParVille
 - Sales by Product: VentesParProduit
 - Sales by Order and Company: VentesParCommandeSociete
 - Sales by City and Product: VentesParVilleProduit

## 🤝 Contribution
Contributions are welcome. Please create an issue or submit a pull request with your improvements.

## 📫 Contact
For questions, reach out to:
  Email: oualidiasmaa65@gmail.com
  LinkedIn: Asmaa oualidi






=======
# supermarket-etl-project
Talend ETL Project: Supermarket Sales Data Integration
