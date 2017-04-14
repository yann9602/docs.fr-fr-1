---
title: "Contraintes DataTable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 27c9f2fd-f64d-4b4e-bbf6-1d24f47067cb
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Contraintes DataTable
Vous pouvez utiliser des contraintes pour appliquer des restrictions sur les données dans un objet <xref:System.Data.DataTable> afin de conserver l'intégrité des données.  Une contrainte est une règle automatique, appliquée à une ou plusieurs colonnes en relation, qui détermine l'action à réaliser lorsque la valeur d'une ligne est modifiée.  Les contraintes sont appliquées lorsque la propriété  `System.Data.DataSet.EnforceConstraints` de l'objet <xref:System.Data.DataSet> a la valeur **true**.  Pour obtenir un exemple de code montrant comment définir la propriété `EnforceConstraints`, consultez la rubrique de référence <xref:System.Data.DataSet.EnforceConstraints%2A>.  
  
 Il y a deux types de contraintes dans ADO.NET : la <xref:System.Data.ForeignKeyConstraint> et la <xref:System.Data.UniqueConstraint>.  Par défaut, ces deux contraintes sont automatiquement créées lorsque vous créez une relation entre plusieurs tables en ajoutant un objet <xref:System.Data.DataRelation> au **DataSet**.  Toutefois, vous pouvez désactiver ce comportement en spécifiant **createConstraints** \= **false** lors de la création de la relation.  
  
## ForeignKeyConstraint  
 **ForeignKeyConstraint** applique des règles sur la manière dont les mises à jour et les suppressions dans les tables connexes sont propagées.  Par exemple, si une valeur d'une ligne d'une table est mise à jour ou supprimée et si cette valeur est également utilisée dans une ou plusieurs autres tables connexes, un **ForeignKeyConstraint** détermine l'action à réaliser dans les tables connexes.  
  
 Les propriétés <xref:System.Data.ForeignKeyConstraint.DeleteRule%2A> et <xref:System.Data.ForeignKeyConstraint.UpdateRule%2A> de la **ForeignKeyConstraint** définissent l'action à entreprendre lorsque l'utilisateur tente de supprimer ou de mettre à jour une ligne dans une table connexe.  Le tableau suivant décrit les différents paramètres disponibles pour les propriétés **DeleteRule** et **UpdateRule** de **ForeignKeyConstraint**.  
  
|Paramètre de règle|Description|  
|------------------------|-----------------|  
|**Cascade**|Supprime ou met à jour les lignes connexes.|  
|**SetNull**|Définit les valeurs dans les lignes connexes sur **DBNull**.|  
|**SetDefault**|Définit les valeurs des lignes connexes sur la valeur par défaut.|  
|**None**|N'effectue aucune action sur les lignes connexes.  Il s'agit de la valeur par défaut.|  
  
 Un **ForeignKeyConstraint** peut limiter et propager les modifications dans les colonnes connexes.  En fonction des propriétés définies pour le **ForeignKeyConstraint** d'une colonne et si la valeur **true** est attribuée ou non à la propriété **EnforceConstraints** du **DataSet**, certaines opérations réalisées dans la ligne parente peuvent provoquer une exception.  Par exemple, si la propriété **DeleteRule** du **ForeignKeyConstraint** a la valeur **None**, il est impossible de supprimer une ligne parente possédant des lignes enfants.  
  
 Vous pouvez créer une contrainte de clé étrangère entre des colonnes uniques ou entre un tableau de colonnes en utilisant le constructeur **ForeignKeyConstraint**.  Passez l'objet **ForeignKeyConstraint** résultant à la méthode **Add** de la propriété **Constraints** de la table, qui est un **ConstraintCollection**.  Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la méthode **Add** d'un **ConstraintCollection** pour créer un **ForeignKeyConstraint**.  
  
 Lors de la création d'un **ForeignKeyConstraint**, vous pouvez passer les valeurs de **DeleteRule** et **UpdateRule** comme arguments au constructeur ou les définir comme propriétés, comme dans l'exemple suivant \(où **DeleteRule** a la valeur **None**\).  
  
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
  
### AcceptRejectRule  
 Les modifications de lignes peuvent être acceptées à l'aide de la méthode **AcceptChanges** ou annulées à l'aide de la méthode **RejectChanges** du **DataSet**, **DataTable** ou **DataRow**.  Lorsqu'un **DataSet** contient **ForeignKeyConstraints**, l'appel aux méthodes **AcceptChanges** ou **RejectChanges** applique la **AcceptRejectRule**.  La propriété **AcceptRejectRule** du **ForeignKeyConstraint** détermine l'action à réaliser dans les lignes enfants lors de l'appel à **AcceptChanges** ou **RejectChanges** dans la ligne parente.  
  
 Le tableau suivant répertorie les paramètres possibles pour **AcceptRejectRule**.  
  
|Paramètre de règle|Description|  
|------------------------|-----------------|  
|**Cascade**|Accepte ou rejette les modifications des lignes enfants.|  
|**None**|N'effectue aucune action sur les lignes enfants.  Il s'agit de la valeur par défaut.|  
  
### Exemple  
 L'exemple suivant crée un objet <xref:System.Data.ForeignKeyConstraint>, définit plusieurs de ses propriétés, notamment la <xref:System.Data.ForeignKeyConstraint.AcceptRejectRule%2A>, et l'ajoute à la <xref:System.Data.ConstraintCollection> d'un objet <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/CS/source.cs#1)]
 [!code-vb[DataWorks Data.AcceptRejectRule#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.AcceptRejectRule/VB/source.vb#1)]  
  
## UniqueConstraint  
 L'objet **UniqueConstraint**, qui peut être assigné soit à une seule colonne, soit à un tableau de colonnes d'un **DataTable**, garantit que toutes les données des colonnes spécifiées sont uniques dans une ligne.  Vous pouvez créer une contrainte unique pour une colonne ou un tableau de colonnes à l'aide du constructeur **UniqueConstraint**.  Passez l'objet **UniqueConstraint** résultant à la méthode **Add** de la propriété **Constraints** de la table, qui est un **ConstraintCollection**.  Vous pouvez également passer des arguments de constructeur à plusieurs surcharges de la méthode **Add** d'un **ConstraintCollection** pour créer un **UniqueConstraint**.  Lors de la création d'un **UniqueConstraint** pour une ou plusieurs colonnes, vous pouvez spécifier si les colonnes correspondent à des clés primaires.  
  
 Vous pouvez également créer une contrainte unique pour une colonne en attribuant la valeur **true** à la propriété **Unique** de la colonne.  L'affectation de la valeur **false** à la propriété **Unique** d'une colonne unique supprime toute contrainte existante.  Lorsque vous définissez une ou plusieurs colonnes comme clé primaire d'une table, une contrainte unique est automatiquement créée pour les colonnes spécifiées.  Si vous supprimez une colonne de la propriété **PrimaryKey** d'un **DataTable**, **UniqueConstraint** est supprimé.  
  
 L'exemple suivant créé un **UniqueConstraint** pour deux colonnes d'un **DataTable**.  
  
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
  
## Voir aussi  
 <xref:System.Data.DataRelation>   
 <xref:System.Data.DataTable>   
 <xref:System.Data.ForeignKeyConstraint>   
 <xref:System.Data.UniqueConstraint>   
 [Définition du schéma d'un DataTable](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-schema-definition.md)   
 [Objets DataSet, DataTable et DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [Fournisseurs managés ADO.NET et Centre de développement de DataSet](http://go.microsoft.com/fwlink/?LinkId=217917)