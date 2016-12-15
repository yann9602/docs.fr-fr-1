---
title: "override (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "override"
  - "override_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "override (mot clé C#)"
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
caps.latest.revision: 26
caps.handback.revision: 26
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# override (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le modificateur `override` est nécessaire pour étendre ou modifier l'implémentation abstraite ou virtuelle d'une méthode, d'une propriété, d'un indexeur ou d'un événement hérité\(e\).  
  
## Exemple  
 Dans cet exemple, la classe `Square` doit fournir une implémentation substituée de `Area` car `Area` est héritée de la classe abstraite `ShapesClass` :  
  
 [!code-cs[csrefKeywordsModifiers#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_1.cs)]  
  
 Une méthode `override` fournit une nouvelle implémentation d'un membre hérité d'une classe de base.  La méthode substituée par une déclaration `override` est appelée méthode de base substituée.  La méthode de base substituée doit avoir la même signature que la méthode `override`.  Pour plus d'informations sur l'héritage, consultez [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Vous pouvez substituer une méthode statique ou non virtuelle.  La méthode de base substituée doit être `virtual`, `abstract` ou `override`.  
  
 Une déclaration `override` ne peut pas changer l'accessibilité de la méthode `virtual`.  Les méthodes `override` et `virtual` doivent avoir le même [modificateur de niveau d'accès](../../../csharp/language-reference/keywords/access-modifiers.md).  
  
 Vous ne pouvez pas utiliser les modificateurs `new`, `static` ou `virtual` pour modifier une méthode `override`.  
  
 Une déclaration de propriété de substitution doit spécifier exactement les mêmes modificateur d'accès, type et nom que la propriété héritée, et la propriété substituée doit être `virtual`, `abstract` ou `override`.  
  
 Pour plus d'informations sur l'utilisation du mot clé `override`, consultez [Versioning avec les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) et [Savoir quand utiliser les mots clés override et new](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## Exemple  
 Cet exemple définit une classe de base nommée `Employee`, et une classe dérivée nommée `SalesEmployee`.  La classe `SalesEmployee` inclut une propriété supplémentaire, `salesbonus`, et substitue la méthode `CalculatePay` afin de prendre en compte cette dernière.  
  
 [!code-cs[csrefKeywordsModifiers#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/override_2.cs)]  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Héritage](../../../csharp/programming-guide/classes-and-structs/inheritance.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Modificateurs](../../../csharp/language-reference/keywords/modifiers.md)   
 [abstract](../../../csharp/language-reference/keywords/abstract.md)   
 [virtuels](../../../csharp/language-reference/keywords/virtual.md)   
 [new](../../../csharp/language-reference/keywords/new.md)   
 [Polymorphisme](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)