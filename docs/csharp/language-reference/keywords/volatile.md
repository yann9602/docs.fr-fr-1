---
title: "volatile (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "volatile_CSharpKeyword"
  - "volatile"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "volatile (mot clé C#)"
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 29
---
# volatile (r&#233;f&#233;rence C#)
Le mot clé `volatile` indique qu'un champ peut être modifié par plusieurs threads qui s'exécutent simultanément.  Les champs qui sont déclarés `volatile` ne sont pas soumis aux optimisations du compilateur qui supposent l'accès par un seul thread.  Cela garantit que la valeur la plus à jour est présente dans le champ à tout moment.  
  
 Le modificateur `volatile` est généralement utilisé pour un champ auquel accèdent plusieurs threads sans utiliser l'instruction [lock](../../../csharp/language-reference/keywords/lock-statement.md) pour sérialiser l'accès.  
  
 Le mot clé `volatile` peut être appliqué aux champs des types suivants :  
  
-   Types référence.  
  
-   Types pointeur \(dans un contexte unsafe\).  Notez que, même si le pointeur lui\-même peut être volatile, l'objet sur lequel il pointe ne le peut pas.  En d'autres termes, vous ne pouvez pas déclarer un pointeur vers un objet volatile.  
  
-   Types tels que sbyte, byte, short, ushort, int, uint, char, float et bool.  
  
-   Type enum avec l'un des types de base suivants : byte, sbyte, short, ushort, int, ou uint.  
  
-   Paramètres de type générique connus comme des types référence.  
  
-   <xref:System.IntPtr> et <xref:System.UIntPtr>.  
  
 Le mot clé volatile ne peut s'appliquer qu'aux champs d'une classe ou d'une structure.  Les variables locales ne peuvent pas être déclarées `volatile`.  
  
## Exemple  
 L'exemple ci\-dessous montre comment déclarer une variable de champ public comme `volatile`.  
  
 [!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## Exemple  
 L'exemple suivant montre comment il est possible de créer un thread auxiliaire ou de travail et de l'utiliser pour effectuer le traitement en parallèle avec le thread principal.  Pour obtenir des informations générales sur le multithreading, consultez [Threading](../Topic/Managed%20Threading.md) et [Thread](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md).  
  
 [!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)