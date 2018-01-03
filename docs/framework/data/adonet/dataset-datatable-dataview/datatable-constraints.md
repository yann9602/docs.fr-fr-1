---
title: Contraintes de DataTable
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
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 3767467024d6c0d0dfbf1be8829d77ba3f7fa439
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="datatable-constraints"></a>Contraintes de DataTable
Vous pouvez utiliser des contraintes pour appliquer des restrictions sur les données dans un objet <xref:System.Data.DataTable> afin de conserver l'intégrité des données. Une contrainte est une règle automatique, appliquée à une ou plusieurs colonnes en relation, qui détermine l'action à réaliser lorsque la valeur d'une ligne est modifiée. Les contraintes sont appliquées lors de la `System.Data.DataSet.EnforceConstraints` propriété de la <xref:System.Data.DataSet> est **true**. Pour obtenir un exemple de code montrant comment définir la propriété `EnforceConstraints`, consultez la rubrique de référence <xref:System.Data.DataSet.EnforceConstraints%2A>.  
  
 Il y a deux types de contraintes dans ADO.NET : la <xref:System.Data.ForeignKeyConstraint> et la <xref:System.Data.UniqueConstraint>. Par défaut, les deux contraintes sont automatiquement créées lorsque vous créez une relation entre deux ou plusieurs tables en ajoutant un <xref:System.Data.DataRelation> à la **DataSet**. Toutefois, vous pouvez désactiver ce comportement en spécifiant **createConstraints** = **false** lors de la création de la relation.  
  
## <a name="foreignkeyconstraint"></a>ForeignKeyConstraint  
 A **ForeignKeyConstraint** applique des règles sur la manière dont les mises à jour et suppressions dans les tables connexes sont propagées. Par exemple, si une valeur dans une ligne d’une table est mise à jour ou supprimée et cette valeur est également utilisée dans une ou plusieurs tables connexes, une **ForeignKeyConstraint** détermine ce qui se passe dans les tables associées.  
  
 Le <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> et <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> propriétés de la **ForeignKeyConstraint** définissent l’action à entreprendre lorsque l’utilisateur tente de supprimer ou mettre à jour une ligne dans une table associée. Le tableau suivant décrit les différents paramètres disponibles pour le **DeleteRule** et **UpdateRule** propriétés de la **ForeignKeyConstraint**.  
  
|Paramètre de règle|Description|  
|------------------|-----------------|  
|**Cascade**|Supprime ou met à jour les lignes connexes.|  
|**SetNull**|Définir les valeurs des lignes connexes **DBNull**.|  
|**SetDefault**|Définit les valeurs des lignes connexes sur la valeur par défaut.|  
|**Aucun**|N'effectue aucune action sur les lignes connexes. Il s'agit de la valeur par défaut.|  
  
 A **ForeignKeyConstraint** peuvent limiter, et propager les modifications apportées à des colonnes associées. En fonction des propriétés définies pour le **ForeignKeyConstraint** d’une colonne, si le **EnforceConstraints** propriété de la **DataSet** est **lavaleurtrue**, certaines opérations réalisées dans la ligne parente entraîne une exception. Par exemple, si le **DeleteRule** propriété de la **ForeignKeyConstraint** est **aucun**, une ligne parente ne peut pas être supprimée s’il a des lignes enfants.  
  
 Vous pouvez créer une contrainte de clé étrangère entre des colonnes uniques ou entre un tableau de colonnes à l’aide de la **ForeignKeyConstraint** constructeur. Passez résultant **ForeignKeyConstraint** de l’objet à la **ajouter** (méthode) de la table **contraintes** propriété, qui est un **ConstraintCollection**. Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la **ajouter** méthode d’un **ConstraintCollection** pour créer un **ForeignKeyConstraint**.  
  
 Lorsque vous créez un **ForeignKeyConstraint**, que vous pouvez passer le **DeleteRule** et **UpdateRule** valeurs au constructeur en tant qu’arguments, ou vous peuvent les définir en tant que propriétés comme dans le après exemple (où le **DeleteRule** a la valeur **aucun**).  
  
```vb  
Dim custOrderFK As ForeignKeyConstraint = New ForeignKeyConstraint("CustOrderFK", _  
  custDS.Tables("CustTable").Columns("CustomerID"), _  
  custDS.Tables("OrdersTable").Columns("CustomerID"))  
custOrderFK.DeleteRule = Rule.None    
' Cannot delete a customer value that has associated existing orders.  
custDS.Tables("OrdersTable").Constraints.Add(custOrderFK)  
```  
  
```csharp  
ForeignKeyConstraint custOrderFK = new ForeignKeyConstraint("CustOrderFK",  
  custDS.Tables["CustTable"].Columns["CustomerID"],   
  custDS.Tables["OrdersTable"].Columns["CustomerID"]);  
custOrderFK.DeleteRule = Rule.None;    
// Cannot delete a customer value that has associated existing orders.  
custDS.Tables["OrdersTable"].Constraints.Add(custOrderFK);  
```  
  
### <a name="acceptrejectrule"></a>AcceptRejectRule  
 Modifications apportées aux lignes peuvent être acceptées à l’aide de la **AcceptChanges** méthode ou annulées à l’aide du **RejectChanges** méthode de la **DataSet**, **DataTable**, ou **DataRow**. Lorsqu’un **DataSet** contient **ForeignKeyConstraints**, l’appel le **AcceptChanges** ou **RejectChanges** méthodes applique le  **AcceptRejectRule**. Le **AcceptRejectRule** propriété de la **ForeignKeyConstraint** détermine l’action à entreprendre sur les enfants des lignes lorsque **AcceptChanges** ou  **RejectChanges** est appelée sur la ligne parente.  
  
 Le tableau suivant répertorie les paramètres disponibles pour le **AcceptRejectRule**.  
  
|Paramètre de règle|Description|  
|------------------|-----------------|  
|**Cascade**|Accepte ou rejette les modifications des lignes enfants.|  
|**Aucun**|N'effectue aucune action sur les lignes enfants. Il s'agit de la valeur par défaut.|  
  
### <a name="example"></a>Exemple  
 L'exemple suivant crée un objet <xref:System.Data.ForeignKeyConstraint>, définit plusieurs de ses propriétés, notamment la <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, et l'ajoute à la <xref:System.Data.ConstraintCollection> d'un objet <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## <a name="uniqueconstraint"></a>UniqueConstraint  
 Le **UniqueConstraint** objet, qui peut être assigné à une seule colonne ou à un tableau de colonnes dans un **DataTable**, garantit que toutes les données dans l’ou les colonnes spécifiées sont uniques pour chaque ligne. Vous pouvez créer une contrainte unique pour une colonne ou un tableau de colonnes à l’aide de la **UniqueConstraint** constructeur. Passez résultant **UniqueConstraint** de l’objet à la **ajouter** (méthode) de la table **contraintes** propriété, qui est un **ConstraintCollection**. Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la **ajouter** méthode d’un **ConstraintCollection** pour créer un **UniqueConstraint**. Lorsque vous créez un **UniqueConstraint** pour une ou plusieurs colonnes, vous pouvez éventuellement spécifier si l’ou les colonnes sont une clé primaire.  
  
 Vous pouvez également créer une contrainte unique pour une colonne en définissant le **Unique** propriété de la colonne à **true**. Vous pouvez également définir le **Unique** propriété d’une seule colonne à **false** supprime toute contrainte qui peut-être exister. Lorsque vous définissez une ou plusieurs colonnes comme clé primaire d'une table, une contrainte unique est automatiquement créée pour les colonnes spécifiées. Si vous supprimez une colonne à partir de la **PrimaryKey** propriété d’un **DataTable**, le **UniqueConstraint** est supprimé.  
  
 L’exemple suivant crée un **UniqueConstraint** pour deux colonnes d’une **DataTable**.  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custUnique As UniqueConstraint = _  
    New UniqueConstraint(New DataColumn()   {custTable.Columns("CustomerID"), _  
    custTable.Columns("CompanyName")})  
custDS.Tables("Customers").Constraints.Add(custUnique)  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
UniqueConstraint custUnique = new UniqueConstraint(new DataColumn[]   
    {custTable.Columns["CustomerID"],   
    custTable.Columns["CompanyName"]});  
custDS.Tables["Customers"].Constraints.Add(custUnique);  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Data.DataRelation>  
 <xref:System.Data.DataTable>  
 <xref:System.Data.ForeignKeyConstraint>  
 <xref:System.Data.UniqueConstraint>  
 [Définition de schéma de DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)  
 [DataSets, DataTables et DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [Fournisseurs managés ADO.NET et centre de développement DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)
