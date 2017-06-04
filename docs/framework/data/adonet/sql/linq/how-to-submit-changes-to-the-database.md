---
title: "Proc&#233;dure&#160;: soumettre des modifications &#224; la base de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c7cba174-9d40-491d-b32c-f2d73b7e9eab
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: soumettre des modifications &#224; la base de donn&#233;es
Indépendamment du nombre de modifications apportées aux objets, celles\-ci sont apportées uniquement aux réplicas en mémoire.  Vous n'avez pas apporté de modifications aux données effectives dans la base de données.  Vos modifications ne sont pas transmises au serveur tant que vous n'appelez pas explicitement <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sur le <xref:System.Data.Linq.DataContext>.  
  
 Lorsque vous effectuez cet appel, le <xref:System.Data.Linq.DataContext> essaie de traduire vos modifications en commandes SQL équivalentes.  Vous pouvez utiliser votre propre logique personnalisée pour substituer ces actions, mais l'ordre de soumission est géré par un service du <xref:System.Data.Linq.DataContext> connu sous le nom de *processeur de modification*.  La séquence d'événements se décompose comme suit :  
  
1.  Lorsque vous appelez <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] examine l'ensemble d'objets connus pour déterminer si de nouvelles instances ont été attachées.  Le cas échéant, ces nouvelles instances sont ajoutées au jeu d'objets suivis.  
  
2.  Tous les objets qui ont des modifications en attente sont organisés dans une séquence d'objets en fonction de leurs dépendances.  Les objets dont les modifications dépendent d'autres objets sont classés d'après leurs dépendances.  
  
3.  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] démarre une transaction pour encapsuler la série de commandes individuelles, juste avant que toutes les modifications réelles soient transmises.  
  
4.  Les modifications apportées aux objets sont traduites une par une en commandes SQL et sont envoyées au serveur.  
  
 À ce stade, toutes les erreurs détectées par la base de données interrompent le processus de soumission et une exception est levée.  Toutes les modifications apportées à la base de données sont restaurées comme si aucune soumission ne s'était produite.  Le <xref:System.Data.Linq.DataContext> a encore un enregistrement complet de toutes les modifications.  Par conséquent, vous pouvez essayer de résoudre le problème et d'appeler encore <xref:System.Data.Linq.DataContext.SubmitChanges%2A>, comme dans l'exemple de code qui suit.  
  
## Exemple  
 Lorsque la transaction autour de la soumission a réussi, le <xref:System.Data.Linq.DataContext> accepte les modifications apportées aux objets en ignorant les informations de suivi des modifications.  
  
 [!code-csharp[DLinqSubmittingChanges#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqSubmittingChanges/cs/Program.cs#1)]
 [!code-vb[DLinqSubmittingChanges#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqSubmittingChanges/vb/Module1.vb#1)]  
  
## Voir aussi  
 [Procédure : détecter et résoudre des soumissions en conflit](../../../../../../docs/framework/data/adonet/sql/linq/how-to-detect-and-resolve-conflicting-submissions.md)   
 [Procédure : gérer les conflits de changement](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)   
 [Téléchargement d'exemples de bases de données](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)   
 [Apport et soumission de modifications de données](../../../../../../docs/framework/data/adonet/sql/linq/making-and-submitting-data-changes.md)