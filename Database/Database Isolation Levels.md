Isolation levels dictates how much one transaction know about another.
There are majorly four of them:
1. **Repeatable Read :** It ensures Consistent read under same transaction, even if the another transaction has commited the changes, first txn would not be able to see the changes (if Value already read). 
2. **Read Commited** 
3. **Read Uncommitted** 
4. **Serializable Read**
