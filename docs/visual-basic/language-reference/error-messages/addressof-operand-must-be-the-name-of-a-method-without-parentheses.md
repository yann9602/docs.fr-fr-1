---
title: "&#39;AddressOf&#39; operand must be the name of a method (without parentheses) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30577"
  - "bc30577"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30577"
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &#39;AddressOf&#39; operand must be the name of a method (without parentheses)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

L'opérateur `AddressOf` crée une instance déléguée de procédure qui fait référence à une procédure spécifique.  La syntaxe est la suivante.  
  
 `AddressOf` `procedurename`  
  
 Vous avez inséré des parenthèses autour de l'argument qui suit `AddressOf`, alors qu'aucune parenthèse n'est requise.  
  
 **ID d'erreur :** BC30577  
  
### Pour corriger cette erreur  
  
1.  Supprimez les parenthèses autour de l'argument qui suit `AddressOf`.  
  
2.  Vérifiez que l'argument est un nom de méthode.  
  
## Voir aussi  
 [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md)   
 [Delegates](../../../visual-basic/programming-guide/language-features/delegates/delegates.md)