---
title: "Niveaux d&#39;accessibilit&#233; (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "modificateurs d'accès (C#), niveaux d'accessibilité"
  - "niveaux d'accessibilité"
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Niveaux d&#39;accessibilit&#233; (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Utilisez les modificateurs d'accès, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md) ou [private](../../../csharp/language-reference/keywords/private.md) pour spécifier l'un des niveaux d'accessibilité déclarés ci\-dessous pour les membres.  
  
|Accessibilité déclarée|Signification|  
|----------------------------|-------------------|  
|`public`|L'accès n'est pas limité.|  
|`protected`|L'accès est restreint à la classe conteneur ou aux types dérivés de la classe conteneur.|  
|`internal`|L'accès est restreint à l'assembly en cours.|  
|`protected` `internal`|L'accès est restreint à l'assembly en cours ou aux types dérivés de la classe conteneur.|  
|`private`|L'accès est restreint au type conteneur.|  
  
 Un seul modificateur d'accès est autorisé pour un membre ou un type, sauf si l'on utilise la combinaison `protected` `internal`.  
  
 Les modificateurs d'accès ne sont pas autorisés sur les espaces de noms.  Les espaces de noms ne présentent aucune limitation d'accès.  
  
 Selon le contexte dans lequel une déclaration de membre est effectuée, seules certaines accessibilités déclarées sont autorisées.  Si aucun modificateur d'accès est spécifié dans une déclaration de membre, une accessibilité par défaut est utilisée.  
  
 Les types de niveau supérieur, qui ne sont pas imbriqués dans d'autres types, ne peuvent disposer que d'une accessibilité `internal` ou `public`.  L'accessibilité par défaut de ces types est `internal`.  
  
 Les types imbriqués, qui sont membres d'autres types, peuvent disposer d'accessibilités déclarées, comme indiqué dans le tableau suivant.  
  
|Membres de|Accessibilité des membres par défaut|Accessibilité déclarée autorisée du membre|  
|----------------|------------------------------------------|------------------------------------------------|  
|`enum`|`public`|Aucun|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected` `internal`|  
|`interface`|`public`|Aucun|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 L'accessibilité d'un type imbriqué dépend de son [domaine d'accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md), qui est déterminé par l'accessibilité déclarée du membre et le domaine d'accessibilité du type conteneur immédiat.  Toutefois, le domaine d'accessibilité d'un type imbriqué ne peut pas dépasser celui du type conteneur.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs d'accès](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Domaine d'accessibilité](../../../csharp/language-reference/keywords/accessibility-domain.md)   
 [Limitations sur l'utilisation des niveaux d'accessibilité](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)   
 [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [privées](../../../csharp/language-reference/keywords/private.md)   
 [protégés](../../../csharp/language-reference/keywords/protected.md)   
 [interne](../../../csharp/language-reference/keywords/internal.md)