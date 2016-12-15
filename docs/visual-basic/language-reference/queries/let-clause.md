---
title: "Let Clause (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QueryLet"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Let"
  - "Let clause"
  - "Let statement"
ms.assetid: 981aa516-16eb-4c53-b1f1-5aa3e82f316e
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Let Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Calcule une valeur et l'assigne à une nouvelle variable dans la requête.  
  
## Syntaxe  
  
```  
Let variable = expression [, ...]  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`variable`|Obligatoire.  Alias qui peut être utilisé pour référencer les résultats de l'expression fournie.|  
|`expression`|Obligatoire.  Expression destinée à être évaluée et assignée à la variable spécifiée.|  
  
## Notes  
 La clause `Let` vous permet de calculer les valeurs de chaque résultat de requête et de les référencer en utilisant un alias.  Cet alias peut être utilisé dans d'autres clauses, telles que la clause `Where`.  La clause `Let` vous permet de créer une instruction de requête plus facile à lire, puisque vous pouvez spécifier un alias pour une clause d'expression incluse dans la requête et substituer l'alias chaque fois que la clause d'expression est utilisée.  
  
 Vous pouvez inclure tout nombre d'assignations `variable` et `expression` dans la clause `Let`.  Séparez chaque assignation par une virgule \(,\).  
  
## Exemple  
 L'exemple de code suivant utilise la clause `Let` pour calculer 10 pour cent de remise sur les produits.  
  
 [!code-vb[VbSimpleQuerySamples#16](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/let-clause_1.vb)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)