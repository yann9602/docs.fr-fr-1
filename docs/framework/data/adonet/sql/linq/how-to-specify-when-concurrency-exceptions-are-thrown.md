---
title: "Proc&#233;dure&#160;: sp&#233;cifier le moment o&#249; des exceptions d&#39;acc&#232;s concurrentiel sont lev&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: sp&#233;cifier le moment o&#249; des exceptions d&#39;acc&#232;s concurrentiel sont lev&#233;es
Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque des objets ne sont pas mis à jour en raison de conflits d'accès concurrentiel optimiste.  Pour plus d'informations, consultez [Accès concurrentiel optimiste : vue d'ensemble](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Avant de soumettre vos modifications à la base de données, vous pouvez spécifier quand des exceptions d'accès concurrentiel doivent être levées :  
  
-   Lever l'exception au premier échec \(<xref:System.Data.Linq.ConflictMode>\).  
  
-   Terminer toutes les tentatives de mise à jour, cumuler les échecs et signaler les échecs cumulés dans l'exception \(<xref:System.Data.Linq.ConflictMode>\).  
  
 Lorsqu'elle est levée, l'exception <xref:System.Data.Linq.ChangeConflictException> donne accès à une collection <xref:System.Data.Linq.ChangeConflictCollection>.  Cette collection fournit des détails pour chaque conflit \(mappé à une seule tentative de mise à jour non réussie\), y compris l'accès à la collection <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A>.  Chaque conflit entre membres mappe à un seul membre dans la mise à jour au cours de laquelle le contrôle d'accès concurrentiel a échoué.  
  
## Exemple  
 Le code suivant présente des exemples des deux valeurs.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## Voir aussi  
 [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)   
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)