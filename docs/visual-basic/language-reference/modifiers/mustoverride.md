---
title: "MustOverride (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.MustOverride"
  - "MustOverride"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "virtual elements, pure"
  - "elements, pure virtual"
  - "properties [Visual Basic], redefining"
  - "procedures, overriding"
  - "overriding, MustOverride keyword"
  - "procedures, redefining"
  - "pure virtual elements"
  - "MustOverride keyword"
  - "properties [Visual Basic], overriding"
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# MustOverride (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie qu'une propriété ou une procédure n'est pas implémentée dans une classe de base et doit être substituée dans une classe dérivée avant son utilisation.  
  
## Notes  
 Vous pouvez utiliser `MustOverride` uniquement dans une propriété ou une instruction de déclaration de procédure.  La propriété ou procédure qui spécifie `MustOverride` doit être un membre d'une classe, et la classe doit être marquée [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## Règles  
  
-   **Déclaration incomplète.** Lorsque vous spécifiez `MustOverride`, vous ne fournissez pas de lignes de code supplémentaires pour la propriété ou la procédure, ni l'instruction `End Function`, `End Property` ou `End Sub`.  
  
-   **Modificateurs combinés.** Vous ne pouvez pas spécifier `MustOverride` avec `NotOverridable`, `Overridable` ou `Shared` dans la même déclaration.  
  
-   **Occultation et substitution.** L'occultation et la substitution redéfinissent toutes les deux un élément hérité, mais les deux approches sont significativement différentes.  Pour plus d'informations, consultez [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Autres termes.** Un élément qui ne peut pas être utilisé sauf dans une substitution est parfois appelé élément *virtuel pur*.  
  
 Le modificateur `MustOverride` peut être utilisé dans les contextes suivants :  
  
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## Voir aussi  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)   
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)   
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)   
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)   
 [Mots clés](../../../visual-basic/language-reference/keywords/index.md)   
 [Shadowing in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)