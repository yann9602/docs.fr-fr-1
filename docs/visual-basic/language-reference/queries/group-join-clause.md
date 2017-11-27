---
title: Group Join, clause (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.QueryGroupJoinIn
- vb.QueryGroupJoinOn
- vb.QueryGroupJoin
- vb.QueryGroupJoinInto
helpviewer_keywords:
- Group Join clause [Visual Basic]
- Group Join statement [Visual Basic]
- queries [Visual Basic], Group Join
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c43b41336393b40684aee79f88c1e6999ebda674
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="group-join-clause-visual-basic"></a>Group Join, clause (Visual Basic)
Combine deux collections en une collection hiérarchique unique. L’opération de jointure est basée sur les clés correspondantes.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## <a name="parts"></a>Composants  
  
|Terme|Définition|  
|---|---|  
|`element`|Obligatoire. La variable de contrôle de la collection jointe.|  
|`type`|Facultatif. Type d'élément `element`. Si aucun `type` est spécifié, le type de `element` est déduit à partir de `collection`.|  
|`collection`|Obligatoire. La collection à combiner à la collection qui se trouve sur le côté gauche de la `Group Join` opérateur. A `Group Join` clause peut être imbriquée dans une `Join` clause ou dans un autre `Group Join` clause.|  
|`key1` `Equals` `key2`|Requis. Identifie les clés pour les collections qui sont jointes. Vous devez utiliser le `Equals` pour comparer les clés des collections qui sont jointes. Vous pouvez combiner des conditions de jointure à l’aide de la `And` opérateur afin d’identifier plusieurs clés. Le `key1` paramètre doit être de la collection sur le côté gauche de la `Join` opérateur. Le `key2` paramètre doit être de la collection sur le côté droit de la `Join` opérateur.<br /><br /> Les clés utilisées dans la condition de jointure peuvent être des expressions incluant plusieurs éléments de la collection. Toutefois, chaque expression clé peut contenir uniquement les éléments à partir de sa collection respective.|  
|`expressionList`|Obligatoire. Une ou plusieurs expressions qui identifient la façon dont les groupes d’éléments de la collection sont agrégés. Pour identifier un nom de membre pour les résultats groupés, utilisez le `Group` (mot clé) (`<alias> = Group`). Vous pouvez aussi inclure des fonctions d’agrégation à appliquer au groupe.|  
  
## <a name="remarks"></a>Remarques  
 Le `Group Join` clause combine deux collections en fonction des valeurs de clés correspondantes des collections qui sont jointes. La collection résultante peut contenir un membre qui fait référence à une collection d’éléments de la deuxième collection qui correspondent à la valeur de clé à partir de la première collection. Vous pouvez également spécifier des fonctions d’agrégation à appliquer aux éléments groupés de la deuxième collection. Pour plus d’informations sur les fonctions d’agrégation, consultez [Aggregate, Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Considérons, par exemple, une collection de gestionnaires et une collection d’employés. Éléments des deux collections ont une propriété ManagerID qui identifie les employés qui réfèrent à un gestionnaire particulier. Les résultats d’une opération de jointure contiendraient un résultat pour chaque gestionnaire et employé avec une valeur ManagerID correspondante. Les résultats d’une `Group Join` opération contient la liste complète des gestionnaires. Chaque résultat de gestionnaire aurait un membre qui a référencé la liste des employés qui ont une correspondance pour le gestionnaire spécifique.  
  
 La collection qui résulte d’une `Group Join` opération peut contenir n’importe quelle combinaison de valeurs à partir de la collection identifiée dans la `From` clause et les expressions identifiées dans le `Into` clause de la `Group Join` clause. Pour plus d’informations sur les expressions valides pour la `Into` clause, consultez [Aggregate, Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 A `Group Join` opération retournera tous les résultats de la collection identifiée sur le côté gauche de la `Group Join` opérateur. Cela est vrai même si aucune correspondance dans la collection jointe. Il s’agit comme un `LEFT OUTER JOIN` dans SQL.  
  
 Vous pouvez utiliser la `Join` clause pour combiner des collections en une collection unique. Cela équivaut à un `INNER JOIN` dans SQL.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant joint deux collections à l’aide de la `Group Join` clause.  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/group-join-clause_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Introduction à LINQ en Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Requêtes](../../../visual-basic/language-reference/queries/queries.md)  
 [Select (clause)](../../../visual-basic/language-reference/queries/select-clause.md)  
 [From (clause)](../../../visual-basic/language-reference/queries/from-clause.md)  
 [Join (clause)](../../../visual-basic/language-reference/queries/join-clause.md)  
 [Where (clause)](../../../visual-basic/language-reference/queries/where-clause.md)  
 [Group By (clause)](../../../visual-basic/language-reference/queries/group-by-clause.md)
