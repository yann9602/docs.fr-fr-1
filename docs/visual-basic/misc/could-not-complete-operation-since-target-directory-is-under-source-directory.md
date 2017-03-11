---
title: "Impossible d’achever l’op&#233;ration, car le r&#233;pertoire cible se situe sous le r&#233;pertoire source | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrIO_CyclicOperation"
ms.assetid: 850d3a24-5d51-4ac8-a912-630efcd75278
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Impossible d’achever l’op&#233;ration, car le r&#233;pertoire cible se situe sous le r&#233;pertoire source
Une opération cyclique a échoué. Les opérations cycliques se répètent et, par conséquent, ne peuvent pas s’achever. Par exemple, l’objet A peut essayer d’hériter de l’objet B qui hérite, à son tour, de l’objet A.  
  
### Pour corriger cette erreur  
  
-   Lors d’un héritage, vérifiez qu’il n’existe aucune référence cyclique.  
  
## Voir aussi  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)   
 [Debugging Basics: Breakpoints](http://msdn.microsoft.com/fr-fr/752a02c2-0ac7-4c8b-aa1b-4b2b3b21152e)