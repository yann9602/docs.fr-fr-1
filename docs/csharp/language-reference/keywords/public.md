---
title: "public (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "public"
  - "public_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "public (mot clé C#)"
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# public (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `public` est un modificateur d'accès pour les types et les membres de types.  L'accès public est le niveau d'accès le plus permissif.  Il n'existe pas de restrictions d'accès aux membres publics, comme dans cet exemple :  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 Pour plus d'informations, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) et [Niveaux d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md).  
  
## Exemple  
 Dans l'exemple suivant, deux classes sont déclarées, `PointTest` et `MainClass`.  L'accès aux membres publics `x` et `y` de `PointTest` s'effectue directement à partir de `MainClass`.  
  
 [!code-cs[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 Si vous modifiez le niveau d'accès `public` en [privé](../../../csharp/language-reference/keywords/private.md) ou [protégé](../../../csharp/language-reference/keywords/protected.md), vous obtiendrez le message d'erreur suivant :  
  
 'PointTest.y' est inaccessible en raison de son niveau de protection.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs d'accès](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Niveaux d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [privées](../../../csharp/language-reference/keywords/private.md)   
 [protégés](../../../csharp/language-reference/keywords/protected.md)   
 [interne](../../../csharp/language-reference/keywords/internal.md)