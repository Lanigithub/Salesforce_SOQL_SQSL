## SOQL VS. SQSL in Salesforce
### 1. SOQL: Salesforce Object Query Language,  you can use to read/query saved records or objects in salesforce **_Query Editor_**. SOQL is similar to the standard SQL language but is customized for the Lightning Platform and it is only for querying purpose (SELECT) and not for modifying statements. 
### Difference between SQL and SOQL: In SQL, the data is stored in database tables whereas the data in Salesforce is stored in the form of objects.
### SOQL is used primarily for querying the Salesforce database and retrieving the records. It does not allow data modifying statements like UPDATE, INSERT, etc. 
### To update or insert multiple records in the Salesforce database, it needs to be done using Salesforce's user interface or DML statements: insert, update, upsert,delete, undelete

### 2. SOSL: Salesforce Object Search Language (SOSL) is a Salesforce search language that is used to perform text searches in records. Use SOSL to search **_fields across multiple standard and custom object records_** in Salesforce. SOSL is similar to Apache Lucene.
((https://trailhead.salesforce.com/content/learn/modules/apex_database/apex_database_sosl?trailmix_creator_id=melwo&trailmix_slug=apex-learning)

### When to Use SOQL 
* ### Use **_SOQL_** when you know which objects the data resides in, and you want to:
#### Retrieve data from a single object or from multiple objects that are related to one another.
#### Count the number of records that meet specified criteria.
#### Sort results as part of the query.
#### Retrieve data from number, date, or checkbox fields.

* ### When to Use SOSL
#### Use SOSL when you don’t know which object or field the data resides in, and you want to:
#### Retrieve data for a specific term that you know exists within a field. Because SOSL can tokenize multiple terms within a field and build a search index from this, SOSL searches are faster and can return more relevant results.
#### Retrieve multiple objects and fields efficiently where the objects might or might not be related to one another.
#### Retrieve data for a particular division in an organization using the divisions feature.
#### Retrieve data that’s in Chinese, Japanese, Korean, or Thai. Morphological tokenization for CJKT terms helps ensure accurate results.

***
### 3. **Write SOQL Queries**
(https://trailhead.salesforce.com/content/learn/modules/apex_database/apex_database_soql?trailmix_creator_id=melwo&trailmix_slug=apex-learning)
* ### Learning Objectives:
* #### After completing this unit, you'll be able to:
* #### Write SOQL queries in Apex.
* #### Execute SOQL queries by using the Query Editor in the Developer Console.
* #### Execute SOQL queries embedded in Apex by using Anonymous Apex.
* #### Query related records.
* #### SOQL Syntax: Select fields IN SObejects( Account, Contact Opportunity, Leads) WHERE condition LIMIT n 
* Example:
```
Question 3: find out the name, phone number and Email from Contact with a name start with John or L


SELECT Name, Phone  FROM Contact WHERE (Name LIKE 'John%' OR Name like 'L%' ) ORDER BY Name LIMIT 2

Find all SFDC Computing accounts and all accounts with more than 25 employees whose billing city is Los Angeles

SELECT Name, Phone, industry NumberOfEmployees FROM Account WHERE (Name='SFDC Computing' OR (NumberOfEmployees > 25 AND BillingCity='Los Angeles') ORDER BY Name )


// Return 0 records

```
***
### 4. **Write SOSL Queries** 
(https://trailhead.salesforce.com/content/learn/modules/apex_database/apex_database_sosl?trailmix_creator_id=melwo&trailmix_slug=apex-learning)

* #### Learning Objectives
* #### After completing this unit, you'll be able to:
* #### Describe the differences between SOSL and SOQL.
* #### Search for fields across multiple objects using SOSL queries.
* #### Execute SOSL queries by using the Query Editor in the Developer Console.
* #### Sytax of SOSL: FIND {SearchQuery} IN SearchGroup RETURNING Objects(Fields)
* #### The search query in the Query Editor and the API must be enclosed within curly brackets ({Wingo}). In contrast, in Apex the search query is enclosed within single quotes ('Wingo').
* #### Example: 
```
Query 2: search for account name and Contact with FirstName, LastName and Department as the fields that have any fields with the word {Wingo}

FIND {Wingo} IN ALL FIELDS RETURNING Account(Name), Contact(FirstName, LastName, Department)

// Returning one contact with'Wingo'
```
***

### 5. SOQL and SOSL References: 

https://developer.salesforce.com/docs/atlas.en-us.soql_sosl.meta/soql_sosl/sforce_api_calls_soql_sosl_intro.htm
