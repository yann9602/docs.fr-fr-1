---
title: "::, op&#233;rateur (r&#233;f&#233;rence C#) | Microsoft Docs"
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
  - "::_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - ":: (opérateur C#)"
  - "opérateur du qualificateur d'alias de l'espace de noms (::) (C#)"
  - "espaces de noms (C#), :: (opérateur)"
ms.assetid: 698b5a73-85cf-4e0e-9e8e-6496887f8527
caps.latest.revision: 21
caps.handback.revision: 21
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# ::, op&#233;rateur (r&#233;f&#233;rence C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le qualificateur d'alias d'espace de noms \(`::`\) sert à rechercher les identificateurs.  Il est toujours positionné entre deux identificateurs, comme dans l'exemple suivant :  
  
 [!code-cs[csRefOperators#27](../../../csharp/language-reference/operators/codesnippet/CSharp/namespace-alias-qualifer_1.cs)]  
  
## Notes  
 Le qualificateur d'alias d'espace de noms peut être `global`.  Cela appelle une recherche dans l'espace de noms global, plutôt que dans un espace de noms sous alias.  
  
## Pour plus d'informations  
 Pour obtenir un exemple d'utilisation de l'opérateur `::`, consultez la section suivante :  
  
-   [Comment : utiliser l'alias d'espace de noms global](../../../csharp/programming-guide/namespaces/how-to-use-the-global-namespace-alias.md)  
  
## Spécification du langage C\#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## Voir aussi  
 [Référence C\#](../../../csharp/language-reference/index.md)   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Opérateurs C\#](../../../csharp/language-reference/operators/index.md)   
 [Mots clés d'espaces de noms](../../../csharp/language-reference/keywords/namespace-keywords.md)   
 [. Opérateur](../../../csharp/language-reference/operators/member-access-operator.md)   
 [extern alias](../../../csharp/language-reference/keywords/extern-alias.md)