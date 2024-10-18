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




## Multiple Conditions

We can use multiple conditions in the Where clause to further refine our filter. Here's an example to get products that are in stock (UnitsInStock > 0) and belong to the "Meat/Poultry" category:

### Fluent Syntax
```csharp
var Result = ProductList.Where(P => P.UnitsInStock > 0 && P.Category == "Meat/Poultry");
```

### Query Expression
```csharp
Result = from P in ProductList
         where P.UnitsInStock > 0 && P.Category == "Meat/Poultry"
         select P;
```

## Displaying Results
```csharp
foreach (var item in Result)
    Console.WriteLine(item);
```

Based on the provided data, the output might look like:
```
ProductID:9,ProductName:Mishi Kobe Niku,CategoryMeat/Poultry,UnitPrice:97.0000,UnitsInStock:29
ProductID:54,ProductName:Tourtière,CategoryMeat/Poultry,UnitPrice:7.4500,UnitsInStock:21
ProductID:55,ProductName:Pâté chinois,CategoryMeat/Poultry,UnitPrice:24.0000,UnitsInStock:115
```

## Indexed Where (Overload)

The Where method has a second overload that takes a Func with two parameters: the element and its index. This allows for filtering based on element position in the sequence.

### Syntax
```csharp
var Result = ProductList.Where((P, I) => I < 10 && P.UnitsInStock == 0);
```

This query gets out-of-stock products from the first 10 elements in the ProductList.

### Important Notes:
- Indexed Where is only available in fluent syntax.
- It cannot be written with query expression syntax.

Based on the provided data, this might return:
```
ProductID:5,ProductName:Chef Anton's Gumbo Mix,CategoryCondiments,UnitPrice:21.3500,UnitsInStock:0
```

## Key Points

1. The Where operator can use multiple conditions combined with logical operators (&&, ||, etc.).
2. Indexed Where allows filtering based on both element properties and position in the sequence.
3. Indexed Where is exclusive to fluent syntax.

This concludes the overview of filtration operators in LINQ, demonstrating various ways to use the Where clause for precise data filtering.
