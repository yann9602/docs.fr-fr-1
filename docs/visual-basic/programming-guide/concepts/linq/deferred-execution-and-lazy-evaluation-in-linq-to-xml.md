---
title: "L’exécution différée et évaluation différées dans LINQ to XML (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 31998eed-b95e-47fb-a865-9de1f337d1fb
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a465c4448157505a42db57202298cb18e44a562
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="deferred-execution-and-lazy-evaluation-in-linq-to-xml-visual-basic"></a>L’exécution différée et évaluation différées dans LINQ to XML (Visual Basic)
Les opérations de requête et d'axe sont souvent implémentées pour utiliser l'exécution différée. Cette rubrique explique les conditions requises et les avantages de l'exécution différée et certaines considérations relatives à l'implémentation.  
  
## <a name="deferred-execution"></a>Exécution différée  
 Le terme "exécution différée" signifie que l’évaluation d’une expression est retardée jusqu’à ce que sa valeur *réalisée* soit réellement nécessaire. L'exécution différée peut améliorer sensiblement les performances lorsque vous devez manipuler de grandes collectes de données, en particulier dans les programmes qui contiennent une série de manipulations ou de requêtes chaînées. Dans le meilleur cas, l'exécution différée autorise une seule itération dans la collection source.  
  
 Les technologies LINQ utilisent beaucoup l'exécution différée dans les membres des classes <xref:System.Linq?displayProperty=nameWithType> principales et dans les méthodes d'extension dans les différents espaces de noms LINQ, tels que <xref:System.Xml.Linq.Extensions?displayProperty=nameWithType>.  
  
## <a name="eager-vs-lazy-evaluation"></a>Évaluation stricte et évaluation différée  
 Lorsque vous écrivez une méthode qui implémente l'exécution différée, vous devez également décider s'il faut implémenter la méthode à l'aide de l'évaluation différée ou de l'évaluation stricte.  
  
-   Avec l’*évaluation différée*, un seul élément de la collection source est traité pendant chaque appel à l’itérateur. Il s'agit du mode d'implémentation par défaut des itérateurs.  
  
-   Avec l’*évaluation stricte*, le premier appel à l’itérateur entraîne le traitement de l’ensemble de la collection. Une copie temporaire de la collection source peut également être nécessaire. Par exemple, la méthode <xref:System.Linq.Enumerable.OrderBy%2A> doit trier l'ensemble de la collection avant de renvoyer le premier élément.  
  
 L'évaluation différée procure en général de meilleures performances car elle répartit le traitement de surcharge de manière égale durant l'évaluation de la collection et limite l'utilisation des données temporaires. Bien entendu, pour certaines opérations il est impossible d'éviter la matérialisation de résultats intermédiaires.  
  
## <a name="next-steps"></a>Étapes suivantes  
 La rubrique suivante de ce didacticiel illustre l'exécution différée :  
  
-   [Exemple d’exécution différée (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-example.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel : Différée d’exécution (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/tutorial-deferred-execution.md)  
 [Concepts et terminologie (Transformation fonctionnelle) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/concepts-and-terminology-functional-transformation.md)  
 [Opérations d’agrégation (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/aggregation-operations.md)
