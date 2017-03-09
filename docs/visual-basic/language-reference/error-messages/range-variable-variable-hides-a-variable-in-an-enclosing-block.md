---
title: "Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc36633"
  - "vbc36633"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36633"
ms.assetid: 5d5470e4-3de5-49c2-8831-1087625f4a77
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Range variable &lt;variable&gt; hides a variable in an enclosing block, a previously defined range variable, or an implicitly declared variable in a query expression
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Le nom de la variable de portée spécifié dans une clause `Select`, `From`, `Aggregate` ou `Let` duplique le nom d'une variable de portée spécifié précédemment dans la requête, ou le nom d'une variable déclaré implicitement par la requête, tel qu'un nom de champ ou le nom d'une fonction d'agrégation.  
  
 **ID d'erreur :** BC36633  
  
### Pour corriger cette erreur  
  
-   Vérifiez que toutes les variables de portée d'une portée de requête particulière ont des noms uniques.  Vous pouvez mettre une requête entre parenthèses pour vous assurer que les requêtes imbriquées ont une portée unique.  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Let Clause](../../../visual-basic/language-reference/queries/let-clause.md)   
 [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)