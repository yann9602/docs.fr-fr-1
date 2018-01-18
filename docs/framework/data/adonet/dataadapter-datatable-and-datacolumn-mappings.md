---
title: Mappages de DataAdapter DataTable et DataColumn
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
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e104ba75026c2ff387eb7c74b11c505e34085f41
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>Mappages de DataAdapter DataTable et DataColumn
A **DataAdapter** contient une collection de zéro ou plusieurs <xref:System.Data.Common.DataTableMapping> des objets dans son **TableMappings** propriété. A **DataTableMapping** fournit un mappage principal entre les données retournées à partir d’une requête sur une source de données et un <xref:System.Data.DataTable>. Le **DataTableMapping** nom peut être passé à la place de la **DataTable** nom pour le **remplir** méthode de la **DataAdapter**. L’exemple suivant crée un **DataTableMapping** nommé **AuthorsMapping** pour le **auteurs** table.  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping** vous permet d’utiliser des noms de colonne dans un **DataTable** qui sont différentes de celles figurant dans la base de données. Le **DataAdapter** utilise le mappage pour faire correspondre les colonnes lorsque la table est mise à jour.  
  
 Si vous ne spécifiez pas un **TableName** ou un **DataTableMapping** nom lors de l’appel du **remplir** ou **mise à jour** méthode de la  **DataAdapter**, le **DataAdapter** recherche un **DataTableMapping** nommé « Table ». Si ce **DataTableMapping** n’existe pas, le **TableName** de la **DataTable** est « Table ». Vous pouvez spécifier une valeur par défaut **DataTableMapping** en créant un **DataTableMapping** avec le nom « Table ».  
  
 L’exemple de code suivant crée un **DataTableMapping** (à partir de la <xref:System.Data.Common> espace de noms) et le rend le mappage par défaut spécifié **DataAdapter** en le nommant « Table ». L’exemple mappe ensuite les colonnes de la première table dans le résultat de requête (la **clients** table de la **Northwind** base de données) à un ensemble de noms plus conviviaux dans la **Customers Northwind**  de table dans le <xref:System.Data.DataSet>. Pour les colonnes qui ne sont pas mappées, le nom de la colonne de la source de données est utilisé.  
  
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
  
 Dans les situations plus évoluées, vous pouvez décider que vous voulez que le même **DataAdapter** pour prendre en charge le chargement de différentes tables avec différents mappages. Pour ce faire, il vous suffit, ajoutez des **DataTableMapping** objets.  
  
 Lorsque le **remplir** une instance d’est passé à la méthode un **DataSet** et un **DataTableMapping** nom, si un mappage de ce nom existe, il est utilisé ; sinon, un  **DataTable** de ce nom est utilisé.  
  
 Les exemples suivants créent un **DataTableMapping** avec un nom de **clients** et un **DataTable** nom de **BizTalkSchema**. L’exemple mappe alors les lignes retournées par l’instruction SELECT à la **BizTalkSchema** **DataTable**.  
  
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
>  Si aucun nom de colonne source n'est fourni pour un mappage de colonne ou aucun nom de table source n'est fourni pour un mappage de table, les noms par défaut sont automatiquement générés. Si aucune colonne source n’est fourni pour un mappage de colonne, le mappage de colonnes reçoit un nom incrémentiel par défaut de **SourceColumn** *N,* compter **SourceColumn1**. Si aucun nom de table source n’est fournie pour un mappage de table, le mappage de table reçoit un nom incrémentiel par défaut de **SourceTable** *N*, en commençant par **SourceTable1**.  
  
> [!NOTE]
>  Nous vous recommandons d’éviter la convention d’affectation de noms de **SourceColumn** *N* pour un mappage de colonne, ou **SourceTable** *N* pour une table mappage, car le nom fourni peut entrer en conflit avec un nom de mappage de colonne par défaut existant dans le **ColumnMappingCollection** ou le nom de mappage de table dans le **DataTableMappingCollection** . Si le nom fourni existe déjà, une exception sera levée.  
  
## <a name="handling-multiple-result-sets"></a>Gestion de jeux de résultats multiples  
 Si votre **SelectCommand** retourne plusieurs tables, **remplir** génère automatiquement des noms de table avec des valeurs incrémentielles pour les tables dans le **DataSet**, en commençant par le spécifié le nom de la table et en continuant sur sous la forme **TableName** *N*, en commençant par **TableName1**. Vous pouvez utiliser des mappages de table pour mapper le nom de table généré automatiquement à un nom que vous souhaitez spécifier pour la table dans le **DataSet**. Par exemple, pour un **SelectCommand** qui retourne deux tables, **clients** et **commandes**, émettre l’appel suivant à **remplir**.  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 Deux tables sont créées dans le **DataSet**: **clients** et **Customers1**. Vous pouvez utiliser les mappages de table pour vous assurer que la deuxième table est nommée **commandes** au lieu de **Customers1**. Pour ce faire, mappez la table de source de **Customers1** à la **DataSet** table **commandes**, comme illustré dans l’exemple suivant.  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [DataAdapters et DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Extraction et modification de données dans ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
