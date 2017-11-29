---
title: "Comment : récupérer des informations en lecture seule"
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
ms.assetid: fb09e298-0b53-47e5-97fb-ab318bcd4fad
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9a9765d8d8330c7ad2a6e8cb25166427cdd9414a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-retrieve-information-as-read-only"></a>Comment : récupérer des informations en lecture seule
Lorsque vous ne projetez pas de modifier les données, vous pouvez augmenter les performances des requêtes en recherchant des résultats en lecture seule.  
  
 Implémentez le traitement en lecture seule en affectant la valeur <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> à `false`.  
  
> [!NOTE]
>  Lorsque la valeur <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> est affectée à `false`, <xref:System.Data.Linq.DataContext.DeferredLoadingEnabled%2A> a implicitement la valeur `false`.  
  
## <a name="example"></a>Exemple  
 Le code suivant récupère une collection en lecture seule de dates d’embauche d’employés.  
  
 [!code-csharp[DLinqQuerying#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQuerying/cs/Program.cs#2)]
 [!code-vb[DLinqQuerying#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQuerying/vb/Module1.vb#2)]  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Interrogation de la base de données](../../../../../../docs/framework/data/adonet/sql/linq/querying-the-database.md)  
 [Exécution différée / le chargement immédiat](../../../../../../docs/framework/data/adonet/sql/linq/deferred-versus-immediate-loading.md)
