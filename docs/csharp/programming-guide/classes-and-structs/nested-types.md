---
title: "Types imbriqu&#233;s (guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "types imbriqués (C#)"
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# Types imbriqu&#233;s (guide de programmation C#)
Un type défini dans une [classe](../../../csharp/language-reference/keywords/class.md) ou un [struct](../../../csharp/language-reference/keywords/struct.md) est appelé type imbriqué.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/nested-types_1.cs)]  
  
 Que le type externe soit une classe ou un struct, les types imbriqués sont [privés](../../../csharp/language-reference/keywords/private.md) par défaut, mais ils peuvent être rendus [publics](../../../csharp/language-reference/keywords/public.md), protégés internes, [protégés](../../../csharp/language-reference/keywords/protected.md), [internes](../../../csharp/language-reference/keywords/internal.md) ou [privés](../../../csharp/language-reference/keywords/private.md).  Dans l'exemple précédent, `Nested` est inaccessible aux types externes, mais peut être rendu public comme suit :  
  
 [!code-cs[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/nested-types_2.cs)]  
  
 Le type imbriqué, ou interne, peut accéder au type conteneur, ou externe.  Pour accéder au type conteneur, passez\-le comme constructeur au type imbriqué.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/nested-types_3.cs)]  
  
 Un type imbriqué a accès à tous les membres qui sont accessibles à son type conteneur.  Il peut accéder aux membres privés et protégés du type conteneur, y compris à tous les membres protégés hérités.  
  
 Dans la déclaration précédente, le nom complet de classe `Nested` est `Container.Nested`.  Il s'agit du nom utilisé pour créer une instance de la classe imbriquée, comme suit :  
  
 [!code-cs[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/csharp/nested-types_4.cs)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)   
 [Constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md)