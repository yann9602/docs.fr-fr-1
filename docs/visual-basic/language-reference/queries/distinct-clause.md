---
title: "Distinct Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryDistinct"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Distinct clause"
  - "Distinct statement"
  - "queries [Visual Basic], Distinct"
ms.assetid: 86f42614-0d8f-4ffc-b888-ce8a37a8d36a
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Distinct Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Restreint les valeurs de la variable de portée actuelle pour éliminer des valeurs en double dans les clauses de requête suivantes.  
  
## Syntaxe  
  
```  
Distinct  
```  
  
## Notes  
 Vous pouvez utiliser la clause `Distinct` pour retourner une liste d'éléments uniques.  La clause `Distinct` permet d'ignorer les doublons dans les résultats de la requête.  La clause `Distinct` s'applique aux valeurs doubles de tous les champs retournés, spécifiés par la clause `Select`.  Si aucune clause `Select` n'est spécifiée, la clause `Distinct` est appliquée à la variable de portée pour la requête identifiée dans la clause `From`.  Si la variable de portée n'est pas un type immuable, la requête n'ignore un résultat de requête que si tous les membres de ce type correspondent à un résultat existant de la requête.  
  
## Exemple  
 L'expression de requête suivante joint une liste de clients et une liste de commandes passées par ces clients.  La clause `Distinct` est incluse pour retourner une liste de noms de clients et de dates de commandes uniques.  
  
 [!code-vb[VbSimpleQuerySamples#20](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#20)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)