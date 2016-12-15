---
title: "Skip While Clause (Visual Basic) | Microsoft Docs"
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
  - "vb.QuerySkipWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Skip While statement"
  - "Skip While clause"
  - "queries [Visual Basic], Skip While"
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Skip While Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Ignore les éléments d'une collection tant qu'une condition spécifiée est `true`, puis retourne les éléments restants.  
  
## Syntaxe  
  
```  
Skip While expression  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`expression`|Obligatoire.  Expression représentant une condition pour tester des éléments.  L'expression doit retourner une valeur `Boolean` ou un équivalent fonctionnel, tel qu'un `Integer` à évaluer comme un `Boolean`.|  
  
## Notes  
 La clause `Skip While` ignore les éléments du début d'un résultat de la requête jusqu'à ce que l' `expression` fournie retourne la valeur `false`.  Après que `expression` a retourné la valeur `false`, la requête retourne tous les éléments restants.  L' `expression` est ignorée pour les résultats restants.  
  
 La clause `Skip While` diffère de la clause `Where` en ce sens que la clause `Where` peut être utilisée pour exclure tous les éléments d'une requête qui ne remplissent pas une condition particulière.  La clause `Skip While` exclut des éléments tant que la condition n'est pas remplie.  La clause `Skip While` est particulièrement utile lorsque vous travaillez avec un résultat de requête commandé.  
  
 Vous pouvez ignorer un nombre spécifique de résultats depuis le début d'un résultat de requête en utilisant la clause `Skip`.  
  
## Exemple  
 L'exemple de code suivant utilise la clause `Skip While` pour ignorer des résultats jusqu'à ce que le premier client des États\-Unis soit trouvé.  
  
 [!code-vb[VbSimpleQuerySamples#3](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/skip-while-clause_1.vb)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)