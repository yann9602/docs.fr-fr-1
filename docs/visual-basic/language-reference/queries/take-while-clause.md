---
title: Take While, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c8add6c55bb9353bac3489e68f497cb32785aad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="take-while-clause-visual-basic"></a>Take While, clause (Visual Basic)
Inclut les éléments d'une collection tant qu'une condition spécifiée a la valeur `true` et ignore les éléments restants.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Take While expression  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`expression`|Obligatoire. Une expression qui représente une condition pour tester des éléments. L’expression doit retourner un `Boolean` valeur ou un équivalent fonctionnel, comme un `Integer` soit évaluée comme une `Boolean`.|  
  
## <a name="remarks"></a>Remarques  
 Le `Take While` clause inclut des éléments depuis le début d’un résultat de la requête jusqu'à ce que l’élément `expression` retourne `false`. Après le `expression` retourne `false`, la requête ignore tous les éléments restants. Le `expression` est ignoré pour les autres résultats.  
  
 Le `Take While` diffère de la clause le `Where` clause qui le `Where` clause peut être utilisée pour inclure tous les éléments d’une requête qui remplissent une condition particulière. Le `Take While` clause inclut des éléments uniquement jusqu'à la première fois que la condition n’est pas satisfaite. Le `Take While` clause est particulièrement utile lorsque vous travaillez avec un résultat de requête commandé.  
  
## <a name="example"></a>Exemple  
 Le code suivant exemple utilise le `Take While` clause pour extraire les résultats jusqu'à ce que le premier client sans commande est trouvé.  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Requêtes](../../../visual-basic/language-reference/queries/queries.md)  
 [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Take (clause)](../../../visual-basic/language-reference/queries/take-clause.md)  
 [Skip While (clause)](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)
