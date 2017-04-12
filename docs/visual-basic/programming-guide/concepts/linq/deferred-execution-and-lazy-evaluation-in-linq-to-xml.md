---
title: "Différé d’exécution et évaluation différées dans LINQ to XML (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3b7318eb9853d633d152b93fafcf9570ccd03835
ms.lasthandoff: 03/13/2017


---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>L’exécution différée et évaluation différées dans LINQ to XML (Visual Basic)
Les opérations de requête et d'axe sont souvent implémentées pour utiliser l'exécution différée. Cette rubrique explique les conditions requises et les avantages de l'exécution différée et certaines considérations relatives à l'implémentation.  
  
## <a name="deferred-execution"></a>Exécution différée  
 Différé l’exécution signifie que l’évaluation d’une expression est retardée jusqu'à ce que sa *réalisé* valeur soit réellement nécessaire. L'exécution différée peut améliorer sensiblement les performances lorsque vous devez manipuler de grandes collectes de données, en particulier dans les programmes qui contiennent une série de manipulations ou de requêtes chaînées. Dans le meilleur cas, l'exécution différée autorise une seule itération dans la collection source.  
  
 Les technologies LINQ utilisent beaucoup l’exécution différée dans les membres du noyau <xref:System.Linq?displayProperty=fullName>les classes et les méthodes d’extension dans les espaces de noms LINQ différents, tels que <xref:System.Xml.Linq.Extensions?displayProperty=fullName>.</xref:System.Xml.Linq.Extensions?displayProperty=fullName> </xref:System.Linq?displayProperty=fullName>  
  
## <a name="eager-vs-lazy-evaluation"></a>Évaluation stricte et évaluation différée  
 Lorsque vous écrivez une méthode qui implémente l'exécution différée, vous devez également décider s'il faut implémenter la méthode à l'aide de l'évaluation différée ou de l'évaluation stricte.  
  
-   Dans *l’évaluation tardive*, un seul élément de la collection source est traité durant chaque appel à l’itérateur. Il s'agit du mode d'implémentation par défaut des itérateurs.  
  
-   Dans *évaluation stricte*, le premier appel à l’itérateur entraîne dans l’ensemble de la collection en cours de traitement. Une copie temporaire de la collection source peut également être nécessaire. Par exemple, le <xref:System.Linq.Enumerable.OrderBy%2A>méthode doit trier l’ensemble de la collection avant de retourner le premier élément.</xref:System.Linq.Enumerable.OrderBy%2A>  
  
 L'évaluation différée procure en général de meilleures performances car elle répartit le traitement de surcharge de manière égale durant l'évaluation de la collection et limite l'utilisation des données temporaires. Bien entendu, pour certaines opérations il est impossible d'éviter la matérialisation de résultats intermédiaires.  
  
## <a name="next-steps"></a>Étapes suivantes  
 La rubrique suivante de ce didacticiel illustre l'exécution différée :  
  
-   [Exemple d’exécution différée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Différée de l’exécution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)   
 [Concepts et terminologie (Transformation fonctionnelle) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)   
 [Opérations d’agrégation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
