---
title: "Select Clause (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.QuerySelect"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Select statement"
  - "Select clause"
  - "queries [Visual Basic], Select"
ms.assetid: 27a3f61c-5960-4692-9b91-4d0c4b6178fe
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# Select Clause (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Définit le résultat d'une requête.  
  
## Syntaxe  
  
```  
Select [ var1 = ] fieldName1 [, [ var2 = ] fieldName2 [...] ]  
```  
  
## Composants  
 `var1`  
 Facultatif.  Alias pouvant être utilisé pour référencer les résultats de l'expression de colonne.  
  
 `fieldName1`  
 Obligatoire.  Nom du champ à retourner dans le résultat de la requête.  
  
## Notes  
 Vous pouvez utiliser la clause `Select` pour définir les résultats à retourner d'une requête.  Cela vous permet de définir les membres d'un nouveau type anonyme créé par une requête ou de cibler les membres d'un type nommé retourné par une requête.  La clause `Select` n'est pas obligatoire pour une requête.  Si aucune clause `Select` n'est spécifiée, la requête retournera un type en fonction de tous les membres des variables de portée identifiés pour la portée actuelle.  Pour plus d'informations, consultez [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  Lorsqu'une requête crée un type nommé, elle retourne un résultat de type <xref:System.Collections.Generic.IEnumerable%601> où `T` est le type créé.  
  
 La clause `Select` peut référencer toutes les variables de la portée actuelle.  Cela inclut des variables de portée identifiées dans la clause `From` \(ou dans les clauses `From`\).  Cela inclut également toutes les nouvelles variables créées avec un alias par les clauses `Aggregate`, `Let`, `Group By`ou `Group Join` ou les variables d'une clause `Select` précédente dans l'expression de requête.  La clause `Select` peut également inclure des valeurs statiques.  Par exemple, l'exemple de code suivant affiche une expression de requête dans laquelle la clause `Select` définit le résultat de la requête comme un nouveau type anonyme possédant quatre membres : `ProductName`, `Price`, `Discount` et `DiscountedPrice`.  Les valeurs membres `ProductName` et `Price` sont issues de la variable de portée du produit définie dans la clause `From`.  La valeur membre `DiscountedPrice` est calculée dans la clause `Let`.  Le membre `Discount` est une valeur statique.  
  
 [!code-vb[VbSimpleQuerySamples#27](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#27)]  
  
 La clause `Select` introduit un nouveau jeu de variables de portée pour les clauses de requête suivantes, et les variables de portée précédentes qui sont hors de portée.  La dernière clause `Select` d'une expression de requête détermine la valeur de retour de la requête.  Par exemple, la requête suivante retourne la Société et l'ID de commande pour chaque ordre de client dont le total dépasse 500.  La première clause `Select` identifie les variables de portée pour la clause `Where` et la deuxième clause `Select`.  La deuxième clause `Select` identifie les valeurs retournées par la requête comme un nouveau type anonyme.  
  
 [!code-vb[VbSimpleQuerySamples#28](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#28)]  
  
 Si la clause `Select` identifie un élément unique à retourner, l'expression de requête retourne une collection du type de cet élément unique.  Si la clause `Select` identifie des éléments multiples à retourner, l'expression de requête retourne une collection d'un nouveau type anonyme, en fonction des éléments sélectionnés.  Par exemple, les deux requêtes suivantes retournent des collections de deux types différents basés sur la clause `Select`.  La première requête retourne une collection de noms de société sous forme de chaînes.  La deuxième requête retourne une collection d'objets `Customer` remplie avec les noms de société et les adresses.  
  
 [!code-vb[VbSimpleQuerySamples#29](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#29)]  
  
## Exemple  
 L'expression de requête suivante utilise une clause `From` pour déclarer une variable de portée `cust` pour la collection `customers`.  La clause `Select` sélectionne le nom de client et la valeur d'ID et remplit les colonnes `CompanyName` et `CustomerID` de la nouvelle variable de portée.  L'instruction `For Each` effectue une boucle sur chaque objet retourné et affiche les colonnes `CompanyName` et `CustomerID` pour chaque enregistrement.  
  
 [!code-vb[VbSimpleQuerySamples#30](../../../visual-basic/language-reference/queries/codesnippet/visualbasic/VbSimpleQuerySamples/QuerySamples1.vb#30)]  
  
## Voir aussi  
 [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)   
 [Queries](../../../visual-basic/language-reference/queries/queries.md)   
 [From Clause](../../../visual-basic/language-reference/queries/from-clause.md)   
 [Where Clause](../../../visual-basic/language-reference/queries/where-clause.md)   
 [Order By Clause](../../../visual-basic/language-reference/queries/order-by-clause.md)   
 [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)