## Isolation
### Lost update
An update to the data by one transaction that gets overwritten by another transaction

### Dirty read
Reading updated data that is not yet committed

### Non-repeatable read
A single row that is retrieved twice in a transaction but contain different values each time

### Phantom read
A set of rows that are retrieved twice in a transaction using the same query but contain different rows each time
