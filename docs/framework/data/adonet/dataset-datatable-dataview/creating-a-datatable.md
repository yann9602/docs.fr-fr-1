---
title: "Création d'un DataTable"
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
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 68f8272aa0f525c04120f129057e6151e42ffee1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="creating-a-datatable"></a>Création d'un DataTable
Un objet <xref:System.Data.DataTable>, qui représente une table de données relationnelles en mémoire, peut être créé et utilisé de façon indépendante. Il peut également être utilisé par d'autres objets .NET Framework, la plupart du temps comme membre d'un objet <xref:System.Data.DataSet>.  
  
 Vous pouvez créer un **DataTable** objet en respectant **DataTable** constructeur. Vous pouvez l’ajouter à la **DataSet** à l’aide de la **ajouter** méthode à ajouter à la **DataTable** l’objet **Tables** collection.  
  
 Vous pouvez également créer **DataTable** objets au sein d’un **DataSet** à l’aide de la **remplir** ou **FillSchema** méthodes de la  **DataAdapter** objet, ou à partir d’un prédéfini ou déduit XML schema à l’aide de la **ReadXml**, **ReadXmlSchema**, ou **InferXmlSchema** méthodes de la **DataSet**. Notez que, après avoir ajouté un **DataTable** en tant que membre de la **Tables** collection d’un **DataSet**, vous ne pouvez l’ajouter à la collection de tables de toutes les autres **DataSet**.  
  
 Lorsque vous créez un **DataTable**, il ne possède pas de schéma (autrement dit, une structure). Pour définir le schéma de la table, vous devez créer et ajouter <xref:System.Data.DataColumn> des objets sur le **colonnes** collection de la table. Vous pouvez également définir une colonne de clé primaire pour la table et créer et ajouter **contrainte** des objets sur le **contraintes** collection de la table. Après avoir défini le schéma pour un **DataTable**, vous pouvez ajouter des lignes de données à la table en ajoutant **DataRow** des objets sur le **lignes** collection de la table.  
  
 Vous n’êtes pas obligé de fournir une valeur pour le <xref:System.Data.DataTable.TableName%2A> propriété lorsque vous créez un **DataTable**; vous pouvez spécifier la propriété à un autre moment, ou vous pouvez la laisser vide. Toutefois, lorsque vous ajoutez une table sans un **TableName** valeur un **DataSet**, la table a un nom incrémentiel par défaut de la Table*N*, en commençant par « Table » pour Table0.  
  
> [!NOTE]
>  Nous vous recommandons d’éviter le « Table*N*« convention d’affectation de noms lorsque vous fournissez un **TableName** valeur, car le nom fourni peut entrer en conflit avec un nom de table par défaut existant dans le **jeu de données** . Si le nom fourni existe déjà, une exception est levée.  
  
 L’exemple suivant crée une instance d’un **DataTable** de l’objet et lui attribue le nom « Customers ».  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 L’exemple suivant crée une instance d’un **DataTable** en l’ajoutant à la **Tables** collection d’un **DataSet**.  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataTable>  
 <xref:System.Data.DataTableCollection>  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Remplissage d’un DataSet à partir d’un DataAdapter](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 [Chargement d’un DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [Chargement des informations de schéma de DataSet à partir de XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
