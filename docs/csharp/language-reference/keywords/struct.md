---
title: "struct (R&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "struct_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "struct (mot clé C#)"
  - "structures (C#), struct (mot clé)"
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: 23
caps.handback.revision: 23
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# struct (R&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Un type `struct` est un type valeur utilisé pour encapsuler de petits groupes de variables liées, par exemple les coordonnées d'un rectangle ou les caractéristiques d'un élément dans un inventaire.  L'exemple suivant illustre une déclaration struct simple :  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## Notes  
 Les structs peuvent également contenir des [constructeurs](../../../csharp/programming-guide/classes-and-structs/constructors.md), des [constantes](../../../csharp/programming-guide/classes-and-structs/constants.md), des [champs](../../../csharp/programming-guide/classes-and-structs/fields.md), des [méthodes](../../../csharp/programming-guide/classes-and-structs/methods.md), des [propriétés](../../../csharp/programming-guide/classes-and-structs/properties.md), des [indexeurs](../../../csharp/programming-guide/indexers/index.md), des [opérateurs](../../../csharp/programming-guide/statements-expressions-operators/operators.md), des [événements](../../../csharp/programming-guide/events/index.md), et des [types imbriqués](../../../csharp/programming-guide/classes-and-structs/nested-types.md), mais si plusieurs membres sont requis, il est conseillé d'utiliser une classe à la place.  
  
 Pour obtenir des exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
 Les structs peuvent implémenter une interface, mais ne peuvent pas hériter d'un autre struct.  C'est pourquoi, les membres struct ne peuvent pas être déclarés en tant que `protected`.  
  
 Pour plus d'informations, consultez [Structures](../../../csharp/programming-guide/classes-and-structs/structs.md).  
  
## Exemples  
 Pour plus d'informations et d'exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## Spécification du langage C\#  
 Pour obtenir des exemples, consultez [Utilisation de structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Tableau des valeurs par défaut](../../../csharp/language-reference/keywords/default-values-table.md)   
 [Tableau des types intégrés](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [Types](../../../csharp/language-reference/keywords/types.md)   
 [Types valeur](../../../csharp/language-reference/keywords/value-types.md)   
 [classe](../../../csharp/language-reference/keywords/class.md)   
 [interface](../../../csharp/language-reference/keywords/interface.md)   
 [Classes et structs](../../../csharp/programming-guide/classes-and-structs/index.md)