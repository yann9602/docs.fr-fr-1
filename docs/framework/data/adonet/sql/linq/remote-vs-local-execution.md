---
title: "Comparaison entre une ex&#233;cution locale et une ex&#233;cution distante | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ee50e943-9349-4c84-ab1c-c35d3ada1a9c
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Comparaison entre une ex&#233;cution locale et une ex&#233;cution distante
Vous pouvez décider d'exécuter vos requêtes à distance \(autrement dit, le moteur de base de données exécute la requête sur la base de données\) ou localement \([!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] exécute la requête sur un cache local\).  
  
## Communication à distance  
 Prenons la requête suivante :  
  
 [!code-csharp[DLinqQueryConcepts#7](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#7)]
 [!code-vb[DLinqQueryConcepts#7](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#7)]  
  
 Si votre base de données contient des milliers de lignes de commandes, vous ne souhaitez pas toutes les récupérer pour traiter un petit sous\-ensemble.  Dans [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], la classe <xref:System.Data.Linq.EntitySet%601> implémente l'interface <xref:System.Linq.IQueryable>.  Cette approche permet de s'assurer que de telles requêtes peuvent être exécutées à distance.  Deux avantages majeurs découlent de cette technique :  
  
-   Les données inutiles ne sont pas récupérées.  
  
-   Une requête exécutée par le moteur de base de données est souvent plus efficace en raison des index de la base de données.  
  
## et exécution locale  
 Dans d'autres situations, vous pouvez souhaiter disposer du jeu complet d'entités connexes dans le cache local.  Pour cela, <xref:System.Data.Linq.EntitySet%601> fournit la méthode <xref:System.Data.Linq.EntitySet%601.Load%2A> pour charger explicitement tous les membres de <xref:System.Data.Linq.EntitySet%601>.  
  
 Si un <xref:System.Data.Linq.EntitySet%601> est déjà chargé, les requêtes suivantes sont exécutées localement.  Cette approche est utile pour les raisons suivantes :  
  
-   Si le jeu complet doit être utilisé localement ou plusieurs fois, vous pouvez éviter des requêtes distantes et des latences associées.  
  
-   L'entité peut être sérialisée comme une entité complète.  
  
 Le fragment de code suivant illustre comment obtenir l'exécution locale :  
  
 [!code-csharp[DLinqQueryConcepts#8](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryConcepts/cs/Program.cs#8)]
 [!code-vb[DLinqQueryConcepts#8](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryConcepts/vb/Module1.vb#8)]  
  
## Comparaison  
 Ces deux fonctions fournissent une combinaison puissante d'options : communication à distance pour les grandes collections et exécution locale pour les petites collections ou lorsque la collection complète est nécessaire.  Implémentez la communication à distance via <xref:System.Linq.IQueryable> et l'exécution locale sur une collection <xref:System.Collections.Generic.IEnumerable%601> en mémoire.  Pour forcer l'exécution locale \(autrement dit, <xref:System.Collections.Generic.IEnumerable%601>\), consultez [Comment : convertir un type en IEnumerable générique](../../../../../../docs/framework/data/adonet/sql/linq/convert-a-type-to-a-generic-ienumerable.md).  
  
### Requêtes sur des jeux non ordonnés  
 Notez la différence importante entre une collection locale qui implémente <xref:System.Collections.Generic.List%601> et une collection qui fournit des requêtes distantes exécutées sur des *jeux non ordonnés* dans une base de données relationnelle.  Les méthodes <xref:System.Collections.Generic.List%601> telles que celles qui utilisent des valeurs d'index requièrent des sémantiques de liste que l'on ne peut généralement pas obtenir via une requête distante sur un jeu non ordonné.  Pour cette raison, de telles méthodes chargent implicitement le <xref:System.Data.Linq.EntitySet%601> pour autoriser l'exécution locale.  
  
## Voir aussi  
 [Concepts relatifs aux requêtes](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)