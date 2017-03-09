---
title: "Group Join Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryGroupJoinIn"
  - "vb.QueryGroupJoinOn"
  - "vb.QueryGroupJoin"
  - "vb.QueryGroupJoinInto"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Group Join clause"
  - "Group Join statement"
  - "queries [Visual Basic], Group Join"
ms.assetid: 37dbf79c-7b5c-421b-bbb7-dadfd2b92a1c
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Group Join Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Regroupe deux collections en une collection hiérarchique unique.  L'opération de jointure est basée sur des clés correspondantes.  
  
## Syntaxe  
  
```  
Group Join element [As type] In collection _  
  On key1 Equals key2 [ And key3 Equals key4 [... ] ] _  
  Into expressionList  
```  
  
## Composants  
  
|||  
|-|-|  
|Terme|Définition|  
|`element`|Obligatoire.  Variable de contrôle pour la collection qui est jointe.|  
|`type`|Facultatif.  Type de `element`.  Si aucun `type` n'est spécifié, le type d'`element` est déduit de `collection`.|  
|`collection`|Obligatoire.  Collection à combiner à la collection qui se trouve sur le côté gauche de l'opérateur `Group Join`.  Une clause `Group Join` peut être imbriquée dans une clause `Join` ou dans une autre clause `Group Join`.|  
|`key1` `Equals` `key2`|Obligatoire.  Identifie les clés des collections qui sont jointes.  Vous devez utiliser l'opérateur `Equals` pour comparer les clés des collections qui sont jointes.  Vous pouvez associer des conditions de jointure à l'aide de l'opérateur `And` afin d'identifier plusieurs clés.  Le paramètre `key1` doit provenir de la collection située du côté gauche de l'opérateur `Join`.  Le paramètre `key2` doit provenir de la collection située du côté droit de l'opérateur `Join`.<br /><br /> Les clés utilisées dans la condition de jointure peuvent être des expressions incluant plusieurs éléments de la collection.  Toutefois, chaque expression clé peut contenir uniquement des éléments de sa collection respective.|  
|`expressionList`|Obligatoire.  Une ou plusieurs expressions qui identifient comment les groupes d'éléments de la collection sont agrégés.  Pour identifier un nom de membre pour les résultats groupés, utilisez le mot clé `Group` \(`<alias> = Group`\).  Vous pouvez également inclure des fonctions d'agrégation à appliquer au groupe.|  
  
## Notes  
 La clause `Group Join` associe deux collections en fonctions des valeurs de clés correspondantes des collections qui sont jointes.  La collection résultante peut contenir un membre référençant une collection d'éléments de la deuxième collection qui correspondent à la valeur de clé de la première collection.  Vous pouvez également spécifier des fonctions d'agrégation à appliquer aux éléments groupés de la deuxième collection.  Pour plus d'informations sur les fonctions d'agrégation, consultez [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Prenons l'exemple d'une collection de gestionnaires et d'une collection d'employés.  Les éléments des deux collections ont une propriété ManagerID qui identifie les employés qui se rapportent à un gestionnaire particulier.  Les résultats d'une opération de jointure contiendraient un résultat pour chaque gestionnaire et employé possédant une valeur ManagerID correspondante.  Les résultats d'une opération `Group Join` contiendraient la liste complète de gestionnaires.  Chaque résultat de gestionnaire aurait un membre ayant référencé la liste des employés correspondant au gestionnaire spécifique.  
  
 La collection qui résulte d'une opération `Group Join` peut contenir toute combinaison de valeurs de la collection identifiée dans la clause `From` et les expressions identifiées dans la clause `Into` de la clause `Group Join`.  Pour plus d'informations sur les expressions valides pour la clause `Into`, consultez [Aggregate Clause](../../../visual-basic/language-reference/queries/aggregate-clause.md).  
  
 Une opération `Group Join` retournera tous les résultats de la collection identifiée sur le côté gauche de l'opérateur `Group Join`.  Cela est vrai même en l'absence de correspondances dans la collection qui est jointe.  Cela équivaut à `LEFT OUTER JOIN` dans SQL.  
  
 Vous pouvez utiliser la clause `Join` pour associer des collections dans une collection unique.  Cela équivaut à un `INNER JOIN` dans SQL.  
  
## Exemple  
 L'exemple de code suivant joint deux collections à l'aide de la clause `Group Join`.  
  
 [!code-vb[VbSimpleQuerySamples#14](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#14)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Join Clause](../../../visual-basic/language-reference/queries/join-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Group By, clause](../../../visual-basic/language-reference/queries/group-by-clause.md)