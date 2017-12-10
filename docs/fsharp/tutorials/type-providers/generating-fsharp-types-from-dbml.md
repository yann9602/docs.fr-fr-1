---
title: "Procédure pas à pas : génération de types F# à partir d'un fichier DBML (F#)"
description: "Découvrez comment créer des types F # pour les données à partir d’une base de données F # 3.0 lorsque vous disposez des informations de schéma codées dans un fichier .dbml."
keywords: visual f#, f#, programmation fonctionnelle
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 6fbb6ccc-248f-4226-95e9-f6f99541dbe4
ms.openlocfilehash: a919c2acb2b5b8c2ce93124f2f541bd092d15c35
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-generating-f-types-from-a-dbml-file"></a>Procédure pas à pas : génération de types F# à partir d'un fichier DBML

> [!NOTE]
Ce guide a été écrit pour F # 3.0 et sera mise à jour.  Pour obtenir la liste la plus récente des fournisseurs de type multiplateformes, consultez [FSharp.Data](http://fsharp.github.io/FSharp.Data/).

> [!NOTE]
Les liens de référence d’API vous permettront de MSDN.  Les informations de référence sur les API docs.microsoft.com ne sont pas terminées.

Cette procédure pas à pas pour F # 3.0 décrit comment créer des types de données à partir d’une base de données lorsque vous disposez des informations de schéma codées dans un fichier .dbml. LINQ to SQL utilise ce format de fichier pour représenter le schéma de base de données. Vous pouvez générer un fichier LINQ to SQL schéma dans Visual Studio en utilisant le Concepteur Objet/Relationnel (O/R). Pour plus d’informations, consultez [vue d’ensemble du Concepteur O/R](https://msdn.microsoft.com/library/bb384511.aspx) et [la génération de Code dans LINQ to SQL](../../../../docs/framework/data/adonet/sql/linq/index.md).

Le fournisseur de type de langage de balisage de base de données (DBML) vous permet d’écrire du code qui utilise les types basés sur un schéma de base de données sans avoir à spécifier une chaîne de connexion statique au moment de la compilation. Qui peut être utile si vous devez autoriser la possibilité que l’application finale doit utiliser une autre base de données, informations d’identification différentes ou une chaîne de connexion autre que celui que vous utilisez pour développer l’application. Si vous avez une connexion directe de la base de données que vous pouvez utiliser au moment de la compilation, et c’est la même base de données et les informations d’identification que vous utiliserez par la suite dans votre application générée, vous pouvez également utiliser le fournisseur de type SQLDataConnection. Pour plus d’informations, consultez [procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de Type](accessing-a-sql-database.md).

Cette procédure pas à pas décrit les tâches suivantes. Ils doivent être effectuées dans cet ordre pour la procédure pas à pas réussisse :


- Création d’un fichier .dbml
<br />

- Création et configuration d’un projet F #
<br />

- Configuration du fournisseur de type et générer les types
<br />

- Interroger la base de données
<br />


## <a name="prerequisites"></a>Conditions préalables

## <a name="creating-a-dbml-file"></a>Création d’un fichier .dbml
Si vous n’avez pas de test sur une base de données, créer un en suivant les instructions au bas de [procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de Type](accessing-a-sql-database.md). Si vous suivez ces instructions, vous allez créer une base de données appelée MyDatabase contenant quelques tableaux simples et des procédures stockées sur votre serveur SQL Server.

Si vous avez déjà un fichier .dbml, vous pouvez passer à la section, **créer et configurer un F # projet**. Sinon, vous pouvez créer un fichier .dbml donné d’une base de données SQL existante et à l’aide de la ligne de commande outil SqlMetal.exe.


#### <a name="to-create-a-dbml-file-by-using-sqlmetalexe"></a>Pour créer un fichier .dbml à l’aide de SqlMetal.exe

1. Ouvrir un **invite de commandes développeur**.
<br />

2. Assurez-vous d’avoir accès à SqlMetal.exe en entrant `SqlMetal.exe /?` à l’invite de commandes. SqlMetal.exe est généralement installé sous le **Microsoft SDKs** dossier **Program Files** ou **Program Files (x86)**.
<br />

3. Exécutez SqlMetal.exe avec les options de ligne de commande suivantes. Remplacez par le chemin d’accès approprié à la place de `c:\destpath` pour créer le fichier .dbml et insérer les valeurs appropriées pour le serveur de base de données, instance nom et le nom de la base de données.
<br />

```
  SqlMetal.exe /sprocs /dbml:C:\destpath\MyDatabase.dbml /server:SERVER\INSTANCE /database:MyDatabase
```

>[!NOTE]
Si SqlMetal.exe a des difficultés pour créer le fichier en raison de problèmes d’autorisations, modifiez le répertoire actif dans un dossier que vous avez accès en écriture au.


4. Vous pouvez également consulter les autres options de ligne de commande disponibles. Par exemple, il existe des options que vous pouvez utiliser si vous souhaitez que les vues et fonctions SQL incluses dans les types générés. Pour plus d’informations, consultez [SqlMetal.exe &#40; Outil de génération de code &#41; ](https://msdn.microsoft.com/library/bb386987).
<br />


## <a name="creating-and-setting-up-an-f-project"></a>Création et configuration d’un projet F #
Dans cette étape, vous créez un projet et ajoutez les références appropriées pour utiliser le fournisseur de type DBML.


#### <a name="to-create-and-set-up-an-f-project"></a>Pour créer et configurer le projet F#

1. Ajouter un nouveau projet d’Application Console F # à votre solution.
<br />

2. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **références**, puis choisissez **ajouter une référence**.
<br />

3. Dans le **assemblys** zone, choisissez le **Framework** nœud, puis, dans la liste des assemblys disponibles, choisissez le **System.Data** et **System.Data.Linq**  assemblys.
<br />

4. Dans le **assemblys** zone, choisissez **Extensions**, puis, dans la liste des assemblys disponibles, choisissez **FSharp.Data.TypeProviders**.
<br />

5. Choisissez le **OK** pour ajouter des références aux assemblys suivants à votre projet.
<br />

6. (Facultatif). Copiez le fichier .dbml que vous avez créé à l’étape précédente et collez le fichier dans le dossier principal de votre projet. Ce dossier contient le fichier de projet (.fsproj) et les fichiers de code. Dans la barre de menus, choisissez **projet**, **ajouter un élément existant**, puis spécifiez le fichier .dbml pour l’ajouter à votre projet. Si vous effectuez ces étapes, vous pouvez omettre le paramètre statique ResolutionFolder dans l’étape suivante.
<br />

## <a name="configuring-the-type-provider"></a>Configuration du fournisseur de type
Dans cette section, vous créez un fournisseur de type et générez des types à partir du schéma qui est décrite dans le fichier .dbml.


#### <a name="to-configure-the-type-provider-and-generate-the-types"></a>Pour configurer le fournisseur de type et générer les types

- Ajoutez le code qui ouvre le **TypeProviders** espace de noms et instancie le fournisseur de type pour le fichier .dbml que vous souhaitez utiliser. Si vous avez ajouté le fichier .dbml à votre projet, vous pouvez omettre le paramètre statique ResolutionFolder.
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ResolutionFolder = @"<path-to-folder-that-contains-.dbml-file>">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let dataContext = new dbml.Mydatabase(connectionString)
```

Le type DataContext fournit l’accès à tous les types générés et hérite de `System.Data.Linq.DataContext`. Le fournisseur de type DbmlFile a plusieurs paramètres statiques que vous pouvez définir. Par exemple, vous pouvez utiliser un autre nom pour le type DataContext en spécifiant `DataContext=MyDataContext`. Dans ce cas, votre code ressemble à l’exemple suivant :
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type dbml = DbmlFile<"MyDatabase.dbml", ContextTypeName = "MyDataContext">

// This connection string can be specified at run time.
let connectionString = "Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;"
let db = new dbml.MyDataContext(connectionString)
```

## <a name="querying-the-database"></a>Interroger la base de données
Dans cette section, vous utilisez des expressions de requête) (F # pour interroger la base de données.


#### <a name="to-query-the-data"></a>Pour interroger les données

- Ajoutez le code pour interroger la base de données.
<br />

```fsharp
  query {
    for row in db.Table1 do
    where (row.TestData1 > 2)
    select row
  } |> Seq.iter (fun row -> printfn "%d %s" row.TestData1 row.Name)
```

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez passer à utiliser d’autres expressions de requête, ou obtenir une connexion de base de données à partir du contexte de données et effectuer des opérations de données ADO.NET normales. Pour obtenir des instructions supplémentaires, consultez les sections après « Données de la requête » dans [procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de Type](accessing-a-sql-database.md).


## <a name="see-also"></a>Voir aussi
[Fournisseur de Type de DbmlFile](https://msdn.microsoft.com/visualfsharpdocs/conceptual/dbmlfile-type-provider-%5bfsharp%5d)

[Fournisseurs de type](index.md)

[Procédure pas à pas : accès à une base de données SQL à l’aide des fournisseurs de type](accessing-a-sql-database.md)

[SqlMetal.exe &#40; Outil de génération de code &#41;](https://msdn.microsoft.com/library/bb386987)

[Expressions de requête](../../language-reference/query-expressions.md)
