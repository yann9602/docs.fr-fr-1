---
title: "Procédure pas à pas : accès à un service OData à l’aide des fournisseurs de type (F#)"
description: "Découvrez comment utiliser le fournisseur de type F # ODataService dans F # 3.0 pour générer des types de client pour un service OData et fournit des flux de données que le service de requête."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0adae84c-b0fa-455f-994b-274ecdc6df30
ms.openlocfilehash: 28c2e9a405670f4e5f9512e99e0e6c3e3082856c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-an-odata-service-by-using-type-providers"></a>Procédure pas à pas : accès à un service OData à l’aide des fournisseurs de type

> [!NOTE]
Ce guide a été écrit pour F # 3.0 et sera mise à jour.  Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).

> [!NOTE]
Les liens de référence d’API vous permettront de MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

OData, ce qui signifie Open Data Protocol, est un protocole de transfert de données via Internet. De nombreux fournisseurs de données exposent l’accès à leurs données en publiant un service web OData. Vous pouvez accéder aux données à partir de n’importe quelle source OData dans F # 3.0 à l’aide des types de données qui sont générés automatiquement par le `ODataService` fournisseur de type. Pour plus d’informations sur OData, consultez https://msdn.microsoft.com/library/da3380cc-f6da-4c6c-bdb2-bb86afa59d62.

Cette procédure pas à pas vous montre comment utiliser le fournisseur de type F # ODataService pour générer des types de client pour un service OData et fournit des flux de données que le service de requête.

Les tâches suivantes, décrites dans cette procédure pas à pas, doivent être exécutées dans cet ordre pour la réussite de cette dernière :


- Configuration d’un projet de client pour un service OData
<br />

- L’accès à des types OData
<br />

- Interroger un service OData
<br />

- Vérifier les demandes OData
<br />


## <a name="configuring-a-client-project-for-an-odata-service"></a>Configuration d’un projet de client pour un service OData
Dans cette étape, vous configurez un projet à utiliser un fournisseur de type OData.


#### <a name="to-configure-a-client-project-for-an-odata-service"></a>Pour configurer un projet de client pour un service OData

- Ouvrez un projet d’Application Console F #, puis ajoutez une référence à la `System.Data.Services.Client` assembly Framework.
<br />

- Sous `Extensions`, ajoutez une référence à la `FSharp.Data.TypeProviders` assembly.
<br />

## <a name="accessing-odata-types"></a>L’accès à des types OData
Dans cette étape, vous créez un fournisseur de type qui fournit l’accès aux types et aux données pour un service OData.


#### <a name="to-access-odata-types"></a>Pour accéder aux types d’OData

- Dans l’éditeur de Code, ouvrez un fichier source F # et entrez le code suivant.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type Northwind = ODataService<"http://services.odata.org/Northwind/Northwind.svc/">

let db = Northwind.GetDataContext()
let fullContext = Northwind.ServiceTypes.NorthwindEntities()
```

Dans cet exemple, vous avez appelé le fournisseur de type F # et invité à créer un ensemble de types qui sont basées sur l’URI OData que vous avez spécifié. Deux objets sont disponibles qui contiennent des informations sur les données ; un est un contexte de données simplifié, `db` dans l’exemple. Cet objet contient uniquement les types de données qui sont associés à la base de données, qui incluent les types de tables ou de flux. L’autre objet, `fullContext` dans cet exemple, est une instance de `System.Data.Linq.DataContext` et contient de nombreuses autres propriétés, méthodes et événements.
<br />


## <a name="querying-an-odata-service"></a>Interroger un service OData
Dans cette étape, vous utilisez des expressions de requête F # pour interroger le service OData.


#### <a name="to-query-an-odata-service"></a>Pour interroger un service OData

1. Maintenant que vous avez configuré le fournisseur de type, vous pouvez interroger un service OData.
<br />  OData prend en charge uniquement un sous-ensemble des opérations de requête disponible. Les opérations suivantes et leurs mots clés correspondantes sont prises en charge :
<br />
  - projection (`select`)
<br />

  - le filtrage (`where`, en utilisant chaîne et les opérations de date)
<br />

  - pagination (`skip`, `take`)
<br />

  - classement (`orderBy`, `thenBy`)
<br />

  - `AddQueryOption`et `Expand`, qui sont des opérations OData
<br />

  Pour plus d’informations, consultez [considérations sur LINQ &#40; WCF Data Services &#41; ](https://msdn.microsoft.com/library/ee622463.aspx).
<br />  Si vous souhaitez que toutes les entrées dans un flux ou une table, utilisez la forme la plus simple de l’expression de requête, comme dans le code suivant :
<br />

```fsharp
query {
  for customer in db.Customers do
  select customer
} |> Seq.iter (fun customer ->
                  printfn "ID: %s\nCompany: %s" customer.CustomerID customer.CompanyName
                  printfn "Contact: %s\nAddress: %s" customer.ContactName customer.Address
                  printfn "         %s, %s %s" customer.City customer.Region customer.PostalCode
                  printfn "%s\n" customer.Phone)
```

2. Spécifiez les champs ou les colonnes que vous souhaitez à l’aide d’un tuple après le mot clé select.
<br />

```fsharp
  query { 
    for cat in db.Categories do
    select (cat.CategoryID, cat.CategoryName, cat.Description)
  } |> Seq.iter (fun (id, name, description) ->
                    printfn "ID: %d\nCategory: %s\nDescription: %s\n" id name description)
```

3. Spécifier des conditions à l’aide un `where` clause.
<br />

```fsharp
query {
  for employee in db.Employees do
  where (employee.EmployeeID = 9)
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

4. Spécifiez une condition de la sous-chaîne à la requête à l’aide de la `System.String.Contains(System.String)` (méthode). La requête suivante retourne tous les produits qui ont « Chef » dans leur nom. Notez également l’utilisation de `System.Nullable<'T>.GetValueOrDefault()`. Le `UnitPrice` étant une valeur nullable, vous devez soit obtenir la valeur à l’aide de la `Value` propriété, ou vous devez appeler `System.Nullable<'T>.GetValueOrDefault()`.
<br />

```fsharp
query { 
  for product in db.Products do
  where (product.ProductName.Contains("Chef"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

5. Utilisez la `System.String.EndsWith(System.String)` méthode pour spécifier qu’une chaîne se termine par une certaine sous-chaîne.
<br />

```fsharp
query {
  for product in db.Products do
  where (product.ProductName.EndsWith("u"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

6. Combiner des conditions where clause à l’aide de la `&&` opérateur.
<br />

```fsharp
// Open this module to use the nullable operators ?> and ?<.
open Microsoft.FSharp.Linq.NullableOperators

let salesIn1997 = query { 
  for sales in db.Category_Sales_for_1997 do
  where (sales.CategorySales ?> 50000.00M && sales.CategorySales ?< 60000.0M)
  select sales }

salesIn1997
|> Seq.iter (fun sales ->
                printfn "Category: %s Sales: %M" sales.CategoryName (sales.CategorySales.GetValueOrDefault()))
```

Les opérateurs `?>` et `?<` sont des opérateurs autorisant la valeur null. Vous pouvez utiliser un ensemble complet des opérateurs de comparaison et d’égalité nullables. Pour plus d’informations, consultez [Linq.nullableoperators, Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d).
<br />

7. Utilisez le `sortBy` opérateur pour spécifier l’ordre de requête et utilisez `thenBy` pour spécifier un autre niveau de la commande. Notez également l’utilisation d’un tuple dans la partie select de la requête. Par conséquent, la requête a un tuple comme un type d’élément.
<br />

```fsharp
printfn "Freight for some orders: "

query { 
  for order in db.Orders do
  sortBy (order.OrderDate.Value)
  thenBy (order.OrderID)
  select (order.OrderDate, order.OrderID, order.Customer.CompanyName)
} |> Seq.iter (fun (orderDate, orderID, company) ->
                  printfn "OrderDate: %s" (orderDate.GetValueOrDefault().ToString())
                  printfn "OrderID: %d Company: %s\n" orderID company)
```

8. Ignore un nombre spécifié d’enregistrements à l’aide de l’opérateur skip et utilisez l’opérateur take pour spécifier un nombre d’enregistrements à retourner. De cette façon, vous pouvez implémenter la pagination sur le flux de données.
<br />

```fsharp
printfn "Get the first page of 2 employees."

query { 
  for employee in db.Employees do
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID)) 

printfn "Get the next 2 employees."

query { 
  for employee in db.Employees do
  skip 2
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

## <a name="verifying-the-odata-request"></a>Vérification de la requête OData
Chaque requête OData est convertie en un URI de demande OData spécifique. Vous pouvez vérifier que l’URI, peut-être pour le débogage à des fins, en ajoutant un gestionnaire d’événements pour le `SendingRequest` événement sur l’objet de contexte de données complète.


#### <a name="to-verify-the-odata-request"></a>Pour vérifier la requête OData

- Pour vérifier que l’URI de requête OData, utilisez le code suivant :
<br />

```fsharp
// The DataContext property returns the full data context.
db.DataContext.SendingRequest.Add (fun eventArgs -> printfn "Requesting %A" eventArgs.Request.RequestUri)
```

La sortie du code précédent est :
<br />`requesting http://services.odata.org/Northwind/Northwind.svc/Orders()?$orderby=ShippedDate&amp;$select=OrderID,ShippedDate`


## <a name="see-also"></a>Voir aussi
[Expressions de requête](../../language-reference/query-expressions.md)

[Considérations de LINQ (WCF Data Services)](https://msdn.microsoft.com/library/ee622463.aspx)

[Fournisseur de ODataService Type (F #)](https://msdn.microsoft.com/visualfsharpdocs/conceptual/odataservice-type-provider-%5bfsharp%5d)
