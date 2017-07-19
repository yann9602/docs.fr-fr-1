---
title: "Proc&#233;dure&#160;: mettre &#224; jour des lignes dans la base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a2b5c90f-6cc3-4128-bfab-1db488d5af26
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: mettre &#224; jour des lignes dans la base de donn&#233;es
Vous pouvez mettre à jour des lignes dans une base de données en modifiant les valeurs de membre des objets associés à la collection [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Table%601> et en soumettant les modifications à la base de données. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit vos modifications en commandes SQL `UPDATE` appropriées.  
  
> [!NOTE]
>  Vous pouvez substituer des méthodes par défaut [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pour les opérations `Insert`, `Update` et `Delete` sur les bases de données.  Pour plus d'informations, consultez [Personnalisation des opérations d'insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).  
>   
>  Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent développer des procédures stockées dans le même but à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] .  
  
 Les étapes suivantes supposent qu'un <xref:System.Data.Linq.DataContext> valide vous connecte à la base de données Northwind.  Pour plus d'informations, consultez [Procédure : se connecter à une base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-connect-to-a-database.md).  
  
### Pour mettre à jour une ligne dans la base de données  
  
1.  Interrogez la base de données concernant la ligne à mettre à jour.  
  
2.  Apportez les modifications souhaitées aux valeurs de membre dans l'objet [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obtenu.  
  
3.  Soumettez les modifications à la base de données.  
  
## Exemple  
 L'exemple suivant interroge la base de données concernant la commande 11000, puis modifie les valeurs de `ShipName` et `ShipVia` dans l'objet `Order` obtenu.  Enfin, les modifications apportées à ces valeurs de membre sont soumises à la base de données comme modifications dans les colonnes `ShipName` et `ShipVia`.  
  
 [!code-csharp[System.Data.Linq.Table#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.table/cs/program.cs#2)]
 [!code-vb[System.Data.Linq.Table#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.table/vb/module1.vb#2)]  
  
## Voir aussi  
 [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)   
 [Procédure : assigner des procédures stockées pour effectuer des mises à jour, des insertions et des suppressions \(Concepteur O\/R\)](../Topic/How%20to:%20Assign%20stored%20procedures%20to%20perform%20updates,%20inserts,%20and%20deletes%20\(O-R%20Designer\).md)   
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)