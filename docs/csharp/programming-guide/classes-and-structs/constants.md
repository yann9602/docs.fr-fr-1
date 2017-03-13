---
title: "Constantes (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "langage C#, constantes"
  - "constantes (C#)"
ms.assetid: 1fb39621-1738-49b1-a1b3-8587f109123f
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# Constantes (Guide de programmation&#160;C#)
Les constantes sont des valeurs immuables qui sont connues au moment de la compilation et ne changent pas pendant la durée de vie du programme.  Les constantes sont déclarées avec le modificateur [const](../../../csharp/language-reference/keywords/const.md).  Seuls les types intégrés C\# \(à l'exclusion de <xref:System.Object?displayProperty=fullName>\) peuvent être déclarés comme `const`.  Pour obtenir une liste des types intégrés, consultez [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md).  Les types définis par l'utilisateur, y compris les classes, les structs et les tableaux, ne peuvent pas être `const`.  Utilisez le modificateur [readonly](../../../csharp/language-reference/keywords/readonly.md) pour créer une classe, un struct ou un tableau initialisé une fois au moment de l'exécution \(par exemple dans un constructeur\) et qui ne peut pas être modifié ultérieurement.  
  
 C\# ne prend pas en charge les méthodes, les propriétés ou les événements `const`.  
  
 Le type enum vous permet de définir des constantes nommées pour les types intégrés intégraux \(par exemple `int`, `uint`, `long`, et ainsi de suite\).  Pour plus d'informations, consultez [enum](../../../csharp/language-reference/keywords/enum.md).  
  
 Les constantes doivent être initialisées à mesure qu'elles sont déclarées.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#64](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_1.cs)]  
  
 Dans cet exemple, la constante `months` est toujours 12 et ne peut pas être modifiée, même par la classe elle\-même.  En fait, lorsque le compilateur rencontre un identificateur constant dans du code source C\# \(par exemple, `months`\), il substitue la valeur littérale directement dans le code IL \(Intermediate Language\) qu'il produit.  Étant donné qu'il n'y a aucune adresse de variable associée à une constante au moment de l'exécution, les champs `const` ne peuvent pas être passés par référence et ne peuvent pas apparaître comme l\-value dans une expression.  
  
> [!NOTE]
>  Procédez avec caution lorsque vous faites référence à des valeurs constantes définies dans un autre code, telles que des DLL.  Si une nouvelle version de la DLL définit une nouvelle valeur pour la constante, votre programme conserve l'ancienne valeur littérale jusqu'à ce qu'elle soit recompilée contre la nouvelle version.  
  
 Plusieurs constantes du même type peuvent être déclarées en même temps, par exemple :  
  
 [!code-cs[csProgGuideObjects#65](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_2.cs)]  
  
 L'expression qui est utilisée pour initialiser une constante peut faire référence à une autre constante si elle ne crée pas de référence circulaire.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#66](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_3.cs)]  
  
 Les constantes peuvent être marquées comme étant [publiques](../../../csharp/language-reference/keywords/public.md), [privées](../../../csharp/language-reference/keywords/private.md), [protégées](../../../csharp/language-reference/keywords/protected.md), [internes](../../../csharp/language-reference/keywords/internal.md) ou  `protected` `internal`.  Ces modificateurs d'accès définissent comment les utilisateurs de la classe peuvent accéder à la constante.  Pour plus d'informations, consultez [Modificateurs d'accès](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
 Les constantes sont accédées comme s'il s'agissait de champs [statiques](../../../csharp/language-reference/keywords/static.md) car la valeur de la constante est identique pour toutes les instances du type.  Vous n'utilisez pas le mot clé `static` pour les déclarer.  Les expressions qui ne sont pas dans la classe qui définit la constante doivent utiliser le nom de la classe, un point et le nom de la constante pour accéder à la constante.  Par exemple :  
  
 [!code-cs[csProgGuideObjects#67](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/constants_4.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md)   
 [Types](../../../csharp/programming-guide/types/index.md)   
 [readonly](../../../csharp/language-reference/keywords/readonly.md)   
 [Immuabilité en C\# Première partie : types d'immuabilité](http://go.microsoft.com/fwlink/?LinkId=112379)