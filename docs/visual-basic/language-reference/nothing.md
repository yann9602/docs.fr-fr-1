---
title: "Nothing (Visual Basic) | Microsoft Docs"
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
  - "Nothing"
  - "vb.Nothing"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Nothing keyword"
  - "Nothing keyword, syntax"
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: 31
caps.handback.revision: 31
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Nothing (Visual Basic)
[!INCLUDE[vs2017banner](../../csharp/includes/vs2017banner.md)]

Représente la valeur par défaut d'un type de données.  Pour les types référence, la valeur par défaut est la référence d' `null` .  Pour les types valeur, la valeur par défaut varie selon que le type valeur est nullable.  
  
> [!NOTE]
>  Pour les types valeur non Null, `Nothing` en Visual Basic et l' `null` en c\#.  En Visual Basic, si vous définissez une variable d'un type valeur non Null à `Nothing`, la variable est définie à la valeur par défaut pour son type déclaré.  En c\#, si vous assignez une variable d'un type valeur non Null à `null`, une erreur de compilation se produit.  
  
## Notes  
 `Nothing` représente la valeur par défaut d'un type de données.  La valeur par défaut dépend de si la variable est d'un type valeur ou un type référence.  
  
 une variable d'un *type valeur* contient directement sa valeur.  Les types valeur incluent tous les types de données numériques, `Boolean`, `Char`, `Date`, toutes les structures, et toutes les énumérations.  Une variable *d'un type référence* enregistre une référence à une instance de l'objet en mémoire.  Les types référence incluent des classes, des tableaux, des délégués, et les chaînes.  Pour plus d'informations, consultez [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 si une variable est d'un type valeur, le comportement d' `Nothing` dépend de si la variable est d'un type de données nullable.  Pour représenter un type valeur nullable, ajoutez un modificateur d' `?` au nom de type.  L'assignation `Nothing` à une variable nullable définit la valeur à `null`.  Pour plus d'informations et d'exemples, consultez [Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Si une variable est d'un type valeur qui n'est pas nullable, lui assigner `Nothing` le définit la valeur par défaut pour son type déclaré.  Si ce type contient des membres de variable, ils ont tous leurs valeurs par défaut.  L'exemple suivant illustre cela pour les types scalaires.  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 si une variable est d'un type référence, l'assignant à `Nothing` aux ensembles variables à une référence d' `null` du type de la variable.  Une variable qui a une référence d' `null` n'est pas associé à un objet.  C'est ce qu'illustre l'exemple suivant.  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 En vérifiant si une variable de référence \(ou type valeur nullable\) est `null`, n'utilisez pas `= Nothing` ou `<> Nothing`.  Utilisez toujours `Is Nothing` ou `IsNot Nothing`.  
  
 Pour les chaînes en Visual Basic, la chaîne vide égale `Nothing`.  Par conséquent, `"" = Nothing` est true.  
  
 L'exemple suivant montre les comparaisons qui utilisent les opérateurs `Is` et `IsNot`.  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Si vous déclarez une variable sans utiliser de clause `As` et que vous la définissez sur `Nothing`, la variable a un type `Object`.  Un exemple est `Dim something = Nothing`.  Une erreur de compilation se produit dans ce cas lorsque `Option Strict` est activé et `Option Infer` est désactivé.  
  
 Lorsque vous assignez `Nothing` à une variable objet, cette dernière ne fait plus référence à une instance d'objet.  Si la variable avait fait référence à une instance au préalable, l'assignation de `Nothing` à la variable ne met pas fin à l'instance.  L'instance se termine, et les ressources mémoire et système qui lui sont associées sont libérées uniquement lorsque le garbage collector \(GC\) détecte l'absence de toute référence active restante.  
  
 `Nothing` diffère de l'objet d' <xref:System.DBNull> , qui représente une variante non initialisée ou une colonne inexistante de base de données.  
  
## Voir aussi  
 [Dim Statement](../../visual-basic/language-reference/statements/dim-statement.md)   
 [Object Lifetime: How Objects Are Created and Destroyed](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Lifetime in Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)   
 [Is Operator](../../visual-basic/language-reference/operators/is-operator.md)   
 [IsNot Operator](../../visual-basic/language-reference/operators/isnot-operator.md)   
 [Nullable Value Types](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)