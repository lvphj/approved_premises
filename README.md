# The approved_premises repository

The approved_premises repository contains code and outputs relating to the FSA's list of approved food establishments. Specifically, the code retrieves the slaughthouse details from FSA monthly updates of approved food establishments that have been downloaded and stored in the directory monthly_updates. The code opens each monthly file consecutively and compares with the data that already exists in the database. If the name of the slaughthouse is unchanged, the associated details (e.g. postcode, co-ordinates, etc.) are updated to the versions contained in the most recent file. However, if the slaughterhouse name has changed then the original details are retained in the database and the new data is added under the new name. The data is than uploaded to a MySQL database. A csv file is also generated that contains the the latest up-to-date information for any given date.

To recreate the database in MySQL, a new database should be created called `ccir_data` with `CHARSET utf8mb4` and `COLLATION utf8mb4_0900_ai_ci` (default settings since MySQL 8.0.1). The tables in the database can be recreated by running the `approved_food_premises_table_structure.sql` query file, included in this repository.

Currently, the code is set up to process all update files consecutively from scratch. This was done intially to ensure that any algorithm used to decide whether a premises' name had changed would be applied to all updates. However, it is an inefficient approach when the same algorithm is used since the process duplicates the analysis done previously.

The monthly updates of approved food establishments are produced by FSA and are available at: https://www.food.gov.uk/business-guidance/approved-food-establishments#list-of-approved-food-establishments.

Processing of FSA monthly updates of approved food establishments in public domain is allowed by Open Government Licence v3 (see: http://www.nationalarchives.gov.uk/doc/open-government-licence/version/3/).
