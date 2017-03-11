---
title: "Where Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryWhere"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Where statement"
  - "queries [Visual Basic], Where"
  - "Where clause"
ms.assetid: 48b5c2c5-3181-429c-8545-894296798c89
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Where Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Spécifie la condition de filtrage pour une requête.  
  
## Syntaxe  
  
```  
Where condition  
```  
  
## Composants  
 `condition`  
 Obligatoire.  Expression qui détermine si les valeurs de l'élément actuel de la collection sont incluses dans la collection de sortie.  L'expression doit prendre la valeur `Boolean` ou l'équivalent d'une valeur `Boolean`.  Si la condition prend la valeur `True`, l'élément est inclus dans le résultat de la requête ; sinon, l'élément en est exclu.  
  
## Notes  
 La clause `Where` vous permet de filtrer les données de requête en sélectionnant uniquement les éléments qui répondent à certains critères.  Les éléments dont les valeurs font que la clause `Where` prend la valeur `True` sont inclus dans le résultat de la requête ; les autres éléments sont exclus.  L'expression utilisée dans une clause `Where` doit prendre la valeur `Boolean` ou l'équivalent d'un `Boolean`, tel qu'un entier qui correspond à la valeur `False` lorsque sa valeur est nulle.  Vous pouvez associer plusieurs expressions dans une clause `Where` en utilisant des opérateurs logique tels que `And`, `Or`, `AndAlso`, `OrElse`, `Is` et `IsNot`.  
  
 Par défaut, les expressions de requête ne sont pas évaluées jusqu'à ce qu'elles soient accessibles, par exemple, lorsqu'elles sont liées aux données ou itérées au sein d'une boucle `For`.  En conséquence, la clause `Where` n'est pas évaluée avant l'accès à la requête.  Si des valeurs externes à la requête sont utilisées dans la clause `Where`, vérifiez que la valeur appropriée est utilisée dans la clause `Where` au moment où la requête est exécutée.  Pour plus d'informations sur l'exécution de la requête, consultez [Écriture de votre première requête LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
 Vous pouvez appeler des fonctions dans une clause `Where` pour effectuer un calcul ou une opération sur une valeur de l'élément actuel de la collection.  L'appel d'une fonction dans une clause `Where` peut provoquer l'exécution immédiate de la requête à sa définition plutôt qu'à son accès.  Pour plus d'informations sur l'exécution de la requête, consultez [Écriture de votre première requête LINQ](../../../visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query.md).  
  
## Exemple  
 L'expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `cust` pour chaque objet `Customer` de la collection `customers`.  La clause `Where` utilise la variable de portée pour restreindre la sortie aux clients de la région spécifiée.  La boucle `For Each` affiche le nom de société pour chaque client dans le résultat de la requête.  
  
 [!code-vb[VbSimpleQuerySamples#23](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#23)]  
  
## Exemple  
 l'exemple suivant utilise `And` et des opérateurs logiques d' `Or` dans la clause d' `Where` .  
  
 [!code-vb[VbSimpleQuerySamples#31](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#31)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [For Each...Next, instruction](../../../visual-basic/language-reference/statements/for-each-next-statement.md)