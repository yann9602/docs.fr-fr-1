---
title: "Take Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryTake"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Take statement"
  - "queries [Visual Basic], Take"
  - "Take clause"
ms.assetid: 77bf87b2-1476-4456-957f-fee922fbad8c
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# Take Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Retourne un nombre spécifié d'éléments contigus à partir du début d'une collection.  
  
## Syntaxe  
  
```  
Take count  
```  
  
## Composants  
 `count`  
 Obligatoire.  Valeur ou expression qui prend la valeur du nombre d'éléments de la séquence à retourner.  
  
## Notes  
 La clause `Take` entraîne l'inclusion dans une requête d'un nombre spécifié d'éléments contigus dès le début d'une liste des résultats.  Le nombre d'éléments à inclure est spécifié par le paramètre `count`.  
  
 Vous pouvez utiliser la clause `Take` avec la clause `Skip` pour retourner une plage de données de n'importe quel segment d'une requête.  Pour ce faire, passez l'index du premier élément de la plage à la clause `Skip` et la taille de la plage à la clause `Take`.  Dans ce cas, la clause `Take` doit être spécifiée après la clause `Skip`.  
  
 Lorsque vous utilisez la clause `Take` dans une requête, vous devez également vous assurer que les résultats sont retournés dans un ordre qui permettra à la clause `Take` d'inclure les résultats prévus.  Pour plus d'informations sur la façon de commander des résultats de requête, consultez [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Vous pouvez utiliser la clause `TakeWhile` pour spécifier que seuls certains éléments soient retournés, selon une condition fournie.  
  
## Exemple  
 L'exemple de code suivant associe la clause `Take` à la clause `Skip` pour retourner les données d'une requête dans des pages.  La fonction GetCustomers utilise la clause `Skip` pour ignorer les clients dans la liste jusqu'à la valeur d'index de départ fournie et utilise la clause `Take` pour retourner une page de clients qui débute à partir de cette valeur d'index.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-clause_1.vb)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Take While Clause](../../../visual-basic/language-reference/queries/take-while-clause.md)   
 [Skip Clause](../../../visual-basic/language-reference/queries/skip-clause.md)