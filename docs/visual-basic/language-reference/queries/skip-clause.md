---
title: "Skip Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QuerySkip"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Skip"
  - "Skip statement"
  - "Skip clause"
ms.assetid: f00eb172-3907-4c43-9745-d8546ab86234
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Skip Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Ignore un nombre spécifié d'éléments dans une collection, puis retourne les éléments restants.  
  
## Syntaxe  
  
```  
Skip count  
```  
  
## Composants  
 `count`  
 Obligatoire.  Valeur ou expression qui prend la valeur du nombre d'éléments de la séquence à ignorer.  
  
## Notes  
 La clause `Skip` force une requête à ignorer des éléments au début d'une liste de résultats et de retourner les éléments restants.  Le nombre d'éléments à ignorer est identifié par le paramètre `count`.  
  
 Vous pouvez utiliser la clause `Skip` avec la clause `Take` pour retourner une plage de données de n'importe quel segment d'une requête.  Pour ce faire, passez l'index du premier élément de la plage à la clause `Skip` et la taille de la plage à la clause `Take`.  
  
 Lorsque vous utilisez la clause `Skip` dans une requête, vous devez également vous assurer que les résultats sont retournés dans un ordre permettant à la clause `Skip` d'ignorer les résultats concernés.  Pour plus d'informations sur la façon de commander des résultats de requête, consultez [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md).  
  
 Vous pouvez utiliser la clause `SkipWhile` pour spécifier que seuls certains éléments doivent être ignorés, selon une condition fournie.  
  
## Exemple  
 L'exemple de code suivant associe la clause `Skip` à la clause `Take` pour retourner les données d'une requête dans des pages.  La fonction `GetCustomers` utilise la clause `Skip` pour ignorer les clients dans la liste jusqu'à la valeur d'index de départ fournie et utilise la clause `Take` pour retourner une page de clients qui débute à partir de cette valeur d'index.  
  
 [!code-vb[VbSimpleQuerySamples#1](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#1)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Skip While Clause](../../../visual-basic/language-reference/queries/skip-while-clause.md)   
 [Take Clause](../../../visual-basic/language-reference/queries/take-clause.md)