---
title: "Ajout de contraintes existantes &#224; un DataSet | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Ajout de contraintes existantes &#224; un DataSet
La méthode **Fill** du **DataAdapter** remplit un objet <xref:System.Data.DataSet> uniquement avec les colonnes et les lignes de la table d'une source de données ; bien que les contraintes soient généralement définies par la source de données, la méthode **Fill** n'ajoute pas ces informations de schéma au **DataSet** par défaut.  Pour remplir un **DataSet** avec les informations de contrainte de clé primaire existantes provenant d'une source de données, vous pouvez appeler la méthode **FillSchema** du **DataAdapter** ou affecter **AddWithKey** à la propriété **MissingSchemaAction** du **DataAdapter** avant d'appeler **Fill**.  Cela garantira que les contraintes de clé primaire dans le **DataSet** reflètent celles de la source de données.  Les informations de contrainte de clé étrangère ne sont pas incluses et doivent être explicitement créées, comme indiqué dans [Contraintes DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 L'ajout d'informations de schéma à un **DataSet** avant de le remplir avec les données garantit que les contraintes de clé primaire sont incluses avec les objets <xref:System.Data.DataTable> du **DataSet**.  En conséquence, lorsque des appels supplémentaires sont établis pour remplir le **DataSet**, les informations de colonne de clé primaire sont utilisées pour faire correspondre les nouvelles lignes de la source de données avec les lignes actuelles de chaque **DataTable** ; les données actuelles des tables sont remplacées par celles de la source de données.  Sans les informations de schéma, les nouvelles lignes de la source de données sont ajoutées au **DataSet**, ce qui a pour résultat des lignes doubles.  
  
> [!NOTE]
>  Si une colonne d'une source de données est identifiée comme étant auto\-incrémentée, les méthodes **FillSchema** ou **Fill** avec un **MissingSchemaAction** de **AddWithKey** créent un **DataColumn** avec la valeur `true` affectée à une propriété **AutoIncrement**.  Il vous faudra cependant définir vous\-même les valeurs **AutoIncrementStep** et **AutoIncrementSeed**.  Pour plus d'informations sur les colonnes auto\-incrémentées, voir [Création de colonnes AutoIncrement](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 L'utilisation de **FillSchema** ou l'affectation de **AddWithKey** à **MissingSchemaAction** exigent un traitement supplémentaire au niveau de la source de données afin de déterminer les informations de colonne de clé primaire.  Ce traitement supplémentaire peut gêner la performance.  Si vous connaissez les informations de clé primaire au moment du design, il est recommandé de spécifier explicitement la ou les colonnes de clé primaire afin d'atteindre une performance optimale.  Pour plus d'informations sur la définition explicite des informations de clé primaire pour une table, voir [Définition des clés primaires](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 L'exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l'aide de **FillSchema**.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 L'exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l'aide de la propriété **MissingSchemaAction.AddWithKey** de la méthode **Fill**.  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## Gestion de jeux de résultats multiples  
 Si le **DataAdapter** trouve plusieurs jeux de résultats retournés à partir de **SelectCommand**, il créera plusieurs tables dans le **DataSet**.  Les tables recevront un nom incrémentiel par défaut de base zéro de **Table** *N*, en commençant par **Table** au lieu de « Table0 ».  Si un nom de table est passé comme argument à la méthode **FillSchema**, les tables recevront un nom incrémentiel de base zéro de **TableName** *N*, en commençant par **TableName** au lieu de « TableName0 ».  
  
> [!NOTE]
>  Si la méthode **FillSchema** de l'objet **OleDbDataAdapter** est appelée pour une commande qui retourne plusieurs jeux de résultats, seules les informations de schéma provenant du premier jeu de résultats sont retournées.  Lors du retour d'informations de schéma pour plusieurs jeux de résultats à l'aide de **OleDbDataAdapter**, il est recommandé de spécifier un **MissingSchemaAction** du **AddWithKey** et d'obtenir les informations de schéma lors de l'appel à la méthode **Fill**.  
  
## Voir aussi  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [Objets DataSet, DataTable et DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)