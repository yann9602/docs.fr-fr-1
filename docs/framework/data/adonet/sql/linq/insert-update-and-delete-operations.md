---
title: "Op&#233;rations d&#39;insertion, de mise &#224; jour et de suppression | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26a43a4f-83c9-4732-806d-bb23aad0ff6b
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# Op&#233;rations d&#39;insertion, de mise &#224; jour et de suppression
Pour effectuer des opérations d'`Insert`, de `Update` et de `Delete` dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ajoutez, modifiez et supprimez des objets dans votre modèle objet.  Par défaut, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] traduit vos actions en SQL et soumet les modifications à la base de données.  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] vous offre une souplesse maximale pour manipuler vos objets et rendre les modifications persistantes.  Dès que des objets d'entité sont disponibles \(objets récupérés via une requête ou reconstruits\), vous pouvez les modifier comme des objets standard de votre application.  Vous pouvez ainsi modifier leurs valeurs, les ajouter à vos collections et les supprimer de vos collections.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] suit vos modifications et est prêt à les renvoyer à la base de données lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>.  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ne prend pas en charge ni ne reconnaît les opérations de suppression en cascade.  Si vous souhaitez supprimer une ligne dans une table comportant des contraintes sur cette suppression, vous devez définir la règle `ON DELETE CASCADE` dans la contrainte de clé étrangère dans la base de données, ou utiliser votre propre code pour supprimer en premier les objets enfants qui empêchent la suppression de l'objet parent. Sinon, une exception est levée.  Pour plus d'informations, consultez [Procédure : supprimer des lignes de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/how-to-delete-rows-from-the-database.md).  
  
 Les extraits suivants utilisent les classes `Customer` et `Order` de l'exemple de base de données Northwind.  Les définitions de classe ne sont pas présentées pour des raisons de concision.  
  
 [!code-csharp[DLinqCRUDOps#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqCRUDOps/cs/Program.cs#1)]
 [!code-vb[DLinqCRUDOps#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqCRUDOps/vb/Module1.vb#1)]  
  
 Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] génère automatiquement et exécute les commandes SQL requises pour renvoyer vos modifications à la base de données.  
  
> [!NOTE]
>  Vous pouvez substituer ce comportement en utilisant votre propre logique personnalisée, en général au moyen d'une procédure stockée.  Pour plus d'informations, consultez [Responsabilités du développeur en matière de substitution du comportement par défaut](../../../../../../docs/framework/data/adonet/sql/linq/responsibilities-of-the-developer-in-overriding-default-behavior.md).  
>   
>  Les développeurs qui utilisent [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] peuvent développer des procédures stockées dans ce but à l'aide du [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].  
  
## Voir aussi  
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [Personnalisation des opérations d'insertion, de mise à jour et de suppression](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md)