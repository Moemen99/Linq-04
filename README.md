# LINQ Filtration: Where Operator

After preparing our customer list and product list, we'll now work with the first category of LINQ operators: Filtration (also known as Restriction).

## The Where Operator

The `Where` operator in LINQ is similar to the WHERE clause in SQL. It allows us to filter a sequence based on a given condition.

### Example: Finding Out-of-Stock Products

In our example, we'll use the `Where` operator to find products that are out of stock (i.e., products with `UnitsInStock` equal to 0).

## Syntax Options

LINQ provides two syntax options for using the `Where` operator:

### 1. Fluent Syntax

The fluent syntax uses extension methods. The `Where` method has two overloads, but we'll use the one that takes a `Func<T, bool>` predicate:

```csharp
var Result = ProductList.Where(P => P.UnitsInStock == 0);

foreach(var item in Result)
{
    Console.WriteLine(item);
}
```

### 2. Query Syntax

The query syntax resembles SQL but is written in the order of execution. It must start with `from` and end with `select` or `group by`:

```csharp
var Result = from P in ProductList
             where P.UnitsInStock == 0
             select P;

foreach(var item in Result)
{
    Console.WriteLine(item);
}
```

## Sample Output

Based on the product data provided, the output might look like this:

```
ProductID:5,ProductName:Chef Anton's Gumbo Mix,CategoryCondiments,UnitPrice:21.3500,UnitsInStock:0
ProductID:17,ProductName:Alice Mutton,CategoryMeat/Poultry,UnitPrice:39.0000,UnitsInStock:0
ProductID:29,ProductName:Thüringer Rostbratwurst,CategoryMeat/Poultry,UnitPrice:123.7900,UnitsInStock:0
ProductID:31,ProductName:Gorgonzola Telino,CategoryDairy Products,UnitPrice:12.5000,UnitsInStock:0
ProductID:53,ProductName:Perth Pasties,CategoryMeat/Poultry,UnitPrice:32.8000,UnitsInStock:0
```

## Key Points

- The `Where` operator filters a sequence based on a predicate.
- It can be used with both fluent and query syntax.
- The condition `UnitsInStock == 0` identifies out-of-stock products.
- Both syntax options produce the same result.

This filtration technique is fundamental in LINQ and can be applied to various scenarios where you need to narrow down a dataset based on specific criteria.
