---
title: "into (R&#233;f&#233;rence&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "into_CSharpKeyword"
  - "into"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "into (mot clé C#)"
ms.assetid: 81ec62c1-f0b1-4755-8a31-959876e77f65
caps.latest.revision: 18
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 18
---
# into (R&#233;f&#233;rence&#160;C#)
Le mot clé contextuel `into` peut être utilisé pour créer un identificateur temporaire pour stocker les résultats d'une clause [group](../../../csharp/language-reference/keywords/group-clause.md), [join](../../../csharp/language-reference/keywords/join-clause.md) ou [select](../../../csharp/language-reference/keywords/select-clause.md) dans un nouvel identificateur.  Cet identificateur peut lui\-même être un générateur pour les commandes de requête supplémentaires.  En cas d'utilisation dans une clause `group` ou `select`, l'utilisation du nouvel identificateur est parfois connue sous le nom de *continuation*.  
  
## Exemple  
 L'exemple suivant illustre l'utilisation du mot clé `into` pour activer un identificateur temporaire `fruitGroup` qui a un type déduit de `IGrouping`.  En utilisant l'identificateur, vous pouvez appeler la méthode <xref:System.Linq.Enumerable.Count%2A> sur chaque groupe et sélectionner uniquement ceux qui contiennent deux mots ou plus.  
  
 [!code-cs[cscsrefQueryKeywords#18](../../../csharp/language-reference/keywords/codesnippet/csharp/csquerykeywords/Into.cs#18)]  
  
 L'utilisation d'`into` dans une clause `group` est nécessaire uniquement lorsque vous souhaitez effectuer des opérations de requête supplémentaires sur chaque groupe.  Pour plus d'informations, consultez [group, clause](../../../csharp/language-reference/keywords/group-clause.md).  
  
 Pour un exemple de l'utilisation d'`into` dans une clause `join`, consultez [join, clause](../../../csharp/language-reference/keywords/join-clause.md).  
  
## Voir aussi  
 [Mots clés de requête \(LINQ\)](../../../csharp/language-reference/keywords/query-keywords.md)   
 [Expressions de requête \(LINQ\)](../../../csharp/programming-guide/linq-query-expressions/index.md)   
 [group, clause](../../../csharp/language-reference/keywords/group-clause.md)