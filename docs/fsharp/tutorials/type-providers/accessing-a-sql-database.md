---
title: "Procédure pas à pas : accès à une base de données SQL Database à l'aide des fournisseurs de type (F#)"
description: "Découvrez comment utiliser le fournisseur de type SqlDataConnection (LINQ to SQL) dans F # 3.0 pour générer des types de base de données SQL lorsque vous avez une connexion de base de données active."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1c413eb0-16a5-4c1a-9a4e-ad6877e645d6
ms.openlocfilehash: c99afc1121b4f0d6d05ef82681a32437ede06e42
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers"></a>Procédure pas à pas : accès à une base de données SQL Database à l’aide des fournisseurs de type

> [!NOTE]
Ce guide a été écrit pour F # 3.0 et sera mise à jour.  Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).

> [!NOTE]
Les liens de référence d’API vous permettront de MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Cette procédure pas à pas explique comment utiliser le fournisseur de type SqlDataConnection (LINQ to SQL) est disponible dans F # 3.0 pour générer des types de données dans une base de données SQL lorsque vous avez une connexion active à une base de données. Si vous n’avez pas d’une connexion active à une base de données, mais vous avez LINQ à SQL schéma (fichier DBML), consultez [procédure pas à pas : génération de Types F # à partir d’un fichier DBML](generating-fsharp-types-from-dbml.md).

Cette procédure pas à pas décrit les tâches suivantes. Ces tâches doivent être effectuées dans cet ordre pour la procédure pas à pas réussisse :


- Préparation d’une base de données de test

- Création du projet

- Configuration d’un fournisseur de type

- Interrogation des données

- Utilisation des champs nullables

- Appel d'une procédure stockée

- Mise à jour de la base de données

- L’exécution de code Transact-SQL

- En utilisant le contexte de données complète

- Suppression des données

- Créer une base de données de test (si nécessaire)

## <a name="preparing-a-test-database"></a>Préparation d’une base de données de Test
Sur un serveur qui exécute SQL Server, créez une base de données à des fins de test. Vous pouvez utiliser la base de données créer un script en bas de cette page dans la section [création d’une base de données de test](#creating-a-test-database) pour ce faire.


#### <a name="to-prepare-a-test-database"></a>Pour préparer une base de données de test

Pour exécuter le Script de création MyDatabase, ouvrez le **vue** menu, puis choisissez **l’Explorateur d’objets SQL Server** ou choisissez Ctrl +\, touches Ctrl + S. Dans **l’Explorateur d’objets SQL Server** fenêtre, ouvrez le menu contextuel pour l’instance appropriée, choisissez **nouvelle requête**, copiez le script en bas de cette page, puis collez le script dans l’éditeur. Pour exécuter le script SQL, cliquez sur l’icône de barre d’outils d’un triangle ou appuyez sur les touches Ctrl + Q. Pour plus d’informations sur **l’Explorateur d’objets SQL Server**, consultez [développement de base de données connectée](https://msdn.microsoft.com/library/hh272679(VS.103).aspx).


## <a name="creating-the-project"></a>Création du projet
Ensuite, vous créez un projet d’application F #.


#### <a name="to-create-and-set-up-the-project"></a>Pour créer et configurer le projet

1. Créer un nouveau projet d’Application F #.

2. Ajoutez des références aux [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3), ainsi que `System.Data`, et `System.Data.Linq`.

3. Ouvrir les espaces de noms appropriées en ajoutant les lignes de code suivantes en haut de votre fichier de code F # Program.fs.

  ```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq
```

4. Comme avec la plupart des programmes F #, vous pouvez exécuter le code dans cette procédure pas à pas comme un programme compilé, ou vous pouvez l’exécuter interactivement sous forme de script. Si vous préférez utiliser des scripts, ouvrez le menu contextuel du nœud de projet, sélectionnez **ajouter un nouvel élément**, ajoutez un fichier de script F # et ajoutez le code dans chaque étape du script. Vous devrez ajouter les lignes suivantes en haut du fichier à charger les références d’assembly.

  ```fsharp
#r "System.Data.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

  Vous pouvez ensuite sélectionner chaque bloc de code que vous ajoutez et appuyez sur Alt + Entrée pour l’exécuter dans F # Interactive.

## <a name="setting-up-a-type-provider"></a>Configuration d’un fournisseur de type
Dans cette étape, vous créez un fournisseur de type de votre schéma de base de données.


#### <a name="to-set-up-the-type-provider-from-a-direct-database-connection"></a>Pour configurer le fournisseur de type à partir d’une connexion directe de la base de données

Il existe deux lignes essentielles de code que vous avez besoin pour créer les types que vous pouvez utiliser pour interroger une base de données SQL à l’aide du fournisseur de type. Tout d’abord, vous instanciez le fournisseur de type. Pour ce faire, créez à quoi ressemble une abréviation de type pour un `SqlDataConnection` avec un paramètre générique statique. `SqlDataConnection`est un fournisseur de type SQL et ne doit pas être confondu avec `SqlConnection` type qui est utilisé dans la programmation d’ADO.NET. Si vous avez une base de données que vous souhaitez vous connecter à et que vous avez une chaîne de connexion, utilisez le code suivant pour appeler le fournisseur de type. Remplacez par votre propre chaîne de connexion pour l’exemple de chaîne donnée. Par exemple, si votre serveur est MYSERVER et l’instance de base de données est l’INSTANCE, le nom de la base de données est MyDatabase, et vous souhaitez utiliser l’authentification Windows pour accéder à la base de données, puis la chaîne de connexion est en tant que donnée dans l’exemple de code suivant.

```fsharp
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">
let db = dbSchema.GetDataContext()

// Enable the logging of database activity to the console.
db.DataContext.Log <- System.Console.Out
```

Maintenant vous disposez d’un type, `dbSchema`, qui est un type de parent qui contient tous les types générés qui représentent des tables de base de données. Vous avez également un objet, `db`, qui a toutes les tables dans la base de données en tant que ses membres. Les noms de table sont les propriétés et le type de ces propriétés est généré par le compilateur F #. Les types eux-mêmes apparaissent en tant que types imbriqués sous `dbSchema.ServiceTypes`. Par conséquent, toutes les données récupérées pour les lignes de ces tables sont une instance du type approprié qui a été généré pour cette table. Le nom du type est `ServiceTypes.Table1`.

Pour vous familiariser avec l’interprétation des requêtes en requêtes SQL dans le langage F #, examinez la ligne qui définit le `Log` propriété sur le contexte de données.

Pour explorer davantage les types créés par le fournisseur de type, ajoutez le code suivant.

```fsharp
let table1 = db.Table1
```

Placez le curseur sur `table1` pour consulter son type. Son type est `System.Data.Linq.Table<dbSchema.ServiceTypes.Table1>` et l’argument générique implique que le type de chaque ligne est le type généré, `dbSchema.ServiceTypes.Table1`. Le compilateur crée un type similaire pour chaque table dans la base de données.

## <a name="querying-the-data"></a>Interrogation des données
Dans cette étape, vous écrivez une requête à l’aide d’expressions de requête F #.


#### <a name="to-query-the-data"></a>Pour interroger les données

1. Créer une requête pour cette table dans la base de données. Ajoutez le code suivant.

  ```fsharp
   let query1 =
     query {
       for row in db.Table1 do
       select row
     }
   query1 |> Seq.iter (fun row -> printfn "%s %d" row.Name row.TestData1)
```

  L’apparence du mot `query` indique qu’il s’agit d’une expression de requête, un type d’expression de calcul qui génère une collection de résultats similaire d’une requête de base de données classique. Si vous pointez sur la requête, vous verrez qu’il est une instance de [Linq.QueryBuilder, classe](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.querybuilder-class-%5bfsharp%5d), un type qui définit l’expression de calcul de requête. Si vous pointez sur `query1`, vous verrez qu’il est une instance de `System.Linq.IQueryable`. Comme son nom l’indique, `System.Linq.IQueryable` représente des données qui peuvent être interrogées, pas le résultat d’une requête. Une requête est soumise à l’évaluation différée, ce qui signifie que la base de données n’est interrogée lorsque la requête est évaluée. La dernière ligne transmet la requête via `Seq.iter`. Les requêtes sont énumérables et peuvent être itérés, comme des séquences. Pour plus d’informations, consultez [les Expressions de requête](../../language-reference/query-expressions.md).

2. Ajoutez maintenant un opérateur de requête à la requête. Il existe un nombre d’opérateurs de requête que vous pouvez utiliser pour construire des requêtes plus complexes. Cet exemple montre également que vous pouvez éliminer la variable de requête et utilisez un opérateur de pipeline à la place.

  ```fsharp
   query {
     for row in db.Table1 do
     where (row.TestData1 > 2)
     select row
   } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

3. Ajouter une requête plus complexe avec une jointure de deux tables.

  ```fsharp
   query {
     for row1 in db.Table1 do
     join row2 in db.Table2 on (row1.Id = row2.Id)
     select (row1, row2)
   } |> Seq.iteri (fun index (row1, row2) ->
                   if (index = 0) then printfn "Table1.Id TestData1 TestData2 Name Table2.Id TestData1 TestData2 Name"
                   printfn "%d %d %f %s %d %d %f %s" row1.Id row1.TestData1 row1.TestData2 row1.Name
                     row2.Id (row2.TestData1.GetValueOrDefault()) (row2.TestData2.GetValueOrDefault()) row2.Name)
```

4. Dans le code du monde réel, les paramètres de votre requête sont généralement les valeurs ou des variables, des constantes de compilation pas. Ajoutez le code suivant qui encapsule une requête dans une fonction qui accepte un paramètre, puis appelle cette fonction avec la valeur 10.

  ```fsharp
   let findData param =
     query {
       for row in db.Table1 do
       where (row.TestData1 = param)
       select row
     }

   findData 10 |> Seq.iter (fun row -> printfn "Found row: %d %d %f %s" row.Id row.TestData1 row.TestData2 row.Name)
```

## <a name="working-with-nullable-fields"></a>Utilisation des champs nullables
Dans les bases de données, les champs permettent souvent des valeurs null. Dans le système de type .NET, vous ne pouvez pas utiliser les types de données numériques ordinaire pour les données qui autorise des valeurs NULL, car ces types n’ont pas null comme une valeur possible. Par conséquent, ces valeurs sont représentées par des instances de `System.Nullable` type. Au lieu de l’accès à la valeur de ces champs directement avec le nom du champ, vous devez ajouter des étapes supplémentaires. Vous pouvez utiliser le `System.Nullable.Value` propriété pour accéder à la valeur sous-jacente d’un type nullable. Le `System.Nullable.Value` propriété lève une exception si l’objet est null au lieu d’avoir une valeur. Vous pouvez utiliser la `System.Nullable.HasValue` méthode booléenne pour déterminer si une valeur existe, ou utilisez `System.Nullable.GetValueOrDefault()` pour vous assurer que vous disposez d’une valeur réelle dans tous les cas. Si vous utilisez `System.Nullable.GetValueOrDefault()` et il existe une valeur null dans la base de données, puis elle est remplacée par une valeur comme une chaîne vide pour les types string, 0 pour les types intégraux ou 0,0 pour les variables les types de points.

Lorsque vous devez effectuer des tests d’égalité ou les comparaisons sur les valeurs NULL dans une `where` clause dans une requête, vous pouvez utiliser les opérateurs autorisant la valeur null trouvées dans le [Linq.nullableoperators, Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d). Ils sont comme les opérateurs de comparaison régulière `=`, `>`, `<=`, et ainsi de suite, sauf qu’un point d’interrogation apparaît à gauche ou à droite de l’opérateur dans lequel les valeurs nullables sont. Par exemple, l’opérateur `>?` est supérieur-que l’opérateur avec une valeur nullable à droite. Le fonctionnement de ces opérateurs est que si un côté de l’expression est null, l’expression prend la valeur `false`. Dans un `where` clause, cela signifie généralement que que les lignes qui contiennent des champs null sont pas sélectionnés et pas renvoyés dans les résultats de requête.


#### <a name="to-work-with-nullable-fields"></a>Pour travailler avec des champs nullables

Le code suivant illustre l’utilisation de valeurs null ; Supposons que **TestData1** est un champ d’entier qui autorise des valeurs NULL.

```fsharp
query {
  for row in db.Table2 do
  where (row.TestData1.HasValue && row.TestData1.Value > 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
  for row in db.Table2 do
  // Use a nullable operator ?>
  where (row.TestData1 ?> 2)
  select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="calling-a-stored-procedure"></a>Appel d'une procédure stockée
Toutes les procédures stockées sur la base de données peuvent être appelées à partir de F #. Vous devez définir le paramètre statique `StoredProcedures` à `true` dans l’instanciation de fournisseur de type. Le fournisseur de type `SqlDataConnection` contient plusieurs méthodes statiques que vous pouvez utiliser pour configurer les types qui sont générés. Pour une description complète, consultez [fournisseur de Type SqlDataConnection](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d). Une méthode sur le type de contexte de données est générée pour chaque procédure stockée.


#### <a name="to-call-a-stored-procedure"></a>Pour appeler une procédure stockée

Si les procédures stockées acceptant des paramètres qui acceptent des valeurs NULL, vous devez passer un `System.Nullable` valeur. La valeur de retour d’une méthode de procédure stockée qui retourne une valeur scalaire ou une table est `System.Data.Linq.ISingleResult`, qui contient des propriétés qui vous permettent d’accéder aux données retournées. L’argument de type pour `System.Data.Linq.ISingleResult` dépend de la procédure spécifique et est également un des types générés par le fournisseur de type. Pour une procédure stockée nommée `Procedure1`, le type est `Procedure1Result`. Le type `Procedure1Result` contient les noms des colonnes dans une table retournée ou, pour une procédure stockée qui retourne une valeur scalaire, il représente la valeur de retour.

Le code suivant suppose qu’il existe une procédure `Procedure1` sur la base de données qui accepte deux entiers nullables en tant que paramètres, exécute une requête qui retourne une colonne nommée `TestData1`et retourne un entier.

```fsharp
type schema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;", StoredProcedures = true>

let testdb = schema.GetDataContext()

let nullable value = new System.Nullable<_>(value)

let callProcedure1 a b =
  let results = testdb.Procedure1(nullable a, nullable b)
  for result in results do
    printfn "%d" (result.TestData1.GetValueOrDefault())
  results.ReturnValue :?> int

printfn "Return Value: %d" (callProcedure1 10 20)
```

## <a name="updating-the-database"></a>Mise à jour de la base de données
Le type DataContext de LINQ contient des méthodes qui rendent plus faciles à effectuer des mises à jour de la base de données traité de manière entièrement typée avec les types générés.


#### <a name="to-update-the-database"></a>Pour mettre à jour la base de données

1. Dans le code suivant, plusieurs lignes sont ajoutées à la base de données. Si vous ajoutez une ligne uniquement, vous pouvez utiliser `System.Data.Linq.Table.InsertOnSubmit()` pour spécifier la nouvelle ligne à ajouter. Si vous insérez plusieurs lignes, vous devez les placer dans une collection et l’appel `System.Data.Linq.Table.InsertAllOnSubmit(System.Collections.Generic.IEnumerable)`. Lorsque vous appelez une de ces méthodes, la base de données n’est pas modifiée immédiatement. Vous devez appeler `System.Data.Linq.DataContext.SubmitChanges` pour valider les modifications. Par défaut, tous les éléments que vous effectuez avant d’appeler `System.Data.Linq.DataContext.SubmitChanges` fait implicitement partie de la même transaction.

 ```fsharp
   let newRecord = new dbSchema.ServiceTypes.Table1(Id = 100,
                                                    TestData1 = 35, 
                                                    TestData2 = 2.0,
                                                    Name = "Testing123")

   let newValues =
     [ for i in [1 .. 10] ->
       new dbSchema.ServiceTypes.Table3(Id = 700 + i,
         Name = "Testing" + i.ToString(),
         Data = i) ]

   // Insert the new data into the database.
   db.Table1.InsertOnSubmit(newRecord)
   db.Table3.InsertAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully inserted new rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

2. Nettoyer maintenant les lignes en appelant une opération de suppression.

  ```fsharp
   // Now delete what was added.
   db.Table1.DeleteOnSubmit(newRecord)
   db.Table3.DeleteAllOnSubmit(newValues)

   try
     db.DataContext.SubmitChanges()
     printfn "Successfully deleted all pending rows."
   with
   | exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="executing-transact-sql-code"></a>L’exécution de code Transact-SQL
Vous pouvez également spécifier Transact-SQL directement à l’aide du `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` méthode sur la `DataContext` classe.


#### <a name="to-execute-custom-sql-commands"></a>Pour exécuter des commandes SQL personnalisées

Le code suivant montre comment envoyer des commandes SQL pour insérer un enregistrement dans une table et supprimer un enregistrement d’une table.

```fsharp
try
  db.DataContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'Testing', 55)") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message

try //AND Name = 'Testing' AND Data = 55
  db.DataContext.ExecuteCommand("DELETE FROM Table3 WHERE Id = 102 ") |> ignore
with
| exn -> printfn "Exception:\n%s" exn.Message
```

## <a name="using-the-full-data-context"></a>En utilisant le contexte de données complète
Dans les exemples précédents, le `GetDataContext` méthode a été utilisée pour obtenir ce que l'on appelle la *contexte de données simplifié* pour le schéma de base de données. Le contexte de données simplifié est plus facile à utiliser lorsque vous construisez des requêtes, car il ne sont pas autant de membres disponibles. Par conséquent, lorsque vous parcourez les propriétés dans IntelliSense, vous pouvez vous concentrer sur la structure de base de données, telles que les tables et les procédures stockées. Toutefois, il est limité par ce que vous pouvez faire avec le contexte de données simplifié. Un contexte de données complète qui offre la possibilité d’effectuer d’autres actions. est également disponible, il se trouve dans le `ServiceTypes` et porte le nom de la *DataContext* paramètre statique si vous avez indiqué qu’il. Si vous n’avez pas fourni à elle, le nom du type de contexte de données est généré pour vous par SqlMetal.exe basé sur l’autre entrée. Le contexte de données complète hérite `System.Data.Linq.DataContext` et expose les membres de sa classe de base, y compris les références aux types de données ADO.NET telles que la `Connection` objet, les méthodes telles que `System.Data.Linq.DataContext.ExecuteCommand(System.String,System.Object[])` et `System.Data.Linq.DataContext.ExecuteQuery(System.String,System.Object[])` que vous pouvez utiliser pour écrire des requêtes dans SQL, et également un moyen pour utiliser des transactions de manière explicite.


#### <a name="to-use-the-full-data-context"></a>Pour utiliser le contexte de données complète

Le code suivant montre comment obtenir un objet de contexte de données complète et l’utiliser pour exécuter des commandes directement sur la base de données. Dans ce cas, les deux commandes sont exécutées dans le cadre de la même transaction.

```fsharp
let dbConnection = testdb.Connection
let fullContext = new dbSchema.ServiceTypes.MyDatabase(dbConnection)

dbConnection.Open()

let transaction = dbConnection.BeginTransaction()
fullContext.Transaction <- transaction

try
  let result1 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (102, 'A', 55)")
  printfn "ExecuteCommand Result: %d" result1
  let result2 = fullContext.ExecuteCommand("INSERT INTO Table3 (Id, Name, Data) VALUES (103, 'B', -2)")
  printfn "ExecuteCommand Result: %d" result2
  if (result1 <> 1 || result2 <> 1) then
    transaction.Rollback()
    printfn "Rolled back creation of two new rows."
  else
    transaction.Commit()
  printfn "Successfully committed two new rows."
with
| exn ->
  transaction.Rollback()
  printfn "Rolled back creation of two new rows due to exception:\n%s" exn.Message

dbConnection.Close()
```

## <a name="deleting-data"></a>Suppression des données
Cette étape vous montre comment supprimer des lignes d’une table de données.


#### <a name="to-delete-rows-from-the-database"></a>Pour supprimer des lignes à partir de la base de données

À présent, ajouté nettoyer les lignes en écrivant une fonction qui supprime des lignes dans une table spécifiée, une instance de la `System.Data.Linq.Table` classe. Écrire une requête pour rechercher toutes les lignes que vous souhaitez supprimer, puis diriger les résultats de la requête dans le `deleteRows` (fonction). Ce code tire parti de la capacité à fournir une application partielle d’arguments de fonction.

```fsharp
let deleteRowsFrom (table:Table<_>) rows =
  table.DeleteAllOnSubmit(rows)

query {
  for rows in db.Table3 do
  where (rows.Id > 10)
  select rows
} |> deleteRowsFrom db.Table3

db.DataContext.SubmitChanges()
printfn "Successfully deleted rows with Id greater than 10 in Table3."
```

## <a name="creating-a-test-database"></a>Création d’une base de données de test
Cette section vous montre comment configurer la base de données de test à utiliser dans cette procédure pas à pas.

Notez que si vous modifiez la base de données d’une certaine façon, vous devrez redéfinir le fournisseur de type. Pour réinitialiser le fournisseur de type, régénérer ou nettoyer le projet qui contient le fournisseur de type.


#### <a name="to-create-the-test-database"></a>Pour créer la base de données de test

1. Dans **l’Explorateur de serveurs**, ouvrez le menu contextuel pour le **des connexions de données** nœud, puis choisissez **ajouter une connexion**. Le **ajouter une connexion** boîte de dialogue s’affiche.

2. Dans le **nom du serveur** zone, spécifiez le nom d’une instance de SQL Server que vous avez un accès administratif à ou si vous n’avez pas l’accès à un serveur, spécifiez (LocalDB \ V11.0). SQL Express LocalDB fournit un serveur de base de données léger pour le développement et les tests sur votre ordinateur. Un nœud est créé dans **l’Explorateur de serveurs** sous **des connexions de données**. Pour plus d’informations sur la base de données locale, consultez [procédure pas à pas : création d’un fichier de base de données Local dans Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).

3. Ouvrez le menu contextuel pour le nouveau nœud de connexion, puis sélectionnez **nouvelle requête**.

4. Copiez le script SQL suivant, collez-le dans l’éditeur de requête, puis choisissez le **Execute** bouton dans la barre d’outils ou appuyez sur les touches Ctrl + Maj + E.

```sql
SET ANSI_NULLS ON
GO
SET QUOTED_IDENTIFIER ON
GO

USE [master];
GO

IF EXISTS (SELECT * FROM sys.databases WHERE name = 'MyDatabase')
  DROP DATABASE MyDatabase;
GO

-- Create the MyDatabase database.
CREATE DATABASE MyDatabase;
GO

-- Specify a simple recovery model 
-- to keep the log growth to a minimum.
ALTER DATABASE MyDatabase 
SET RECOVERY SIMPLE;
GO

USE MyDatabase;
GO

-- Create the Table1 table.
CREATE TABLE [dbo].[Table1] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NOT NULL,
  [TestData2] FLOAT (53) NOT NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);

-- Create the Table2 table.
CREATE TABLE [dbo].[Table2] (
  [Id]        INT        NOT NULL,
  [TestData1] INT        NULL,
  [TestData2] FLOAT (53) NULL,
  [Name]      NTEXT      NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
);


-- Create the Table3 table.
CREATE TABLE [dbo].[Table3] (
  [Id]   INT           NOT NULL,
  [Name] NVARCHAR (50) NOT NULL,
  [Data] INT           NOT NULL,
  PRIMARY KEY CLUSTERED ([Id] ASC)
  );
GO

CREATE PROCEDURE [dbo].[Procedure1]
  @param1 int = 0,
  @param2 int
AS
SELECT TestData1 FROM Table1
RETURN 0
GO

USE MyDatabase

-- Insert data into the Table1 table.
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table1 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');

-- Insert data into the Table2 table.
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(1, 10, 5.5, 'Testing1');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(2, 20, -1.2, 'Testing2');
INSERT INTO Table2 (Id, TestData1, TestData2, Name)
  VALUES(3, NULL, NULL, 'Testing3');

-- Insert data into the Table3 table.
INSERT INTO Table3 (Id, Name, Data)
  VALUES (1, 'Testing1', 10);
INSERT INTO Table3 (Id, Name, Data)
  VALUES (2, 'Testing2', 100);
```


## <a name="see-also"></a>Voir aussi
[Fournisseurs de type](index.md)

[Fournisseur de Type de SqlDataConnection](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqldataconnection-type-provider-%5bfsharp%5d)

[Procédure pas à pas : Génération de Types F # à partir d’un fichier DBML](generating-fsharp-types-from-dbml.md)

[Expressions de requête](../../language-reference/query-expressions.md)

[LINQ to SQL](https://msdn.microsoft.com/library/bb386976)

[SqlMetal.exe &#40; Outil de génération de code &#41;](https://msdn.microsoft.com/library/bb386987)
