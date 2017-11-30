---
title: "Procédure pas à pas : accès à une base de données SQL Database à l'aide des fournisseurs de type et des entités (F#)"
description: "Découvrez comment accéder aux données typées pour une base de données SQL en fonction de l’ADO.NET Entity Data Model dans F # 3.0."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dc82a932-5401-4d19-9fb3-92c50d8db514
ms.openlocfilehash: 770d405921758eeb7e8d7ea98b95c29c99631475
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-accessing-a-sql-database-by-using-type-providers-and-entities"></a>Procédure pas à pas : accès à une base de données SQL Database à l'aide des fournisseurs de type et des entités

> [!NOTE]
Ce guide a été écrit pour F # 3.0 et sera mise à jour.  Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).

> [!NOTE]
Les liens de référence d’API vous permettront de MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Cette procédure pas à pas pour F# 3.0 indique comment accéder à des données typées pour une base de données SQL sur ADO.NET Entity Data Model. Cette procédure pas à pas indique comment installer le fournisseur de type F# `SqlEntityConnection` à utiliser avec une base de données SQL, comment écrire des requêtes sur les données, comment appeler des procédures stockées sur la base de données, et comment utiliser certains types et méthodes ADO.NET Entity Framework pour mettre à jour la base de données.

Les tâches suivantes, décrites dans cette procédure pas à pas, doivent être exécutées dans cet ordre pour la réussite de cette dernière :


- Créer la base de données School
<br />

- Créer et configurer un projet F#
<br />

- Configurer le fournisseur de type et de se connecter à l’Entity Data Model
<br />

- La base de données
<br />

- Mise à jour de la base de données
<br />


## <a name="prerequisites"></a>Conditions préalables
Vous devez avoir accès à un serveur qui exécute SQL Server sur lequel vous pouvez créer une base de données pour effectuer ces étapes.

## <a name="create-the-school-database"></a>Créer la base de données School
Vous pouvez créer la base de données School sur un serveur qui exécute SQL Server et auquel vous avez un accès administratif, ou vous pouvez utiliser LocalDB.


#### <a name="to-create-the-school-database"></a>Pour créer la base de données School

1. Dans **l’Explorateur de serveurs**, ouvrez le menu contextuel pour le **des connexions de données** nœud, puis choisissez **ajouter une connexion**.
<br />  Le **ajouter une connexion** boîte de dialogue s’affiche.
<br />

2. Dans le **nom du serveur** zone, spécifiez le nom d’une instance de SQL Server à laquelle vous avez un accès administratif ou spécifiez (LocalDB \ V11.0) si vous n’avez pas accès à un serveur.
<br />  SQL Server Express LocalDB fournit un serveur de base de données léger pour le développement et les tests sur votre ordinateur. Pour plus d’informations sur la base de données locale, consultez [procédure pas à pas : création d’un fichier de base de données Local dans Visual Studio](https://msdn.microsoft.com/library/ms233763.aspx).
<br />  Un nœud est créé dans **l’Explorateur de serveurs** sous **des connexions de données**.
<br />

3. Ouvrez le menu contextuel pour le nouveau nœud de connexion, puis choisissez **nouvelle requête**.
<br />

4. Ouvrez [création de la base de données School](http://go.microsoft.com/fwlink/?LinkID=237278) dans le site Web de Microsoft, puis copiez et collez le script de base de données qui crée la base de données de l’étudiant dans la fenêtre d’éditeur.
<br />


## <a name="BKMK_CreateConfigFSProj"> </a>

## <a name="create-and-configure-an-f-project"></a>Créer et configurer un projet F#
Dans cette étape, vous créez un projet et le configurez pour utiliser un fournisseur de type.


#### <a name="to-create-and-configure-an-f-project"></a>Pour créer et configurer un projet F#

1. Fermez le projet précédent, créez un autre projet et nommez-le **SchoolEDM**.
<br />

2. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **références**, puis choisissez **ajouter une référence**.
<br />

3. Choisissez le **Framework** nœud, puis, dans le **Framework** , choisissez **System.Data**, **System.Data.Entity**et **System.Data.Linq**.
<br />

4. Choisissez le **Extensions** nœud, ajouter une référence à la [FSharp.Data.TypeProviders](https://msdn.microsoft.com/library/a858f859-047a-44ab-945b-8731d7a0e6e3) assembly, puis choisissez le **OK** bouton pour fermer la boîte de dialogue.
<br />

5. Ajoutez le code suivant pour définir un module interne et ouvrir les espaces de noms appropriés. Le fournisseur de type peut injecter des types uniquement dans un espace de noms privé ou interne.
<br />

```fsharp
module internal SchoolEDM

open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

6. Pour exécuter le code dans cette procédure pas à pas de façon interactive en tant que script au lieu d’en tant qu’un programme compilé, ouvrez le menu contextuel du nœud de projet, choisissez **ajouter un nouvel élément**, ajoutez un fichier de script F #, puis ajoutez le code dans chaque étape du script. Pour charger les références d'assembly, ajoutez les lignes suivantes.
<br />

```fsharp
#r "System.Data.Entity.dll"
#r "FSharp.Data.TypeProviders.dll"
#r "System.Data.Linq.dll"
```

7. Mettez en surbrillance chaque bloc de code au fur et à mesure que vous l'ajoutez, puis appuyez sur Alt+Entrée pour l'exécuter dans F# Interactive.
<br />

## <a name="configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Configurer le fournisseur de type et se connecter à l'Entity Data Model
Dans cette étape, vous configurez un fournisseur de type avec une connexion de données et obtenez un contexte de données qui vous permet d'utiliser des données.


#### <a name="to-configure-the-type-provider-and-connect-to-the-entity-data-model"></a>Pour configurer le fournisseur de type et se connecter à l'Entity Data Model

1. Entrez le code suivant pour configurer le fournisseur de type `SqlEntityConnection` qui génère des types F# basés sur l'Entity Data Model que vous avez créés précédemment. Au lieu de la chaîne de connexion complète EDMX, utilisez uniquement la chaîne de connexion SQL.
<br />

```fsharp
type private EntityConnection = SqlEntityConnection<ConnectionString="Server=SERVER\InstanceName;Initial Catalog=School;Integrated Security=SSPI;MultipleActiveResultSets=true",Pluralize = true>
```

  Cette action configure un fournisseur de type avec la connexion de base de données que vous avez créée précédemment. La propriété `MultipleActiveResultSets` est nécessaire lorsque vous utilisez ADO.NET Entity Framework, car cette propriété permet à plusieurs commandes de s'exécuter de façon asynchrone sur la base de données dans une connexion, ce qui peut se produire fréquemment dans le code ADO.NET Entity Framework. Pour plus d’informations, consultez [MARS (Multiple Active Result Sets)](/sql/relational-databases/native-client/features/using-multiple-active-result-sets-mars).
<br />

2. Obtenez le contexte de données, qui est un objet qui contient les tables de base de données en tant que propriétés et les procédures et fonctions stockées de base de données en tant que méthodes.
<br />

```fsharp
let context = EntityConnection.GetDataContext()
```

## <a name="querying-the-database"></a>Interroger la base de données
Dans cette étape, vous utilisez des expressions de requête F# pour exécuter diverses requêtes sur la base de données.


#### <a name="to-query-the-data"></a>Pour interroger les données

- Entrez le code suivant pour interroger les données de l'Entity Data Model. Notez l'effet de Pluralize = true, qui modifie la table de base de données Course par Courses et Person par People.
<br />

```fsharp
query { 
  for course in context.Courses do
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.People do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results.
query {
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables.
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="updating-the-database"></a>Mise à jour de la base de données
Pour mettre à jour la base de données, vous utilisez les classes et les méthodes Entity Framework. Vous pouvez utiliser deux types de contexte de données avec le fournisseur de type SQLEntityConnection. En premier lieu, `ServiceTypes.SimpleDataContextTypes.EntityContainer` est le contexte de données simplifié, qui inclut uniquement les propriétés fournies qui représentent des tables et des colonnes de base de données. Ensuite, le contexte de données complet est une instance de la classe Entity Framework `System.Data.Objects.ObjectContext`, qui contient la méthode `System.Data.Objects.ObjectContext.AddObject(System.String,System.Object)` pour ajouter des lignes à la base de données. L'Entity Framework reconnaît des tables et des relations entre elles, ce qui garantit la cohérence de base de données.


#### <a name="to-update-the-database"></a>Pour mettre à jour la base de données

1. Ajoutez le code suivant à votre programme. Dans cet exemple, vous ajoutez deux objets ayant une relation entre eux, et vous ajoutez un formateur et une attribution de lieu de travail. Le tableau `OfficeAssignments` contient la colonne `InstructorID`, qui référence la colonne `PersonID` dans le tableau `Person`.
<br />

```fsharp
// The full data context
let fullContext = context.DataContext

// A helper function.
let nullable value = new System.Nullable<_>(value)

let addInstructor(lastName, firstName, hireDate, office) =
  let hireDate = DateTime.Parse(hireDate)
  let newPerson = new EntityConnection.ServiceTypes.Person(LastName = lastName,
                                                           FirstName = firstName,
                                                           HireDate = nullable hireDate)
  fullContext.AddObject("People", newPerson)

  let newOffice = new EntityConnection.ServiceTypes.OfficeAssignment(Location = office)

  fullContext.AddObject("OfficeAssignments", newOffice)
  fullContext.CommandTimeout <- nullable 1000
  fullContext.SaveChanges() |> printfn "Saved changes: %d object(s) modified."

addInstructor("Parker", "Darren", "1/1/1998", "41/3720")
```

Rien n'est modifié dans la base de données jusqu'à ce que vous appeliez `System.Data.Objects.ObjectContext.SaveChanges`.
<br />

2. À présent, restaurez la base de données afin qu'elle retrouve son précédent état en supprimant les objets que vous avez ajoutés.
<br />

```fsharp
let deleteInstructor(lastName, firstName) =
  query {
    for person in context.People do
    where (person.FirstName = firstName &&
           person.LastName = lastName)
    select person
  } |> Seq.iter (fun person->
                    query {
                      for officeAssignment in context.OfficeAssignments do
                      where (officeAssignment.Person.PersonID = person.PersonID)
                      select officeAssignment
                    } |> Seq.iter (fun officeAssignment -> fullContext.DeleteObject(officeAssignment))

                    fullContext.DeleteObject(person))

  // The call to SaveChanges should be outside of any iteration on the queries.
  fullContext.SaveChanges() |> printfn "Saved changed: %d object(s) modified."

deleteInstructor("Parker", "Darren")
```

>[!WARNING] 
Lorsque vous utilisez une expression de requête, gardez en mémoire que la requête est sujette à l'évaluation tardive. Par conséquent, la base de données est encore ouverte pour lecture pendant les évaluations chaînées, comme dans les blocs d'expression lambda après chaque expression de requête. Toute opération de base de données qui utilise explicitement ou implicitement une transaction doit se produire après que les opérations de lecture soient terminées.


## <a name="next-steps"></a>Étapes suivantes
Explorer d’autres options de requête en examinant les opérateurs de requête disponibles dans [les Expressions de requête](../../language-reference/query-expressions.md)et aussi passer en revue les [ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572) à comprendre quelles sont les fonctionnalités à votre disposition quand vous utilisez ce fournisseur de type.


## <a name="see-also"></a>Voir aussi
[Fournisseurs de type](index.md)

[Fournisseur de Type de SqlEntityConnection](https://msdn.microsoft.com/visualfsharpdocs/conceptual/sqlentityconnection-type-provider-%5bfsharp%5d)

[Procédure pas à pas : Génération de Types F # à partir d’un fichier de schéma EDMX](generating-fsharp-types-from-edmx.md)

[ADO.NET Entity Framework](https://msdn.microsoft.com/library/bb399572)

[vue d’ensemble du fichier .edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[EDM Generator &#40; EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)
