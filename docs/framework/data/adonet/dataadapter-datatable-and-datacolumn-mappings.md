---
title: "Mappages de DataAdapter DataTable et DataColumn | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Mappages de DataAdapter DataTable et DataColumn
Un **DataAdapter** contient une collection de zéro ou plusieurs objets <xref:System.Data.Common.DataTableMapping> dans sa propriété **TableMappings**.  Un **DataTableMapping** fournit un mappage principal entre les données retournées d'une requête sur une source de données et un objet <xref:System.Data.DataTable>.  Le nom **DataTableMapping**, à la place du nom **DataTable**, peut être passé à la méthode **Fill** du **DataAdapter**.  L'exemple suivant crée un **DataTableMapping** nommé **AuthorsMapping** pour la table **Authors**.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTableMapping** vous permet d'utiliser dans un **DataTable** des noms de colonne différents de ceux de la base de données.  Le **DataAdapter** utilise le mappage pour faire correspondre les colonnes lorsque la table est mise à jour.  
  
 Si vous ne spécifiez pas de **TableName** ni de nom **DataTableMapping** lors de l'appel à la méthode **Fill** ou **Update** du **DataAdapter**, celui\-ci recherche un **DataTableMapping** nommé « Table ».  Si ce **DataTableMapping** n'existe pas, le **TableName** du **DataTable** est « Table ».  Vous pouvez spécifier un **DataTableMapping** par défaut en créant un **DataTableMapping** avec le nom « Table ».  
  
 L'exemple de code suivant crée un **DataTableMapping** \(de l'espace de noms <xref:System.Data.Common>\) et en fait le mappage par défaut pour le **DataAdapter** spécifié en le nommant « Table ».  L'exemple mappe ensuite les colonnes de la première table du résultat de requête \(table **Customers** de la base de données **Northwind**\) à un ensemble de noms plus conviviaux dans la table **Customers Northwind** de l'objet <xref:System.Data.DataSet>.  Pour les colonnes qui ne sont pas mappées, le nom de la colonne de la source de données est utilisé.  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
  
```  
  
```csharp  
DataTableMapping mapping =   
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 Dans les situations plus évoluées, vous pouvez éventuellement décider que vous voulez que le même **DataAdapter** prenne en charge le chargement de différentes tables avec différents mappages.  Pour cela, ajoutez simplement des objets **DataTableMapping** supplémentaires.  
  
 Lorsqu'une instance d'un **DataSet** et un nom **DataTableMapping** sont passés à la méthode **Fill**, si un mappage de ce nom existe, il est utilisé, sinon un **DataTable** de ce nom est utilisé.  
  
 L'exemple suivant crée un **DataTableMapping** avec un nom **Customers** et un nom de **DataTable** **BizTalkSchema**.  L'exemple mappe alors les lignes retournées par l'instruction SELECT au **DataTable** **BizTalkSchema**.  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
  
```  
  
```csharp  
ITableMapping mapping =   
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
>  Si aucun nom de colonne source n'est fourni pour un mappage de colonne ou aucun nom de table source n'est fourni pour un mappage de table, les noms par défaut sont automatiquement générés.  Si aucune colonne source n'est fournie pour un mappage de colonne, celui\-ci reçoit un nom incrémentiel par défaut de **SourceColumn** *N*, commençant par **SourceColumn1**.  Si aucun nom de table source n'est fourni pour un mappage de table, celui\-ci reçoit un nom incrémentiel par défaut de **SourceTable** *N*, commençant par **SourceTable1**.  
  
> [!NOTE]
>  Il est recommandé d'éviter la convention d'affectation de noms de **SourceColumn** *N* pour un mappage de colonnes ou **SourceTable** *N* pour un mappage de table car le nom que vous fournissez peut être en conflit avec un nom de mappage de colonnes par défaut existant dans le **ColumnMappingCollection** ou un nom de mappage de tables dans le **DataTableMappingCollection**.  Si le nom fourni existe déjà, une exception sera levée.  
  
## Gestion de jeux de résultats multiples  
 Si votre **SelectCommand** retourne plusieurs tables, **Fill** génère automatiquement les noms de table avec des valeurs incrémentielles pour les tables dans le **DataSet**, en commençant par le nom de table spécifié et en continuant sous la forme **TableName** *N*, en commençant par **TableName1**.  Vous pouvez utiliser les mappages de table pour mapper le nom de table généré automatiquement à un nom que vous souhaitez spécifier pour la table dans le **DataSet**.  Par exemple, pour un **SelectCommand** qui retourne deux tables, **Customers** et **Orders**, établissez l'appel suivant à **Fill**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Deux tables sont créées dans le **DataSet** : **Customers** et **Customers1**.  Vous pouvez utiliser les mappages de table pour vous assurer que la deuxième table est nommée **Orders** au lieu de **Customers1**.  Pour cela, mappez la table source de **Customers1** à la table **Orders** du **DataSet**, comme le montre l'exemple suivant.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## Voir aussi  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)