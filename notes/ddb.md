# AWS Developer Associate: DynamoDB

## freeCodeCamp ExamPro walkthrough

### Intro

[Video 1](https://youtu.be/RrKRN9zRBWs) 5.05.15. **This is the most important service to know for the exam.**

- Capacity
  - **RCU**: Read capacity unit
  - **WCU**: Write capacity unit
- Anatomy
  - **Tables**
  - **Items** (like rows)
  - **Attributes** (like columns)
  - **Values** (data itself)
- Read consistency
  - Stored on SSD
  - Replicated in ≥3 data centers
  - With the default (Eventual Consistent Reads), there is potential for data to be out of sync among the data centers (updates take place within a second). Strongly consistent reads checks all copies, with the downside of longer latency.

### Partitions

- Slice up table into smaller chunks of data (partitions)
- Speeds up reads for large tables by grouping similar data
- DynamoDB automatically creates partitions:
  - per 10 GB data
  - when RCUs or WCUs are exceeded for a single partition
- DynamoDB has a proprietary internal hash algorithm it uses to decide to which partition to write.
- 5.13.00 Andrew forgot to edit out a clip of him stopping and editing the PowerPoint haha

### Primary keys

- Defined when table is created
- Determines where and how data will be stored in partitions
- Cannot be changed later
- **Simple primary key**: only a partition key. ID is a good value.
- **Composite primary key**: combo of partition and sort key.
  - **Two values can have the same partition key, but the composite of partition key and sort key must be unique.**
  - For example, `Alien` (species of Star Trek aliens) could be the partition key, and `Name` could be the sort key. This would partition the database by `Alien`.
- 5.17.00 Primary key design
  - **Distinct: The primary key should be as unique as possible.**
  - **Uniform: the primary key should evenly divide data.**

### Query

- Video 1 5.18.00
- Query allows you to find items in a table by primary key values
- Return specific attributes with `ProjectionExpression`
- Reverse order with `ScanIndexForward`

### Scan

- Video 1 5.21.00
- Scan through all items and return one or more through filters
- Returns all attributes for every item, or can limit with `ProjectExpression`
- **Avoid scans when possible.** Less efficient than queries.

### Capacity

- Video 1 5.22.00
- **Provisioned capacity** is max capacity allowed to read or write per second
  - Autoscaling can be enabled for provisioned capacity. You can set a floor and ceiling for capacity, and DynamoDB will automatically manage capacity between the floor and ceiling.
  - **Exceeding capacity** results in `ProvisionedThroughputExceededException` (throttling). Throttled requests are dropped, resulting in data loss. **Know this for the exam.**
- **On-demand capacity** is pay per request, so only pay for what you use.
  - Good for unpredictable application traffic, but can become very expensive if traffic spikes.
  - Throughput limited by default upper limits for table (40K RCUs and 40K WCUs), or if you exceed 2x peak capacity within 30 minutes.

### Calculating RCU

- Video 1 5.25.00
- **RCU** (read capacity units):
  - 1 strongly consistent read per second
  - 2 eventually consistent reads per second
  - item ≤4 KB
- **Calculating strong RCUs:** **Exam will ask how to calculate RCUs**
  - Round data up to nearest multiple of 4
  - Divide by 4
  - Multiply by number of reads
  - 50 reads at 40 kb per item: `(40 / 4) x 50` = 500 RCUs
  - 10 reads at 6 kb per item (6 rounds to 8): `(8 / 4) x 10` = 20 RCUs
- **Calculating eventual RCUs**
  - Round data up to nearest multiple of 4
  - Divide by 4
  - Multiply by number of reads
  - Divide result by 2
  - Round up to nearest whole number
  - 11 reads at 9 kb per item: `(12 / 4) x 11 / 2` = 16.5 RCU -> 17 RCU
  - 14 reads at 24 kb per item: `(24 / 4) x 14 / 2` = 42 RCU (Andrew makes a math error here: 24/4=6, not 5)

### Calculating WCU

- Video 1 5.28.50
- Much easier than reads
- **WCU** (write capacity units):
  - 1 write per second
  - item ≤1 kb
- **Calculating WCU**
  - Round to nearest integer
  - Multiply by number of writes

### Global tables

- Video 1 5.29.50
- You can have Amazon manage globally replicated tables

### Transactions

- Video 1 5.31.00
- **Transaction**:
  - Atomic (all or nothing) change to database
  - Can be performed within or across tables
  - If dependent conditions fail, transaction rollback will occur
- Transactions are **ACID**
  - Atomic
  - Consistent
  - Isolated
  - Durable
- Transactions can be performed at **no additional cost** with `TransactWriteItems` and `TransactGetItems`
- There are two underlying reads or writes for each transaction:
  1. Prepare
  2. Commit
- CloudWatch can be used to view these reads and writes
- `ConditionCheck` can be used prior to transactions.

### TTL

- Video 1 5.33.45
- **Time To Live (TTL)**: DynamoDB can delete items when their TTL expires
- Examples: session data, event logs, usage patterns
- Enable TTL by adding a **TTL attribute**. The TTL attribute value for an item will be a **datetime in epoch format** (DynamoDB doesn't have a date time data type).

### DynamoDB streams

- Video 1 5.35.15
- **Streams** can be enabled on tables. They log modifications to items.
- When an insert, update, or delete occurs, the change will be logged and sent to a lambda function.

### DynamoDB errors

- Video 1 5.36.40
- **Exceptions are likely to show up on the exam.**
- `ThrottlingException`: rate of requests exceeds allowed throughput for `CreateTable`, `UpdateTable`, or `DeleteTable`.
- `ProvisionedThroughputExceededException`
- The AWS SDK will automatically retry when an error occurs. It uses exponential backoffs (gradually trying less and less frequently) starting at 50 ms and going up to a minute before stopping.

### Secondary Indices

Video 1 5.39.15

**Secondary Index** is a copy of selected database values used to quickly query data on **keys other than the primary key, with no uniqueness requirement**.

[Types of DynamoDB secondary indices](https://www.dynamodbguide.com/secondary-indexes): **Generally use GSI over LSI**

#### LSI

Local Secondary Index

- **Requires a partition key and a sort key (composite key schema).** The partition key is the same as the base table, but sort key should be different (because the whole idea is to sort differently).
- Query over **single partition**, using partition key
- **Must be specified at table creation.**
- **Strong or eventual consistency**
- Shares provisioned throughput with table it is indexing
- 10 GB limit, 5 LSI per table

#### GSI

Global Secondary Index

- Can specify a completely different structure for a table, using a **simple or composite key schema**. Partition key should be different from base table.
- Queries over **entire table**, across all partitions
- GSI can be **created at any time**
- **Eventual consistency only.** Cannot provide strong consistency.
- Separate throughput from base table
- No size limit, 20 per table default

### DynamoDB Accelerator (DAX)

- DAX is an in-memory cache for DynamoDB, **ideal for read-intensive** cases
- Can reduce response times to microseconds
- App can provide the endpoint for a DAX cluster
- Eventual consistency only
- ElastiCache can also be used for write-intensive cases

### DynamoDB cheat sheet

- Video 1 5.49.00
- Kirk Kirkconnell from AWS helped put this together

### DynamoDB CLI commands

#### Items

- `get-item`
  - Returns attributes for item with given primary key
- `put-item`
  - If no item exists with the given primary key, add new item to table
  - If item exists with the given primary key, replace old item with new item
- `update-item`
  - If no item exists with the given primary key, add new item to table
  - If item exists with the given primary key, edit attributes of existing item
- `batch-get-item`
  - Returns attributes of ≥1 items from ≥1 tables
  - 16 MB total max per operation
  - 100 item max per operation
- `batch-write-item`
  - 16 MB total max
  - 400 KB max for individual items
  - 25 put or delete requests
- `query`: see above
- `scan`: see above

#### Tables

- `create-table`
  - Add new table
  - Table names must be unique within a given region
- `update-table`
  - Modify provisioned throughput, GSI, or streams
- `delete-table`

#### Bulk transactions

- `transact-get-items`
  - Synchronous and atomic
  - Retrieves multiple items from ≥1 tables in a single account and region
  - 25 objects max
  - 4 MB total max
- `transact-write-items`
  - Synchronous
  - Groups ≤25 action requests

### DynamoDB follow-along

Video 1 6.05.45

- Andrew uses the same Cloud9 environment from the [[AWS Developer Associate: Elastic Beanstalk]] follow-along.
- Files: [GitHub - ExamProCo/TheFreeAWSDeveloperAssociate](https://github.com/examproco/thefreeawsdeveloperassociate)
- Data: _starfleet.csv_ (Star Trek)

#### Create table

Video 1 6.10.30

Andrew walks through table creation in the UI and CLI (`aws dynamodb create-table`). Andrew specifies all the arguments in a text file and pastes them onto the command line with Cloud9:

```
~
❯ aws dynamodb create-table \
--table-name Starships \
--attribute-definitions \
AttributeName=ShipClass,AttributeType=S \
AttributeName=Registry,AttributeType=S \
--key-schema \
AttributeName=ShipClass,KeyType=HASH \
AttributeName=Registry,KeyType=RANGE \
--provisioned-throughput \
ReadCapacityUnits=5,WriteCapacityUnits=5 \
--region us-east-2
```

A better way is to generate a skeleton file in YAML, populate the fields there, read the file when creating the table.

[Generating AWS CLI skeleton and input parameters from a JSON or YAML input file - AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/cli-usage-skeleton.html):

> **You can create and consume YAML input skeleton templates only with version 2 of the AWS CLI.** If you use AWS CLI version 1, you can create and consume only JSON input skeleton templates.

```sh
# Generate a skeleton
~
❯ aws dynamodb create-table --generate-cli-skeleton yaml-input > \
~/dev/aws/TheFreeAWSDeveloperAssociate/DynamoDB/dynamodb-starships.yaml

# Edit the skeleton in your text editor
~
❯ code ~/dev/aws/TheFreeAWSDeveloperAssociate/DynamoDB/dynamodb-starships.yaml

# Create the table with the skeleton
~
❯ aws dynamodb create-table --region us-east-2 --cli-input-yaml \
~/dev/aws/TheFreeAWSDeveloperAssociate/DynamoDB/dynamodb-starships.yaml
```

#### Convert CSV to JSON
