---
title: "Declaration Contexts and Default Access Levels (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "module level, defined"
  - "declaration contexts, Visual Basic"
  - "procedure level, defined"
  - "namespace level, defined"
  - "access levels, Visual Basic"
  - "access levels, default levels"
ms.assetid: bf63b96e-e825-4745-88c8-5dae222728db
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Declaration Contexts and Default Access Levels (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cette rubrique décrit quels types Visual Basic il est possible de déclarer dans quels autres types et quelle est la valeur par défaut de leurs niveaux d'accès si ceux\-ci ne sont pas spécifiés.  
  
## Niveaux de contexte de déclaration  
 Le *contexte de déclaration* d'un élément de programmation est la région de code dans laquelle il est déclaré.  Il s'agit souvent d'un autre élément de programmation, qui est ensuite appelé *élément contenant*.  
  
 Les niveaux de contextes de déclaration sont les suivants :  
  
-   *Niveau d'espace de noms* — dans un fichier source ou un espace de noms, mais pas dans une classe, une structure, un module ou une interface  
  
-   *Niveau de module* — dans une classe, une structure, un module ou une interface, mais pas dans une procédure ou un bloc  
  
-   *Niveau de procédure* — dans une procédure ou un bloc \(tel que `If` ou `For`\)  
  
 Le tableau suivant montre les niveaux d'accès par défaut de plusieurs éléments de programmation déclarés, selon leurs contextes de déclaration.  
  
|Élément déclaré|Niveau d'espace de noms|Niveau de module|Niveau de procédure|  
|---------------------|-----------------------------|----------------------|-------------------------|  
|Variable \([Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md)\)|Non autorisé|`Private` \(`Public` dans `Structure`, non autorisé dans `Interface`\)|`Public`|  
|Constante \([Const Statement](../../../visual-basic/language-reference/statements/const-statement.md)\)|Non autorisé|`Private` \(`Public` dans `Structure`, non autorisé dans `Interface`\)|`Public`|  
|Énumération \([Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)\)|`Friend`|`Public`|Non autorisé|  
|Classe \([Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)\)|`Friend`|`Public`|Non autorisé|  
|Structure \([Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)\)|`Friend`|`Public`|Non autorisé|  
|Module \([Module Statement](../../../visual-basic/language-reference/statements/module-statement.md)\)|`Friend`|Non autorisé|Non autorisé|  
|l'interface \([Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)\)|`Friend`|`Public`|Non autorisé|  
|Procédure \([Function Statement](../../../visual-basic/language-reference/statements/function-statement.md), [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)\)|Non autorisé|`Public`|Non autorisé|  
|Référence externe \([Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)\)|Non autorisé|`Public` \(non autorisé dans `Interface`\)|Non autorisé|  
|Opérateur \([Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)\)|Non autorisé|`Public` \(non autorisé dans `Interface` ou `Module`\)|Non autorisé|  
|Propriété \([Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)\)|Non autorisé|`Public`|Non autorisé|  
|Propriété par défaut \([Default](../../../visual-basic/language-reference/modifiers/default.md)\)|Non autorisé|`Public` \(non autorisé dans `Module`\)|Non autorisé|  
|Événement \([Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)\)|Non autorisé|`Public`|Non autorisé|  
|Délégué \([Delegate Statement](../../../visual-basic/language-reference/statements/delegate-statement.md)\)|`Friend`|`Public`|Non autorisé|  
  
 Pour plus d'informations, consultez [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## Voir aussi  
 [Friend](../../../visual-basic/language-reference/modifiers/friend.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [Public](../../../visual-basic/language-reference/modifiers/public.md)