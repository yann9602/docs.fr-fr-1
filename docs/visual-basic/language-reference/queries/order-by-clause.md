---
title: "Order By Clause (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.QueryOrderBy"
  - "vb.QueryAscending"
  - "vb.QueryDescending"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "queries [Visual Basic], Order By"
  - "Order By clause"
  - "Order By statement"
ms.assetid: fa911282-6b81-44c7-acfa-46b5bb93df75
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Order By Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Spécifie l'ordre de tri pour un résultat de requête.  
  
## Syntaxe  
  
```  
Order By orderExp1 [ Ascending | Descending ] [, orderExp2 [...] ]  
```  
  
## Composants  
 `orderExp1`  
 Obligatoire.  Un ou plusieurs champs du résultat actuel de la requête identifiant la manière de classer les valeurs retournées.  Les noms de champs doivent être séparés par une virgule \(,\).  Vous pouvez identifier l'ordre de tri de chaque champ, croissant ou décroissant, en utilisant les mots clés `Ascending` ou `Descending`.  Si aucun mot clé `Ascending` ou `Descending` n'est spécifié, l'ordre de tri par défaut est l'ordre croissant.  La priorité des champs d'ordre de tri se fait de gauche à droite.  
  
## Notes  
 Vous pouvez utiliser la clause `Order By` pour trier les résultats d'une requête.  La clause `Order By` ne peut trier qu'un résultat basé sur la variable de portée de la portée actuelle.  Par exemple, la clause `Select` introduit une nouvelle portée dans une expression de requête avec de nouvelles variables d'itération pour cette portée.  Les variables de portée définies avant une clause `Select` dans une requête ne sont pas disponibles après la clause `Select`.  Par conséquent, si vous souhaitez classer vos résultats par champ non disponible dans la clause `Select`, vous devez placer la clause `Order By` avant la clause `Select`.  Vous devez procéder ainsi, par exemple, lorsque vous souhaitez trier votre requête par champs non retournés dans le cadre du résultat.  
  
 L'ordre de tri croissant et décroissant d'un champ est déterminé par l'implémentation de l'interface <xref:System.IComparable> pour le type de données du champ.  Si le type de données n'implémente pas l'interface <xref:System.IComparable>, l'ordre de tri est ignoré.  
  
## Exemple  
 L'expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `book` pour la collection `books`.  La clause `Order By` trie le résultat de la requête par prix et par ordre croissant \(par défaut\).  Les livres de prix identique sont triés par titre et par ordre croissant.  La clause `Select` sélectionne les propriétés `Title` et `Price` en tant que valeurs retournées par la requête.  
  
 [!code-vb[VbSimpleQuerySamples#24](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_1.vb)]  
  
## Exemple  
 L'expression de requête suivante utilise la clause `Order By` pour trier le résultat de la requête par prix et par ordre décroissant.  Les livres de prix identique sont triés par titre et par ordre croissant.  
  
 [!code-vb[VbSimpleQuerySamples#25](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_2.vb)]  
  
## Exemple  
 L'expression de requête suivante utilise une clause `Select` pour sélectionner le titre du livre, son prix, sa date de publication et son auteur.  Elle renseigne alors les champs `Title`, `Price`, `PublishDate`et `Author` de la variable de portée pour la nouvelle portée.  La clause `Order By` classe la nouvelle variable de portée par nom d'auteur, titre de livre, puis par prix.  Chaque colonne est triée dans l'ordre par défaut \(croissant\).  
  
 [!code-vb[VbSimpleQuerySamples#26](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/order-by-clause_3.vb)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [Select Clause](../../../visual-basic/language-reference/queries/select-clause.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)