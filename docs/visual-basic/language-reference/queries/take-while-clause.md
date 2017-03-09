---
title: "Take While Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryTakeWhile"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Take While"
  - "Take While clause"
  - "Take While statement"
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# Take While Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Inclut des éléments dans une collection tant qu'une condition spécifiée est `true` et ignore les éléments restants.  
  
## Syntaxe  
  
```  
Take While expression  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`expression`|Obligatoire.  Expression représentant une condition pour tester des éléments.  L'expression doit retourner une valeur `Boolean` ou un équivalent fonctionnel, tel qu'un `Integer` à évaluer comme un `Boolean`.|  
  
## Notes  
 La clause `Take While` inclut des éléments depuis le démarrage d'un résultat de requête, jusqu'à ce que l' `expression` fournie retourne la valeur `false`.  Après que l'`expression` a retourné la valeur `false`, la requête ignore tous les éléments restants.  L' `expression` est ignorée pour les résultats restants.  
  
 La clause `Take While` diffère de la clause `Where` en ce sens que la clause `Where` peut être utilisée pour inclure tous les éléments d'une requête qui remplissent une condition particulière.  La clause `Take While` inclut des éléments jusqu'à la première fois que la condition n'est pas remplie uniquement.  La clause `Take While` est particulièrement utile lorsque vous travaillez avec un résultat de requête commandé.  
  
## Exemple  
 L'exemple de code suivant utilise la clause `Take While` pour récupérer des résultats jusqu'au premier client sans commande.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#2)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)