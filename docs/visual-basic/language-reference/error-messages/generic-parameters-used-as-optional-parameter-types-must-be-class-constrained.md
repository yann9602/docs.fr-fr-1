---
title: "Generic parameters used as optional parameter types must be class constrained | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc32124"
  - "bc32124"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC32124"
ms.assetid: 55aa8b2a-9ce3-4620-a710-2f9b0feb6143
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Generic parameters used as optional parameter types must be class constrained
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Une procédure est déclarée avec un paramètre optionnel qui utilise un paramètre de type qui n'est pas contraint à être un type référence.  
  
 Vous devez toujours fournir une valeur par défaut pour chaque paramètre optionnel.  Si le paramètre est d'un type référence, la valeur facultative doit être `Nothing`, qui est une valeur valide pour tout type référence.  Toutefois, si le paramètre est d'un type valeur, ce type doit être un type de données élémentaire prédéfini par Visual Basic.  En effet, un type valeur composite, tel qu'une structure définie par l'utilisateur, n'a aucune valeur par défaut valide.  
  
 Lorsque vous utilisez un paramètre de type pour un paramètre optionnel, vous devez garantir qu'il soit d'un type référence pour éviter d'utiliser un type valeur sans valeur par défaut valide.  Cela signifie que vous devez contraindre le paramètre de type avec le mot clé `Class` ou avec le nom d'une classe spécifique.  
  
 **ID d'erreur :** BC32124  
  
### Pour corriger cette erreur  
  
-   Appliquez une contrainte au paramètre de type pour accepter uniquement un type référence, ou ne l'utilisez pas pour le paramètre optionnel.  
  
## Voir aussi  
 [Types génériques Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [Type List](../../../visual-basic/language-reference/statements/type-list.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)   
 [Structures](../../../visual-basic/programming-guide/language-features/data-types/structures.md)   
 [Nothing](../../../visual-basic/language-reference/nothing.md)