---
title: "Comment&#160;: effectuer sans risque un cast &#224; l&#39;aide des op&#233;rateurs as et is (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "as (opérateur C#)"
  - "cast (opérateurs C#), as et is (opérateurs)"
  - "Is (opérateur C#)"
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 10
---
# Comment&#160;: effectuer sans risque un cast &#224; l&#39;aide des op&#233;rateurs as et is (Guide de programmation&#160;C#)
Parce que les objets sont polymorphes, la variable d'un type de classe de base peut contenir un type dérivé.  Pour accéder à la méthode du type dérivé, il est nécessaire de caster la valeur pour la reconvertir en type dérivé.  Néanmoins, toute tentative de simple cast risque, dans de tels cas, de provoquer la levée d'une <xref:System.InvalidCastException>.  C'est pourquoi C\# fournit les opérateurs [is](../../../csharp/language-reference/keywords/is.md) et [as](../../../csharp/language-reference/keywords/as.md).  Vous pouvez utiliser ces opérateurs pour vérifier qu'un cast réussit sans provoquer la levée d'une exception.  En général, l'opérateur `as` est plus efficace parce qu'il retourne réellement la valeur de cast si le cast aboutit.  L'opérateur `is` retourne seulement une valeur booléenne.  Il peut être utilisé par conséquent lorsque vous souhaitez juste déterminer le type d'un objet, mais n'avez pas réellement à effectuer de cast.  
  
## Exemple  
 Les exemples suivants indiquent comment utiliser les opérateurs `is` et `as` pour effectuer un cast d'un type référence en un autre sans risquer de lever une exception.  Ils montrent également comment utiliser l'opérateur `as` avec des types valeur Nullable.  
  
 [!code-cs[csProgGuideTypes#40](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-safely-cast-by-using-as-and-is-operators_1.cs)]  
  
## Voir aussi  
 [Types](../../../csharp/programming-guide/types/index.md)   
 [Cast et conversions de types](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [Types Nullable](../../../csharp/programming-guide/nullable-types/index.md)