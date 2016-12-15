---
title: "WithEvents (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.WithEvents"
  - "WithEvents"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "WithEvents keyword"
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# WithEvents (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Indique qu'une ou plusieurs variables membres déclarées font référence à une instance d'une classe qui peut déclencher des événements.  
  
## Notes  
 Lorsqu'une variable est définie à l'aide de `WithEvents`, vous pouvez spécifier de façon déclarative qu'une méthode gère les événements de la variable à l'aide du mot clé `Handles`.  
  
 Vous pouvez utiliser `WithEvents` seulement au niveau de la classe ou du module.  Cela signifie que le contexte de déclaration pour une variable `WithEvents` doit être une classe ou un module, et ne peut pas être un fichier source, un espace de noms, une structure ou une procédure.  
  
 Vous ne pouvez pas utiliser `WithEvents` sur un membre de structure.  
  
 Vous ne pouvez déclarer que des variables, et non des tableaux, avec `WithEvents`.  
  
## Règles  
  
-   **Types d'éléments.** Vous devez déclarer les variables `WithEvents` comme des variables objet afin qu'elles puissent accepter des instances de classe.  Toutefois, vous ne pouvez pas les déclarer comme `Object`.  Vous devez les déclarer comme la classe spécifique capable de déclencher les événements.  
  
 Le modificateur `WithEvents` peut être utilisé dans le contexte suivant : [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## Voir aussi  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)