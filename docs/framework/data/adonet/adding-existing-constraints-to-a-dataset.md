---
title: "Ajout de contraintes existantes à un DataSet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e457113eff471c620ccdbf78337d2013d7a62bb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="adding-existing-constraints-to-a-dataset"></a>Ajout de contraintes existantes à un DataSet
Le **remplir** méthode de la **DataAdapter** remplit un <xref:System.Data.DataSet> uniquement avec les colonnes des tables et des lignes à partir d’une source de données ; bien que les contraintes soient généralement définies par la source de données, le **deremplissage** méthode n’ajoute pas ces informations de schéma pour le **DataSet** par défaut. Pour remplir un **DataSet** avec les informations de contrainte de clé primaire existante à partir d’une source de données, vous pouvez appeler la **FillSchema** méthode de la **DataAdapter**, ou définir le **MissingSchemaAction** propriété de la **DataAdapter** à **AddWithKey** avant d’appeler **remplir**. Cela permet de garantir cette clé primaire contraintes dans les **DataSet** reflètent celles de la source de données. Les informations de contrainte de clé étrangère n’est pas incluses et doivent être créées explicitement, comme indiqué dans [contraintes DataTable](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md).  
  
 Ajout d’informations de schéma à un **DataSet** avant de remplir avec les données garantit que les contraintes de clé primaire sont incluses avec le <xref:System.Data.DataTable> des objets dans le **DataSet**. Par conséquent, lorsqu’une appels pour remplir le **DataSet** sont effectuées, le serveur principal les informations de colonne clé sont utilisées pour faire correspondre les nouvelles lignes de la source de données avec les lignes actuelles de chaque **DataTable**et les données actuelles dans les tables sont remplacées par les données à partir de la source de données. Sans les informations de schéma, les nouvelles lignes à partir de la source de données sont ajoutées à la **DataSet**, se traduisant par des lignes en double.  
  
> [!NOTE]
>  Si une colonne dans une source de données est identifiée en tant que l’incrémentation automatique, le **FillSchema** (méthode), ou le **remplir** méthode avec un **MissingSchemaAction** de  **AddWithKey**, crée un **DataColumn** avec un **AutoIncrement** propriété `true`. Toutefois, vous devez définir le **AutoIncrementStep** et **AutoIncrementSeed** vous-même les valeurs. Pour plus d’informations sur les colonnes à incrémentation automatique, consultez [Creating AutoIncrement Columns](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
 À l’aide de **FillSchema** ou le **MissingSchemaAction** à **AddWithKey** nécessite un traitement supplémentaire à la source de données pour déterminer les informations de colonne de clé primaire. Ce traitement supplémentaire peut gêner la performance. Si vous connaissez les informations de clé primaire au moment du design, il est recommandé de spécifier explicitement la ou les colonnes de clé primaire afin d'atteindre une performance optimale. Pour plus d’informations sur la définition explicite des informations de clé primaire pour une table, consultez [définition des clés primaires](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l’aide de **FillSchema**.  
  
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
  
 L’exemple de code suivant montre comment ajouter des informations de schéma à un **DataSet** à l’aide de la **MissingSchemaAction.AddWithKey** propriété de la **remplir** (méthode).  
  
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
  
## <a name="handling-multiple-result-sets"></a>Gestion de jeux de résultats multiples  
 Si le **DataAdapter** rencontre plusieurs jeux de résultats retournés à partir de la **SelectCommand**, il créera plusieurs tables dans le **DataSet**. Les tables recevront un nom de base zéro incrémentiel par défaut de **Table** *N*, en commençant par **Table** au lieu de « Table0 ». Si un nom de table est passé comme argument à la **FillSchema** (méthode), les tables recevront un nom incrémentiel de base zéro de **TableName** *N*, en commençant par **TableName** au lieu de « TableName0 ».  
  
> [!NOTE]
>  Si le **FillSchema** méthode de la **OleDbDataAdapter** objet est appelé pour une commande qui retourne plusieurs jeux de résultats, les informations de schéma du premier jeu de résultats sont retournées. Lorsque retournant des informations de schéma pour plusieurs résultats définit à l’aide de la **OleDbDataAdapter**, il est recommandé de spécifier un **MissingSchemaAction** de **AddWithKey** et obtenir les informations de schéma lors de l’appel du **remplir** (méthode).  
  
## <a name="see-also"></a>Voir aussi  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [DataSets, DataTables et DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
