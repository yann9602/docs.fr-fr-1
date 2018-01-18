---
title: "Ajout de colonnes à un DataTable"
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
ms.assetid: e85c4a0e-4f3f-458c-b58b-0ddbc06bf974
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6340baa434467ec4ccde501b4bb11d55a72c069b
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="adding-columns-to-a-datatable"></a>Ajout de colonnes à un DataTable
A <xref:System.Data.DataTable> contient une collection de <xref:System.Data.DataColumn> objets référencés par le **colonnes** propriété de la table. Cette collection de colonnes, ainsi que toute contrainte, définit le schéma, ou structure, de la table.  
  
 Vous créez **DataColumn** objets au sein d’une table à l’aide de la **DataColumn** constructeur, ou en appelant le **ajouter** méthode de la **colonnes**propriété de la table, qui est un <xref:System.Data.DataColumnCollection>. Le **ajouter** méthode accepte facultatif **ColumnName**, **DataType**, et **Expression** arguments et crée un nouveau  **DataColumn** en tant que membre de la collection. Elle accepte également un existant **DataColumn** de l’objet et l’ajoute à la collection et retourne une référence à l’ajout **DataColumn** si nécessaire. Étant donné que **DataTable** objets ne sont pas spécifiques à n’importe quelle source de données, les types .NET Framework sont utilisées lorsque vous spécifiez le type de données d’une **DataColumn**.  
  
 L’exemple suivant ajoute quatre colonnes à un **DataTable**.  
  
```vb  
Dim workTable As DataTable = New DataTable("Customers")  
  
Dim workCol As DataColumn = workTable.Columns.Add( _  
    "CustID", Type.GetType("System.Int32"))  
workCol.AllowDBNull = false  
workCol.Unique = true  
  
workTable.Columns.Add("CustLName", Type.GetType("System.String"))  
workTable.Columns.Add("CustFName", Type.GetType("System.String"))  
workTable.Columns.Add("Purchases", Type.GetType("System.Double"))  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
  
DataColumn workCol = workTable.Columns.Add("CustID", typeof(Int32));  
workCol.AllowDBNull = false;  
workCol.Unique = true;  
  
workTable.Columns.Add("CustLName", typeof(String));  
workTable.Columns.Add("CustFName", typeof(String));  
workTable.Columns.Add("Purchases", typeof(Double));  
```  
  
 Dans l’exemple, notez que les propriétés de la **CustID** colonne sont définies pour ne pas autoriser **DBNull** valeurs et à limiter les valeurs soient uniques. Toutefois, si vous définissez la **CustID** colonne en tant que la colonne de clé primaire de la table, la **AllowDBNull** propriété sera automatiquement la valeur **false** et le **Unique** propriété sera automatiquement la valeur **true**. Pour plus d’informations, consultez [définition des clés primaires](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
> [!CAUTION]
>  Si un nom de colonne n’est pas fourni pour une colonne, la colonne reçoit un nom incrémentiel par défaut de la colonne*N,* commençant par « Column1 », lorsqu’il est ajouté à la **DataColumnCollection**. Nous vous recommandons d’éviter la convention d’affectation de noms de « colonne*N*» lorsque vous fournissez un nom de colonne, car le nom fourni peut entrer en conflit avec un nom de colonne par défaut existant dans le **DataColumnCollection**. Si le nom fourni existe déjà, une exception est levée.  
  
 Si vous utilisez <xref:System.Xml.Linq.XElement> en tant que <xref:System.Data.DataColumn.DataType%2A> d'un <xref:System.Data.DataColumn> dans <xref:System.Data.DataTable>, la sérialisation XML ne fonctionnera pas lors de la lecture dans les données. Par exemple, si vous écrivez un <xref:System.Xml.XmlDocument> à l'aide de la méthode `DataTable.WriteXml`, lors de la sérialisation vers XML, un nœud parent supplémentaire est ajouté dans le <xref:System.Xml.Linq.XElement>. Pour contourner ce problème, utilisez le type <xref:System.Data.SqlTypes.SqlXml> à la place de <xref:System.Xml.Linq.XElement>. `ReadXml` et `WriteXml` fonctionnent correctement avec <xref:System.Data.SqlTypes.SqlXml>.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataColumn>  
 <xref:System.Data.DataColumnCollection>  
 <xref:System.Data.DataTable>  
 [Définition de schéma de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
