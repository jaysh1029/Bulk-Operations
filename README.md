## Improve SQL insert, update, delete and merge performance and overcome SqlBulkCopy limitations
 - Auditing
 - Case Sensitivity
 - Entity DataSource / Lambda Mapping
 - Output Value
 - And more...

##### Scalable
SQL Server - Benchmarks

| Operations | 1,000 Rows | 10,000 Rows | 100,000 Rows | 1,000,000 Rows |
| ---------- | ---------: | ----------: | -----------: | -------------: |
|**Insert**  | 6 ms       | 25 ms       | 200 ms       | 2,000 ms       |
|**Update**  | 50 ms      | 80 ms       | 575 ms       | 6,500 ms       |
|**Delete**  | 45 ms      | 70 ms       | 625 ms       | 6,800 ms       |
|**Merge**   | 65 ms      | 160 ms      | 1,200 ms     | 12,000 ms      |

> _As fast as SqlBulkCopy for insert but with way more capabilities_

##### Extensible
Support Multiple SQL Providers:
- SQL Server 2008+
- SQL Azure
- SQL Compact
- MySQL
- SQLite
- PostgreSQL
- Oracle

Support Multiple Datasources:
- Entity
- DataTable
- DataRow
- DataReader
- DataSet
- Expando Object

## Download
<a href="https://www.nuget.org/packages/Z.BulkOperations/" target="_blank"><img src="https://zzzprojects.github.io/images/nuget/bulk-operations-v.svg" alt="download" /></a>
<a href="https://www.nuget.org/packages/Z.BulkOperations/" target="_blank"><img src="https://zzzprojects.github.io/images/nuget/bulk-operations-d.svg" alt="" /></a>

```
PM> Install-Package Z.BulkOperations
```

_* PRO Version unlocked for the current month_

Stay updated with latest changes

<a href="https://twitter.com/zzzprojects" target="_blank"><img src="http://www.zzzprojects.com/images/twitter_follow.png" alt="Twitter Follow" height="24" /></a>
<a href="https://www.facebook.com/zzzprojects/" target="_blank"><img src="http://www.zzzprojects.com/images/facebook_like.png" alt="Facebook Like" height="24" /></a>

## Insert - Output Identity Value

##### Problem
You need to output newly generated identity value but SqlBulkCopy do not support it.

##### Solution
Map your identity column with output direction.

```
var bulk = new BulkOperation(connection);

bulk.ColumnMappings.Add("CustomerID", ColumnMappingDirectionType.Output);
// ... mappings ...

bulk.BulkInsert(dt);
```

##### Flexibility
You can also output concurrency column (Timestamp) or any other column values. All kind of mapping direction are supported including "Formula" to use with a SQL Formula.

## Entity DataSource / Lambda Mapping
##### Problem
You have a list of entity to insert but SqlBulkCopy doesn't support entity and lambda expression mapping.

##### Solution
Create a generic bulk operations with your entity type and use lambda expression for your column input, output and primary key mapping.

```csharp
var bulk = new BulkOperation<Customer>(connection);

bulk.ColumnInputExpression = c => new { c.Name,  c.FirstName };
bulk.ColumnOutputExpression = c => c.CustomerID;
bulk.ColumnPrimaryKeyExpression = c => c.Code;

bulk.BulkMerge(customers);
```

##### Maintainability
Get rid of hardcoded string and use strongly-typed lambda expressions.

## AutoMapping & Case Sensitivity
##### Problem
You have a DataTable which columns name match name in the database but SqlBulkCopy throw an error because name match are case insensitive.

##### Solution
Turn off case sensitivity with **IsCaseSensitive** property.

```csharp
var bulk = new BulkOperation(connection);

bulk.IsCaseSensitive = false;

bulk.BulkMerge(dt);
```

##### Readability
Remove useless code which would have required to create your own mapping and keep the essentials.

## Support
Contact our outstanding customer support for any request. We usually answer within the next business day, hour, or minutes!

- info@zzzprojects.com
- [Documentation](https://github.com/zzzprojects/Bulk-Operations/wiki)
- [Issues / Questions](https://github.com/zzzprojects/Bulk-Operations/issues)

## PRO
_PRO Version unlocked for the current month_

Features                    | [PRO Version](http://bulk-operations.net/#pro)
--------                    | :-------------: |
Bulk Insert                 | Yes
Bulk Update                 | Yes
Bulk Delete                 | Yes
Bulk Merge                  | Yes
Bulk SaveChanges            | Yes
Bulk Synchornize            | Yes
DeleteFromQuery             | Yes
UpdateFromQuery             | Yes
Commercial License          | Yes
Royalty-Free                | Yes
Support & Upgrades (1 year) | Yes

Learn more about the **[PRO Version](http://bulk-operations.net/#pro)**

## Contribute
The best way to contribute is by **spreading the word** about the library:

 - Blog it
 - Comment it
 - Fork it
 - Star it
 - Share it
 
A **HUGE THANKS** for your help.

## More Projects

**Entity Framework**
- [EntityFramework Extensions](http://entityframework-extensions.net/)
- [EntityFramework Plus](http://entityframework-plus.net)

**Bulk Operations**
- [Bulk Operations](http://bulk-operations.net/)
- [Dapper Plus](http://dapper-plus.net/)

**Expression Evaluator**
- [Eval-SQL.NET](http://eval-sql.net/)
- [Eval-Expression.NET](http://eval-expression.net/)

**Utilities**
- [Extension Methods Library](https://github.com/zzzprojects/Z.ExtensionMethods/)
- [Html Agility Pack](http://html-agility-pack.net/)

**Need more info?** info@zzzprojects.com

Contact our outstanding customer support for any request. We usually answer within the next business day, hour, or minutes!
