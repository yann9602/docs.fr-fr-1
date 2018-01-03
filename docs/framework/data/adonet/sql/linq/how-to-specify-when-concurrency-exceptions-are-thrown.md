---
title: "Comment : spécifier le moment où des exceptions d'accès concurrentiel sont levées"
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
ms.assetid: 344ae068-ff63-4a2e-8b00-af22e143675f
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: b30f529def27418a02383a5b8348fded4a67aadb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-when-concurrency-exceptions-are-thrown"></a>Comment : spécifier le moment où des exceptions d'accès concurrentiel sont levées
Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], une exception <xref:System.Data.Linq.ChangeConflictException> est levée lorsque des objets ne sont pas mis à jour en raison de conflits d'accès concurrentiel optimiste. Pour plus d’informations, consultez [d’accès concurrentiel optimiste : vue d’ensemble](../../../../../../docs/framework/data/adonet/sql/linq/optimistic-concurrency-overview.md).  
  
 Avant de soumettre vos modifications à la base de données, vous pouvez spécifier quand des exceptions d'accès concurrentiel doivent être levées :  
  
-   Lever l'exception au premier échec (<xref:System.Data.Linq.ConflictMode.FailOnFirstConflict>).  
  
-   Terminer toutes les tentatives de mise à jour, cumuler les échecs et signaler les échecs cumulés dans l'exception (<xref:System.Data.Linq.ConflictMode.ContinueOnConflict>).  
  
 Lorsqu'elle est levée, l'exception <xref:System.Data.Linq.ChangeConflictException> donne accès à une collection <xref:System.Data.Linq.ChangeConflictCollection>. Cette collection fournit des détails pour chaque conflit (mappé à une seule tentative de mise à jour non réussie), y compris l'accès à la collection <xref:System.Data.Linq.ObjectChangeConflict.MemberConflicts%2A>. Chaque conflit entre membres mappe à un seul membre dans la mise à jour au cours de laquelle le contrôle d'accès concurrentiel a échoué.  
  
## <a name="example"></a>Exemple  
 Le code suivant présente des exemples des deux valeurs.  
  
 [!code-csharp[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/cs/program.cs#1)]
 [!code-vb[System.Data.Linq.ConflictModeEnumeration#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/system.data.linq.conflictmodeenumeration/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
