---
title: "Proc&#233;dure&#160;: d&#233;tecter et r&#233;soudre des soumissions en conflit | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 91e27206-01fb-4c7a-8afc-1383a6ac5067
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: d&#233;tecter et r&#233;soudre des soumissions en conflit
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] fournit de nombreuses ressources pour détecter et résoudre des conflits issus de modifications effectuées par plusieurs utilisateurs dans la base de données.  Pour plus d'informations, consultez [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
## Exemple  
 L'exemple suivant affiche un bloc `try`\/`catch` qui intercepte une exception <xref:System.Data.Linq.ChangeConflictException>.  La fenêtre de console affiche des informations sur les entités et les membres de chaque conflit.  
  
> [!NOTE]
>  Vous devez inclure la directive `using System.Reflection` \(`Imports System.Reflection` dans Visual Basic\) pour prendre en charge la récupération d'informations.  Pour plus d'informations, consultez <xref:System.Reflection>.  
  
 [!code-csharp[DLinqSubmittingChanges#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#2)]
 [!code-vb[DLinqSubmittingChanges#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#2)]  
  
## Voir aussi  
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)   
 [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)