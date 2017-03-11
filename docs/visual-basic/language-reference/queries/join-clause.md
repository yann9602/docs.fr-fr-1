---
title: "Join Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QueryJoinIn"
  - "vb.QueryJoin"
  - "vb.QueryJoinOn"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Join"
  - "Join statement"
  - "Join clause"
ms.assetid: 6dd37936-b27c-4e00-98ad-154b23f4de64
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# Join Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Regroupe deux collections en une collection unique.  L'opération de jointure, basée sur la correspondance des clés, utilise l'opérateur `Equals`.  
  
## Syntaxe  
  
```  
Join element In collection _  
  [ joinClause _ ]   
  [ groupJoinClause ... _ ]   
On key1 Equals key2 [ And key3 Equals key4 [... ]  
```  
  
## Composants  
 `element`  
 Requis.  Variable de contrôle pour la collection qui est jointe.  
  
 `collection`  
 Requis.  Collection à combiner à la collection identifiée qui se trouve du côté gauche de l'opérateur `Join`.  Une clause `Join` peut être imbriquée dans une autre clause `Join` ou dans une clause `Group Join`.  
  
 `joinClause`  
 Optionnel.  Une ou plusieurs clauses supplémentaires `Join` pour affiner la requête.  
  
 `groupJoinClause`  
 Optionnel.  Une ou plusieurs clauses supplémentaires `Group Join` pour affiner la requête.  
  
 `key1` `Equals` `key2`  
 Requis.  Identifie les clés des collections qui sont jointes.  Vous devez utiliser l'opérateur `Equals` pour comparer les clés des collections qui sont jointes.  Vous pouvez associer des conditions de jointure à l'aide de l'opérateur `And` afin d'identifier plusieurs clés.  `key1` doit être de la collection sur le côté gauche de l'opérateur `Join`.  `key2` doit être à droite de la collection côté de l'opérateur `Join`.  
  
 Les clés utilisées dans la condition de jointure peuvent être des expressions incluant plusieurs éléments de la collection.  Toutefois, chaque expression clé peut contenir uniquement des éléments de sa collection respective.  
  
## Notes  
 La clause `Join` associe deux collections en fonctions des valeurs de clés correspondantes des collections qui sont jointes.  La collection résultante peut contenir toutes les combinaisons de valeurs de la collection identifiée située du côté gauche de l'opérateur `Join` et de la collection identifiée dans la clause `Join`.  La requête retournera uniquement des résultats pour lesquels la condition spécifiée par l'opérateur `Equals` est remplie.  Cela équivaut à un `INNER JOIN` dans SQL.  
  
 Vous pouvez utiliser plusieurs clauses `Join` dans une requête pour joindre deux collections ou plus en une collection unique.  
  
 Vous pouvez effectuer une jointure implicite pour combiner des collections sans la clause `Join`.  Pour ce faire, incluez plusieurs clauses `In` dans votre clause `From` et spécifiez une clause `Where` qui identifie les clés que vous souhaitez utiliser pour la jointure.  
  
 Vous pouvez utiliser la clause `Group Join` pour combiner des collections en une collection hiérarchique unique.  Cela équivaut à `LEFT OUTER JOIN` dans SQL.  
  
## Exemple  
 L'exemple de code suivant effectue une jointure implicite pour combiner une liste de clients avec leurs commandes.  
  
 [!code-vb[VbSimpleQuerySamples#13](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#13)]  
  
## Exemple  
 L'exemple de code suivant joint deux collections à l'aide de la clause `Join`.  
  
 [!code-vb[VbSimpleQuerySamples#12](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples2.vb#12)]  
  
 Cet exemple produira un résultat analogue à celui\-ci :  
  
 `winlogon (968), Windows Logon`  
  
 `explorer (2424), File Explorer`  
  
 `cmd (5136), Command Window`  
  
## Exemple  
 L'exemple de code suivant joint deux collections en utilisant la clause `Join` avec deux colonnes clés.  
  
 [!code-vb[VbSimpleQuerySamples#17](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples3.vb#17)]  
  
 L'exemple produira un résultat analogue à celui\-ci :  
  
 `winlogon (968), Windows Logon, Priority = 13`  
  
 `cmd (700), Command Window, Priority = 8`  
  
 `explorer (2424), File Explorer, Priority = 8`  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Group Join Clause](../../../visual-basic/language-reference/queries/group-join-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)