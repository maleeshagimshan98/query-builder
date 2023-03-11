# QueryBuilder
A tool to easily generate simple SQL queries.

## About
The QueryBuilder is a PHP class that provides a set of methods for building SQL queries. This class supports building queries for CRUD Operations as well as adding conditions, limits, and offsets to the queries. Additionally, the class supports joining tables and ordering and grouping data.

## Installation

To install the package, add the package to composer.json and update.

````
"require": {
        "maleeshagimshan98/query-builder": "1.0.*"
    }

````

run following command :

```` php composer.phar update ````

## Getting Started

To get started, add this file to your project folder,

````
use Infinite\SimpleOrm\Query\QueryBuilder;

$builder = new QueryBuilder();

````

Here are key methods of the class:

`from(string $table)` : Sets the table to select data from.
`select(array $columns = null)` : Adds columns to select data from. If no columns are specified, all columns are selected.
`where(array $condition)` : Adds a where condition to the query.
`leftJoin(string $tableName, array $condition)` : Adds a left join with another table.
`orderBy(string $column, string $type = "ASC")` : Adds an order by clause to the query.
`limit(string $limit, string $offset)` : Sets the limit and offset of the result.
`insert(string $table, array $values)` : Builds an insert query.
`update(string $table, array $values, array $condition = [])` : Builds an update query.
`delete(string $table, array $condition = [])` : Builds a delete query.


## SELECT

select data from the users table, the following code can be used:

````
$builder = new QueryBuilder();
$builder->from('users');
$builder->select(['id', 'name', 'email']);
$query = $builder->sql();

````

## SELECT with WHERE (Only uses "=")

Select data with ````WHERE```` condition. Compares the array's key and value using "=" operator.

Syntax :
    ````where([...['column_name' => 'value_evaluated']])````

````
$builder->from('users');
$builder->select(['id', 'name', 'email'])->where(['id' => '123','name' => "'abc'"])
$query = $builder->sql(); //... returns the generated sql query

````

## SELECT with WHERE (Use comparison operators)

Select data with ````WHERE```` condition, use any comparison operators (=, >, <, etc.)

syntax : 
    ````where([.., [..], ['column_name','comparison_operator', 'value_evaluated']])````

````
$builder->from('users');
$builder->select(['id', 'name', 'email'])->where([['id','=','00002'],['name','=',"'aaaa'"]]);
$query = $builder->sql();

````

## LEFT JOIN

Select data and left join another table

````
$builder->from('users');
$builder->select(['id', 'name', 'email'])->leftJoin('products',[['product.user_id', '=', 'users.id'],['product.type','=','electronic']]);
$query = $builder->sql();

````

### INSERT

To insert data into the users table, the following code can be used:

````
$builder = new QueryBuilder();
$builder->insert('users', ['name' => 'John Doe', 'email' => 'john.doe@example.com']);
$query = $builder->sql();

````

This code will generate a SQL query to insert a new row into the users table with the name 'John Doe' and the email 'john.doe@example.com'.

### UPDATE

To update data in the users table, the following code can be used:

````
$builder = new QueryBuilder();
$builder->update('users', ['name' => 'John Doe', 'email' => 'john.doe@example.com']);
$query = $builder->sql();

````

### DELETE

To delete data in the users table, the following code can be used:

````
$builder = new QueryBuilder();
$builder->delete('users', ['name' => 'John Doe', 'email' => 'john.doe@example.com']);
$query = $builder->sql();

````


Overall, the QueryBuilder provides a convenient and flexible way to build SQL queries in PHP code.



## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement". Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (git checkout -b feature/AmazingFeature)
3. Commit your Changes (git commit -m 'Add some AmazingFeature')
4. Push to the Branch (git push origin feature/AmazingFeature)
5. Open a Pull Request


## Licence
Distributed under the MIT License

## Contact
- name - Maleesha Gimshan
- email - (maleeshagimshan74@gmail.com)