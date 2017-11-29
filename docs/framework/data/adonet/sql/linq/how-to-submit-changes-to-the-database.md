---
title: "Comment : soumettre des modifications à la base de données"
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
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 039eaac26833651fbd82dc1a69a31f394c1464c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-submit-changes-to-the-database"></a>Comment : soumettre des modifications à la base de données
Indépendamment du nombre de modifications apportées aux objets, celles-ci sont apportées uniquement aux réplicas en mémoire. Vous n'avez pas apporté de modifications aux données effectives dans la base de données. Vos modifications ne sont pas transmises au serveur tant que vous n'appelez pas explicitement <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext>.  
  
 Lorsque vous effectuez cet appel, le <xref:System.Data.Linq.DataContext> essaie de traduire vos modifications en commandes SQL équivalentes. Vous pouvez utiliser votre propre logique personnalisée pour substituer ces actions, mais l’ordre de soumission est géré par un service de la <xref:System.Data.Linq.DataContext> appelé le *processeur de modification*. La séquence d'événements se décompose comme suit :  
  
1.  Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examine l'ensemble d'objets connus pour déterminer si de nouvelles instances ont été attachées. Le cas échéant, ces nouvelles instances sont ajoutées au jeu d'objets suivis.  
  
2.  Tous les objets qui ont des modifications en attente sont organisés dans une séquence d'objets en fonction de leurs dépendances. Les objets dont les modifications dépendent d'autres objets sont classés d'après leurs dépendances.  
  
3.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] démarre une transaction pour encapsuler la série de commandes individuelles, juste avant que toutes les modifications réelles soient transmises.  
  
4.  Les modifications apportées aux objets sont traduites une par une en commandes SQL et sont envoyées au serveur.  
  
 À ce stade, toutes les erreurs détectées par la base de données interrompent le processus de soumission et une exception est levée. Toutes les modifications apportées à la base de données sont restaurées comme si aucune soumission ne s'était produite. Le <xref:System.Data.Linq.DataContext> a encore un enregistrement complet de toutes les modifications. Par conséquent, vous pouvez essayer de résoudre le problème et d'appeler encore <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, comme dans l'exemple de code qui suit.  
  
## <a name="example"></a>Exemple  
 Lorsque la transaction autour de la soumission a réussi, le <xref:System.Data.Linq.DataContext> accepte les modifications apportées aux objets en ignorant les informations de suivi des modifications.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 [Comment : détecter et résoudre des soumissions en conflit](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)  
 [Comment : gérer les conflits de modifications](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)  
 [Téléchargement d’exemples de base de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)  
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)
