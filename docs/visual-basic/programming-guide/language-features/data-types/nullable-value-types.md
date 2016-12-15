---
title: "Nullable Value Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Nullable"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "nullable types [Visual Basic]"
  - "? [Visual Basic]"
  - "types [Visual Basic], nullable"
  - "nullable types"
  - "data types [Visual Basic], nullable"
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nullable Value Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Vous utilisez parfois un type valeur dont la valeur n'est pas définie dans certains cas.  Un champ de base de données doit parfois distinguer entre une valeur assignée explicite et l'absence de valeur assignée.  Les types valeur peuvent être étendus pour accepter leurs valeurs normales ou une valeur null.  Cette extension est appelée *type Nullable*.  
  
 Chaque type Nullable est construit à partir de la structure <xref:System.Nullable%601> générique.  Prenons une base de données qui assure le suivi des activités professionnelles.  L'exemple suivant construit un type `Boolean` nullable et déclare une variable de ce type.  Vous pouvez écrire la déclaration de trois manières différentes:  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 La variable `ridesBusToWork` peut contenir la valeur `True`, la valeur `False` ou aucune valeur.  Sa valeur par défaut initiale n'est pas définie, ce qui signifie, dans ce cas, que les informations n'ont pas encore été obtenues pour cette personne.  E revanche, `False` peut indiquer que les informations ont été obtenues et que la personne ne prend pas le bus pour aller au travail.  
  
 Vous pouvez déclarer des variables et des propriétés avec des types Nullables, et vous pouvez déclarer un tableau avec des éléments d'un type nullable.  Vous pouvez déclarer des procédures avec des types nullables comme paramètres, et vous pouvez retourner un type Nullable à partir d'une procédure `Function`.  
  
 Vous ne pouvez pas construire un type Nullable sur un type référence, par exemple un tableau, une `String` ou une classe.  Le type sous\-jacent doit être un type valeur.  Pour plus d'informations, consultez [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
## Utilisation d'une variable de type Nullable  
 Les membres les plus importants d'un type Nullable sont ses propriétés <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A>.  Pour une variable d'un type Nullable, <xref:System.Nullable%601.HasValue%2A> vous indique si la variable contient une valeur définie.  Si <xref:System.Nullable%601.HasValue%2A> a la valeur `True`, vous pouvez lire la valeur de <xref:System.Nullable%601.Value%2A>.  Notez que <xref:System.Nullable%601.HasValue%2A> et <xref:System.Nullable%601.Value%2A> sont des propriétés `ReadOnly`.  
  
### Valeurs par défaut  
 Lorsque vous déclarez une variable avec un type Nullable, sa propriété <xref:System.Nullable%601.HasValue%2A> a la valeur par défaut `False`.  Cela signifie que par défaut, la variable n'a aucune valeur définie, au lieu de la valeur par défaut de son type valeur sous\-jacent.  Dans l'exemple suivant, la variable `numberOfChildren` n'a initialement aucune valeur définie, même si la valeur par défaut du type `Integer` est 0.  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 Une valeur null est utile pour indiquer une valeur non définie ou inconnue.  Si `numberOfChildren` a été déclaré comme `Integer`, aucune valeur ne peut indiquer que les informations ne sont pas actuellement disponibles.  
  
### Stockage de valeurs  
 Vous stockez normalement une valeur dans une variable ou une propriété de type Nullable.  L'exemple suivant assigne une valeur à la variable `numberOfChildren` déclarée dans l'exemple précédent.  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 Si une variable ou une propriété d'un type Nullable contient une valeur définie, vous pouvez faire en sorte qu'elle rétablisse son état initial, c'est\-à\-dire sans valeur assignée.  Pour ce faire, affectez `Nothing` à la variable ou la propriété, comme indiqué dans l'exemple suivant.  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  Bien que vous puissiez assigner `Nothing` à une variable de type Nullable, vous ne pouvez pas le tester pour `Nothing` en utilisant le signe égal.  Une comparaison qui utilise le signe égal, `someVar = Nothing`, évalue toujours à `Nothing`.  Vous pouvez tester la propriété <xref:System.Nullable%601.HasValue%2A> de la variable pour `False` ou tester en utilisant l'opérateur `Is` ou `IsNot`.  
  
### Récupération de valeurs  
 Pour récupérer la valeur d'une variable d'un type Nullable, vous devez d'abord tester sa propriété <xref:System.Nullable%601.HasValue%2A> pour confirmer qu'une valeur lui est assignée.  Si vous essayez de lire la valeur lorsque <xref:System.Nullable%601.HasValue%2A> a la valeur `False`, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] lève une exception <xref:System.InvalidOperationException>.  L'exemple suivant décrit la méthode recommandée pour lire la variable `numberOfChildren` des exemples précédents.  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## Comparaison de types Nullable  
 Lorsque des variables `Boolean` nullables sont utilisées dans des expressions booléennes, le résultat peut être `True`, `False` ou `Nothing`.  Ce qui suit constitue la table de vérité pour `And` et `Or`.  `b1` et `b2` ayant maintenant trois valeurs possibles, les combinaisons à évaluer sont au nombre de neuf.  
  
|b1|b2|b1 And b2|b1 Or b2|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 Lorsque la valeur d'une variable ou expression booléenne est `Nothing`, elle n'est ni `true` , ni `false`.  Prenons l'exemple suivant.  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 Dans cet exemple, `b1 And b2` prend la valeur `Nothing`.  En conséquence, la clause `Else` s'exécute dans chaque instruction `If` et le résultat est le suivant :  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  `AndAlso` et `OrElse`, qui utilisent l'évaluation de court\-circuit doivent évaluer leurs seconds opérandes lorsque le premier prend la valeur `Nothing`.  
  
## Propagation  
 Si l'un ou les deux opérandes d'une opération arithmétique, de comparaison, de décalage ou de type est nullable, le résultat de l'opération est également nullable.  Si les deux opérandes ont des valeurs différentes de `Nothing`, l'opération s'applique à des valeurs sous\-jacentes des opérandes, comme si ni l'un ni l'autre n'étaient Nullable.  Dans l'exemple qui suit, les variables `compare1` et `sum1` sont typées implicitement.  Si vous arrêtez le pointeur de la souris sur ces variables, vous voyez que le compilateur déduit des types Nullable pour les deux variables.  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 Si l'un ou les deux opérandes ont une valeur de `Nothing`, le résultat est `Nothing`.  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## Utilisation de types Nullable avec des données  
 Une base de données est l'un des emplacements les plus importants pour utiliser des types Nullable.  Tous les objets de base de données ne prennent pas en charge actuellement les types Nullable, contrairement aux adaptateurs de table générés par le concepteur.  Consultez « Prise en charge des types Nullable par le TableAdapter » dans [Vue d'ensemble de TableAdapter](/visual-studio/data-tools/tableadapter-overview).  
  
## Voir aussi  
 <xref:System.InvalidOperationException>   
 <xref:System.Nullable%601.HasValue%2A>   
 [Utilisation de types Nullable](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)   
 [Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Vue d'ensemble de TableAdapter](/visual-studio/data-tools/tableadapter-overview)   
 [If Operator](../../../../visual-basic/language-reference/operators/if-operator.md)   
 [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)   
 [Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md)