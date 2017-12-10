---
title: "Procédure pas à pas : génération de types F# à partir d'un fichier de schéma EDMX (F#)"
description: "Découvrez comment créer des types F # pour les données représentées par le modèle EDM (Entity Data) dans F # 3.0, où le schéma est spécifié dans un fichier .edmx."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 81adb2eb-625f-4ad8-aeaa-8f672a6d79a2
ms.openlocfilehash: 1df0344e8dab2b40d82d1b9c61ccd2f026906243
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-an-edmx-schema-file"></a>Procédure pas à pas : génération de types F# à partir d'un fichier de schéma EDMX

> [!NOTE]
Ce guide a été écrit pour F # 3.0 et sera mise à jour.  Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).

> [!NOTE]
Les liens de référence d’API vous permettront de MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Cette procédure pas à pas pour F# 3.0 indique comment créer des types pour les données qui sont représentées par l'EDM (Entity Data Model), le schéma spécifié pour un fichier .edmx. Elle montre également comment utiliser le fournisseur de type EdmxFile. Avant de commencer, déterminez si un fournisseur de type SqlEntityConnection est une option de fournisseur de type plus appropriée. Le fournisseur de type SqlEntityConnection est plus performant pour les scénarios où vous pouvez vous connecter à une base de données active pendant la phase de développement de votre projet, et où vous ne vous occupez pas de spécifier la chaîne de connexion au moment de la compilation. Toutefois, ce fournisseur de type est également limité, car il ne dispose pas d'autant de fonctionnalités de base de données que le fournisseur de type EdmxFile. En outre, si vous n'avez pas une connexion de base de données active pour un projet de base de données qui utilise l'Entity Data Model, vous pouvez utiliser le fichier .edmx pour coder la base de données. Lorsque vous utilisez le fournisseur de type EdmxFile, le compilateur F# exécute EdmGen.exe pour générer les types qu'il fournit.

Les tâches suivantes, décrites dans cette procédure pas à pas, doivent être exécutées dans cet ordre pour la réussite de cette dernière :


- Création d'un fichier EDMX
<br />

- Création du projet
<br />

- Recherche ou création de la chaîne de connexion de l'Entity Data Model
<br />

- Configuration du fournisseur de type
<br />

- Interrogation des données
<br />

- Appel d'une procédure stockée
<br />


## <a name="prerequisites"></a>Conditions préalables

## <a name="creating-an-edmx-file"></a>Création d'un fichier EDMX
Si vous disposez déjà d'un fichier EDMX, vous pouvez ignorer cette étape.


#### <a name="to-create-an-edmx-file"></a>Pour créer un fichier EDMX

- Si vous n’avez pas déjà un fichier EDMX, vous pouvez suivre les instructions à la fin de cette procédure pas à pas à l’étape [configuration de l’Entity Data Model](generating-fsharp-types-from-edmx.md#configuring-the-entity-data-model).
<br />

## <a name="creating-the-project"></a>Création du projet
Dans cette étape, vous créez un projet et y ajoutez les références appropriées pour utiliser le fournisseur de type EDMX.


#### <a name="to-create-and-set-up-an-f-project"></a>Pour créer et configurer le projet F#

1. Fermez le projet précédent, créez un autre projet, et nommez-le SchoolEDM.
<br />

2. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **références**, puis choisissez **ajouter une référence**.
<br />

3. Dans le **assemblys** zone, choisissez le **Framework** nœud.
<br />

4. Dans la liste des assemblys disponibles, choisissez le **System.Data.Entity** et **System.Data.Linq** assemblys, puis choisissez le **ajouter** bouton pour ajouter des références à ces assemblys à votre projet.
<br />

5. Dans le **assemblys** zone, sélectionnez le **Extensions** nœud.
<br />

6. Dans la liste d’extensions disponibles, ajoutez une référence à l’assembly FSharp.Data.TypeProviders.
<br />

7. Ajoutez le code suivant pour ouvrir les espaces de noms appropriés.
<br />

```fsharp
open System.Data.Linq
open System.Data.Entity
open Microsoft.FSharp.Data.TypeProviders
```

## <a name="finding-or-creating-the-connection-string-for-the-entity-data-model"></a>Recherche ou création de la chaîne de connexion pour l'Entity Data Model
La chaîne de connexion pour l'Entity Data Model (chaîne de connexion EDMX) comprend non seulement la chaîne de connexion du fournisseur de base de données mais également des informations supplémentaires. Par exemple, pour une base de données SQL Server simple, la chaîne de connexion EDMX ressemble au code suivant.

```fsharp
let edmConnectionString = "metadata=res://*/;provider=System.Data.SqlClient;Provider Connection String='Server=SERVER\Instance;Initial Catalog=DatabaseName;Integrated Security=SSPI;'"
```

Pour plus d’informations sur les chaînes de connexion EDMX, consultez [les chaînes de connexion](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).


#### <a name="to-find-or-create-the-connection-string-for-the-entity-data-model"></a>Pour rechercher ou créer la chaîne de connexion pour l'Entity Data Model

1. Générer des chaînes de connexion EDMX manuellement peut s'avérer difficile ; vous pouvez gagner du temps en les générant par programmation. Si vous connaissez la chaîne de connexion EDMX, vous pouvez ignorer cette étape et utiliser simplement cette chaîne dans l'étape suivante. Sinon, utilisez le code suivant pour générer la chaîne de connexion EDMX à partir d'une chaîne de connexion d'une base de données fournie par vos soins.
<br />

```fsharp
open System
open System.Data
open System.Data.SqlClient
open System.Data.EntityClient
open System.Data.Metadata.Edm

let getEDMConnection(dbConnectionString) =
  let dbConnection = new SqlConnection(dbConnectionString)
  let resourceArray = [| "res://*/" |]
  let assemblyList = [| System.Reflection.Assembly.GetCallingAssembly() |]
  let metaData = MetadataWorkspace(resourceArray, assemblyList)
  new EntityConnection(metaData, dbConnection)
```

## <a name="configuring-the-type-provider"></a>Configuration du fournisseur de type
Dans cette étape, vous créez et configurez le fournisseur de type avec la chaîne de connexion EDMX, et vous générez des types pour le schéma défini dans le fichier .edmx.


#### <a name="to-configure-the-type-provider-and-generate-types"></a>Pour configurer le fournisseur de type et générer des types

1. Copiez le fichier .edmx créé au cours de la première étape de cette procédure dans le dossier du projet.
<br />

2. Ouvrez le menu contextuel du nœud de projet dans votre projet F #, choisissez **ajouter un élément existant**, puis choisissez le fichier .edmx pour l’ajouter à votre projet.
<br />

3. Entrez le code suivant pour activer le fournisseur de type de votre fichier .edmx. Remplacez *Server*\*Instance * avec le nom de votre serveur qui exécute SQL Server et le nom de votre instance et utiliser le nom de votre fichier .edmx à partir de la première étape dans cette procédure pas à pas.
<br />

```fsharp
type edmx = EdmxFile<"Model1.edmx", ResolutionFolder = @"<path-tofolder-that-containsyour.edmx-file>">

use edmConnection =
  getEDMConnection("Data Source=SERVER\instance;Initial Catalog=School;Integrated Security=true;")
use context = new edmx.SchoolModel.SchoolEntities(edmConnection)
```

## <a name="querying-the-data"></a>Interrogation des données
Dans cette étape, des expressions de requête F# sont utilisées pour interroger la base de données.


#### <a name="to-query-the-data"></a>Pour interroger les données

- Entrez le code suivant pour interroger les données dans un Entity Data Model.
<br />

```fsharp
query { 
  for course in context.Courses do
  select course 
} |> Seq.iter (fun course -> printfn "%s" course.Title)

query { 
  for person in context.Person do
  select person 
} |> Seq.iter (fun person -> printfn "%s %s" person.FirstName person.LastName)

// Add a where clause to filter results
query { 
  for course in context.Courses do
  where (course.DepartmentID = 1)
  select course
} |> Seq.iter (fun course -> printfn "%s" course.Title)

// Join two tables
query { 
  for course in context.Courses do
  join dept in context.Departments on (course.DepartmentID = dept.DepartmentID)
  select (course, dept.Name) 
} |> Seq.iter (fun (course, deptName) -> printfn "%s %s" course.Title deptName)
```

## <a name="calling-a-stored-procedure"></a>Appel d'une procédure stockée
Vous pouvez appeler des procédures stockées à l’aide du fournisseur de type EDMX. Dans la procédure suivante, la base de données School contient une procédure stockée, **UpdatePerson**, qui met à jour un enregistrement, l’aide de nouvelles valeurs pour les colonnes. Cette procédure stockée peut être utilisée, car elle est exposée en tant que méthode sur le type DataContext.


#### <a name="to-call-a-stored-procedure"></a>Pour appeler une procédure stockée

- Ajoutez le code suivant pour mettre à jour des enregistrements.
<br />

```fsharp
// Call a stored procedure.
let nullable value = new System.Nullable<_>(value)

// Assume now that you must correct someone's hire date.
// Throw an exception if more than one matching person is found.
let changeHireDate(lastName, firstName, hireDate) =

  query { 
    for person in context.People do
    where (person.LastName = lastName &&
           person.FirstName = firstName)
    exactlyOne 
  } |> (fun person ->
            context.UpdatePerson(nullable person.PersonID, person.LastName, person.FirstName, nullable hireDate, person.EnrollmentDate))

changeHireDate("Abercrombie", "Kim", DateTime.Parse("1/12/1998"))
|> printfn "Result: %d"
```

En cas de réussite, le résultat est 1. Notez que **exactlyOne** est utilisé dans l’expression de requête pour vous assurer qu’un seul résultat est retourné ; sinon, une exception est levée. En outre, pour utiliser plus facilement avec les valeurs NULL, vous pouvez utiliser la simple **nullable** fonction qui est définie dans ce code pour créer une valeur nullable à partir d’une valeur ordinaire.

<br />

## <a name="configuring-the-entity-data-model"></a>Configuration de l'Entity Data Model
Effectuez cette procédure uniquement si vous souhaitez savoir comment générer un Entity Data Model complet à partir d'une base de données et si vous ne disposez pas de base de données avec laquelle effectuer un test.


#### <a name="to-configure-the-entity-data-model"></a>Pour créer l'Entity Data Model

1. Dans la barre de menus, choisissez **SQL**, **éditeur Transact-SQL**, **nouvelle requête** pour créer une base de données. Si vous y êtes invité, spécifiez votre serveur et instance de base de données.
<br />

2. Copiez et collez le contenu du script de base de données qui crée la base de données de l’étudiant, comme décrit dans la [documentation d’Entity Framework](http://msdn.microsoft.com/data/JJ614587.aspx) dans le centre de développement de données.
<br />

3. Exécutez le script SQL en cliquant sur le bouton de barre d’outils avec le symbole de triangle ou en appuyant sur Ctrl + Q.
<br />

4. Dans **l’Explorateur de serveurs**, ouvrez le menu contextuel pour **des connexions de données**, choisissez **ajouter une connexion**, puis entrez le nom du serveur de base de données, le nom de l’instance et la base de données School.
<br />

5. Créer un projet d’Application de Console Visual Basic ou c#, ouvrez le menu contextuel, choisissez **ajouter un nouvel élément**, puis choisissez **ADO.NET Entity Data Model**.
<br />  L'Assistant Entity Data Model s'ouvre. À l'aide de cet assistant, vous pouvez choisir la façon dont vous souhaitez créer l'Entity Data Model.
<br />

6. Sous **choisir le contenu du modèle**, sélectionnez le **générer à partir de la base de données** case à cocher.
<br />

7. Sur la page suivante, choisissez la base de données School nouvellement créée comme connexion de données.
<br />  Cette connexion doit ressembler à  **&lt;nom_serveur&gt;.&lt; INSTANCENAME&gt;. School.dbo**.
<br />

8. Copiez votre chaîne de connexion d'entité dans le Presse-papiers, car elle sera importante ultérieurement.
<br />

9. Assurez-vous que la case à cocher pour enregistrer la chaîne de connexion d’entité à la **App.Config** fichier est sélectionnée et notez la valeur de chaîne dans la zone de texte, qui devrait vous aider à trouver la chaîne de connexion plus tard, si nécessaire.
<br />

10. Dans la page suivante, choisissez **Tables** et **des procédures stockées et fonctions**.
<br />  En choisissant ces nœuds de niveau supérieur, vous sélectionnez toutes les tables, les procédures stockées, et les fonctions. Vous pouvez également choisir ces éléments individuellement, si vous le souhaitez.
<br />

11. Vérifiez que les cases à cocher des autres paramètres sont sélectionnées.
<br />  La première **mettre au pluriel ou au singulier les noms d’objets générés** case à cocher indique s’il faut modifier des formes au pluriel pour correspondre aux conventions d’appellation des objets qui représentent des tables de base de données. Le **inclure les colonnes clés étrangères dans le modèle** case à cocher détermine s’il faut inclure des champs dont l’objectif est de joindre d’autres champs dans les types d’objets qui sont générés pour le schéma de base de données. La troisième case à cocher indique s'il faut inclure les procédures et fonctions stockées dans le modèle.
<br />

12. Sélectionnez le **Terminer** bouton pour générer un fichier .edmx qui contient un Entity Data Model basé sur la base de données School.
<br />  Un fichier, **Model1.edmx**, est ajouté à votre projet, et un schéma de base de données s’affiche.
<br />

13. Dans la barre de menus, choisissez **vue**, **autres fenêtres**, **Explorateur EDM** pour afficher tous les détails du modèle ou **entité détails de mappage EDM**  pour ouvrir une fenêtre qui montre comment le modèle objet généré se mappe sur les tables de base de données et des colonnes.
<br />


## <a name="next-steps"></a>Étapes suivantes
Examinez les autres requêtes en examinant les opérateurs de requête disponible comme indiqué dans [les Expressions de requête](../../language-reference/query-expressions.md).


## <a name="see-also"></a>Voir aussi
[Fournisseurs de type](index.md)

[Fournisseur de Type de EdmxFile](https://msdn.microsoft.com/visualfsharpdocs/conceptual/edmxfile-type-provider-%5bfsharp%5d)

[Procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de type et des entités](accessing-a-sql-database-entities.md)

[Entity Framework](http://msdn.microsoft.com/data/ef)

[vue d’ensemble du fichier .edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4)

[EDM Generator &#40; EdmGen.exe &#41;](https://msdn.microsoft.com/library/bb387165)

