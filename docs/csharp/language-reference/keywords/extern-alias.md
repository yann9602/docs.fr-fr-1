---
title: "extern alias (r&#233;f&#233;rence C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "alias_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "alias (C#), extern (mot clé)"
  - "alias, extern (mot clé)"
  - "extern alias (mot clé C#)"
ms.assetid: f487bf4f-c943-4fca-851b-e540c83d9027
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# extern alias (r&#233;f&#233;rence C#)
Il peut être nécessaire de référencer deux versions d'assemblys portant le même nom complet.  Par exemple lorsque vous devez utiliser deux versions ou plus d'un assembly dans la même application.  En utilisant un alias d'assembly externe, les espaces de noms de chaque assembly peuvent être encapsulés à l'intérieur d'espaces de noms racine nommés par l'alias, ce qui permet de les utiliser dans le même fichier.  
  
> [!NOTE]
>  Le mot clé [extern](../../../csharp/language-reference/keywords/extern.md) est également utilisé comme modificateur de méthode, qui déclare les méthodes écrites dans un code non managé.  
  
 Pour référencer deux assemblys portant le même nom complet, un alias doit être spécifié sur une invite de commande, comme suit :  
  
 `/r:GridV1=grid.dll`  
  
 `/r:GridV2=grid20.dll`  
  
 Cela crée les alias externes `GridV1` et `GridV2`.  Pour utiliser ces alias à partir d'un programme, référencez\-les à l'aide du mot clé `extern`.  Par exemple :  
  
 `extern alias GridV1;`  
  
 `extern alias GridV2;`  
  
 Chaque déclaration d'alias extern introduit un espace de noms racine supplémentaire qui se place parallèlement à l'espace de noms global, sans s'y intégrer.  On peut donc faire référence aux types de chaque assembly sans ambiguïté en utilisant leur nom complet, associé à une racine dans l'alias d'espace de noms approprié.  
  
 Dans l'exemple précédent, `GridV1::Grid` serait le contrôle Grid de `grid.dll` et `GridV2::Grid` serait le contrôle Grid de `grid20.dll`.  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Mots clés C\#](../../../csharp/language-reference/keywords/index.md)   
 [Mots clés d'espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [::, opérateur](../../../csharp/language-reference/operators/namespace-alias-qualifer.md)   
 [\/reference \(Import Metadata\)](../../../csharp/language-reference/compiler-options/reference-compiler-option.md)