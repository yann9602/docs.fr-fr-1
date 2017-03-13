---
title: "Modificateurs d&#39;acc&#232;s (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "modificateurs d'accès (C#), à propos de"
  - "Langage C#, modificateurs d'accès"
ms.assetid: 6e81ee82-224f-4a12-9baf-a0dca2656c5b
caps.latest.revision: 32
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 32
---
# Modificateurs d&#39;acc&#232;s (Guide de programmation C#)
Tous les types et membres de type ont un niveau d'accessibilité, qui contrôle s'ils peuvent être utilisés à partir d'un autre code dans votre assembly ou d'autres assemblys.  Vous pouvez utiliser les modificateurs d'accès suivants pour spécifier l'accessibilité d'un type ou d'un membre lorsque vous le déclarez :  
  
 [public](../../../csharp/language-reference/keywords/public.md)  
 Tout autre code du même assembly ou d'un autre assembly qui y fait référence peut accéder au type ou au membre.  
  
 [private](../../../csharp/language-reference/keywords/private.md)  
 Seul le code de la même classe ou du même struct peut accéder au type ou au membre.  
  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 Seul le code de la même classe ou du même struct, ou d'une classe dérivée de cette classe, peut accéder au type ou au membre.  
  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 Tout code du même assembly, mais pas d'un autre assembly, peut accéder au type ou au membre.  
  
 `protected internal`  
 Le type ou le membre est accessible par tout code de l'assembly dans lequel il est déclaré, ou à partir d'une classe dérivée dans un autre assembly.  L'accès à partir d'un autre assembly doit avoir lieu dans une déclaration de classe qui dérive de la classe dans laquelle l'élément interne protégé est déclaré, et il doit avoir lieu via une instance du type de la classe dérivée.  
  
 Les exemples suivants montrent comment spécifier des modificateurs d'accès sur un type ou un membre :  
  
 [!code-cs[csProgGuideObjects#72](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_1.cs)]  
  
 Tous les modificateurs d'accès ne peuvent pas être utilisés par tous les types ou membres dans tous les contextes, et dans certains cas l'accessibilité d'un membre de type est contrainte par l'accessibilité de son type conteneur.  Les sections suivantes fournissent plus de détails sur l'accessibilité.  
  
## Accessibilité aux classes et structures  
 Les classes et les structures déclarées directement dans un espace de noms \(autrement dit, qui ne sont pas imbriquées dans d'autres classes ou structures\) peuvent être publiques ou internes.  Si aucun modificateur d'accès n'est spécifié, la valeur interne s'applique par défaut.  
  
 Les membres de struct, y compris les classes imbriquées et structs, peuvent être déclarés comme public, interne ou privé.  Les membres de classe, y compris les classes imbriquées et les structs, peuvent être publics, internes et protégés, protégés, internes ou privés.  Le niveau d'accès pour les membres de la classe et les membres de struct, y compris les classes imbriquées et structs, est privé par défaut.  Les types imbriqués privés ne sont pas accessibles en dehors du type conteneur.  
  
 Les classes dérivées ne peuvent pas avoir une accessibilité supérieure à leurs types de base.  Cela signifie que vous ne pouvez pas avoir une classe publique `B` qui provient d'une classe `A` interne.  Si cela était autorisé, cela rendrait `A` public, parce que tous les membres protégés ou internes de `A` sont accessibles à partir de la classe dérivée.  
  
 Vous pouvez permettre aux autres assemblys spécifiques d'accéder à vos types internes en utilisant InternalsVisibleToAttribute.  Pour plus d'informations, consultez [Assemblys friend](../Topic/Friend%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Accessibilité aux membres de classes et de structures  
 Les membres de classe \(y compris les classes imbriquées et structures\) peuvent être déclarés avec chacun des cinq types d'accès.  Les membres de struct ne peuvent pas être déclarés comme protégés parce que les structs ne prennent pas en charge l'héritage.  
  
 Normalement, l'accessibilité d'un membre n'est pas plus élevée que l'accessibilité du type qui la contient.  Toutefois, un membre public d'une classe interne peut être accessible depuis l'extérieur de l'assembly si le membre implémente les méthodes d'interface ou remplace des méthodes virtuelles définies dans une classe de base publique.  
  
 Le type d'un membre qui est un champ, une propriété ou un événement doit être au moins aussi accessibles que le membre lui\-même.  De même, le type de retour et les types de paramètres de tout membre qui est une méthode, un indexeur ou délégué doivent être au moins aussi accessibles que le membre lui\-même.  Par exemple, vous ne pouvez pas avoir une méthode `M` publique qui retourne une classe `C` à moins que `C` soit également public.  De même, vous ne pouvez pas avoir une propriété protégée de type `A` si `A` est déclaré comme privé.  
  
 Les opérateurs définis par l'utilisateur doivent toujours être déclarés publics.  Pour plus d'informations, consultez [d'opérateur](../../../csharp/language-reference/keywords/operator.md).  
  
 Les destructeurs ne peuvent pas avoir de modificateurs d'accessibilité.  
  
 Pour définir le niveau d'accès d'un membre de classe ou de struct, ajoutez le mot clé approprié à la déclaration de membre, comme indiqué dans l'exemple suivant.  
  
 [!code-cs[csProgGuideObjects#73](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/access-modifiers_2.cs)]  
  
> [!NOTE]
>  Le niveau d'accessibilité interne protégé signifie protégé OU interne, et non protégé ET interne.  En d'autres termes, un membre interne protégé peut être accessible à partir de n'importe quelle classe dans le même assembly, y compris les classes dérivées.  Pour limiter l'accessibilité aux seules classes dérivées du même assembly, déclarez la classe elle\-même comme interne et déclarez ses membres comme protégés.  
  
## Autres types  
 Les interfaces déclarées directement au sein d'un espace de noms peuvent être déclarées comme publiques ou internes, et comme les classes et structs, les interfaces ont comme valeur par défaut l'accès interne.  Les membres d'interface sont toujours publics parce que le but d'une interface est permettre à d'autres types d'accéder à une classe ou un struct.  Aucun modificateur d'accès ne peut être appliqué aux membres d'interface.  
  
 Les membres d'énumération sont toujours publics, et aucun modificateur d'accès ne peut être appliqué.  
  
 Les délégués se comportent comme des classes et des structures.  Par défaut, ils ont un accès interne lorsqu'ils sont déclarés directement dans un espace de noms, et un accès privé lorsqu'ils sont imbriqués.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)   
 [Interfaces](../../../csharp/programming-guide/interfaces/index.md)   
 [privées](../../../csharp/language-reference/keywords/private.md)   
 [public](../../../csharp/language-reference/keywords/public.md)   
 [interne](../../../csharp/language-reference/keywords/internal.md)   
 [protégés](../../../csharp/language-reference/keywords/protected.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [struct](../../../csharp/language-reference/keywords/struct.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)