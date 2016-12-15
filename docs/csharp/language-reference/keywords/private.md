---
title: "private (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "private_CSharpKeyword"
  - "private"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "private (mot clé C#)"
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 17
caps.handback.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# private (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le mot clé `private` est un modificateur d'accès au membre.  L'accès privé est le niveau d'accès le moins permissif.  Les membres privés sont accessibles uniquement dans le corps de la classe ou de la structure où ils sont déclarés, comme dans l'exemple suivant :  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  
  
 Les types imbriqués dans le même corps peuvent également accéder à ces membres privés.  
  
 Référencer un membre privé en dehors de la classe ou du struct où il est déclaré serait à l'origine d'une erreur de compilation.  
  
 Pour comparer le modificateur d'accès `private` et les autres modificateurs d'accès, consultez [Niveaux d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md) et [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## Exemple  
 Dans cet exemple, la classe `Employee` contient deux membres de données privés, `name` et `salary`.  En tant que membres privés, ils ne sont pas accessibles, sauf par les méthodes membre.  Des méthodes publiques appelées `GetName` et `Salary` sont ajoutées pour permettre un accès contrôlé aux membres privés.  L'accès au membre `name` est réalisé via une méthode publique, et l'accès au membre `salary` via une propriété publique en lecture seule.  \(Consultez [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md) pour plus d'informations.\)  
  
 [!code-cs[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs d'accès](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Niveaux d'accessibilité](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [protégés](../../../csharp/language-reference/keywords/protected.md)   
 [interne](../../../csharp/language-reference/keywords/internal.md)