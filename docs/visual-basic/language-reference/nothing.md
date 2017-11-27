---
title: Nothing (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- Nothing
- vb.Nothing
helpviewer_keywords:
- Nothing keyword [Visual Basic]
- Nothing keyword [Visual Basic], syntax
ms.assetid: 06176e2d-bbf7-4a37-afaa-a86ad21ee99f
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6932fee01ec6f39f67fb1a26a9a5b5cbd47d9767
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nothing-visual-basic"></a>Nothing (Visual Basic)
Représente la valeur par défaut de n’importe quel type de données. Pour les types référence, la valeur par défaut est le `null` référence. Pour les types valeur, la valeur par défaut varie selon que le type de valeur est nullable.  
  
> [!NOTE]
>  Pour les types de valeur non nullable, `Nothing` en Visual Basic diffère `null` en c#. En Visual Basic, si vous définissez une variable d’un type valeur non nullable à `Nothing`, la variable est définie sur la valeur par défaut pour son type déclaré. En c#, si vous assignez une variable d’un type valeur non nullable à `null`, une erreur de compilation se produit.  
  
## <a name="remarks"></a>Remarques  
 `Nothing`représente la valeur par défaut d’un type de données. La valeur par défaut varie selon que la variable est d’un type valeur ou d’un type référence.  
  
 Une variable d’un *type valeur* directement contient sa valeur. Types valeur incluent tous les types de données numériques, `Boolean`, `Char`, `Date`, toutes les structures et toutes les énumérations. Une variable d’un *type référence* stocke une référence à une instance de l’objet en mémoire. Types référence incluent les classes, les tableaux, les délégués et les chaînes. Pour plus d'informations, consultez [Value Types and Reference Types](../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).  
  
 Si une variable est d’une valeur de type, le comportement de `Nothing` varie selon que la variable est un type nullable. Pour représenter un type valeur nullable, ajoutez un `?` modificateur au nom de type. Affectation `Nothing` à une variable nullable définit la valeur sur `null`. Pour plus d’informations et d’exemples, consultez [des Types valeur Nullable](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md).  
  
 Si une variable est d’un type valeur qui n’est pas nullable, affectation `Nothing` pour qu’il lui affecte la valeur par défaut pour son type déclaré. Si ce type contient des variables membres, ils sont tous définis sur leurs valeurs par défaut. L’exemple suivant illustre ce comportement pour les types scalaires.  
  
 [!code-vb[VbVbalrKeywords#7](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_1.vb)]  
  
 Si une variable est d’un type référence, l’assignation `Nothing` à la variable lui affecte un `null` référence de type de la variable. Une variable qui est définie sur une `null` référence n’est pas associée à n’importe quel objet. Cela est illustré par l'exemple suivant.  
  
 [!code-vb[VbVbalrKeywords#8](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_2.vb)]  
  
 Lors de la vérification si une référence (ou un type de valeur nullable) variable est `null`, n’utilisez pas `= Nothing` ou `<> Nothing`. Toujours utiliser `Is Nothing` ou `IsNot Nothing`.  
  
 Pour les chaînes en Visual Basic, la chaîne vide est égal à `Nothing`. Par conséquent, `"" = Nothing` a la valeur true.  
  
 L’exemple suivant montre les comparaisons qui utilisent la `Is` et `IsNot` opérateurs.  
  
 [!code-vb[VbVbalrKeywords#9](../../visual-basic/language-reference/codesnippet/VisualBasic/nothing_3.vb)]  
  
 Si vous déclarez une variable sans utiliser un `As` clause et affectez-lui la valeur `Nothing`, la variable a un type de `Object`. Est un exemple de ce `Dim something = Nothing`. Une erreur de compilation se produit dans ce cas lorsque `Option Strict` sur et `Option Infer` est désactivée.  
  
 Lorsque vous assignez `Nothing` à une variable objet, il ne fait plus référence à une instance d’objet. Si la variable avait fait référence précédemment à une instance, la valeur `Nothing` n’arrête pas l’instance elle-même. L’instance est arrêtée et les ressources mémoire et système qui lui sont libérés uniquement lorsque le garbage collector (GC) détecte qu’il n’y a aucune référence active restante.  
  
 `Nothing`diffère le <xref:System.DBNull> objet qui représente une variante non initialisée ou une colonne de base de données qui n’existe pas.  
  
## <a name="see-also"></a>Voir aussi  
 [Dim (instruction)](../../visual-basic/language-reference/statements/dim-statement.md)  
 [Durée de vie d’un objet : création et destruction des objets](../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 [Durée de vie dans Visual Basic](../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Is (opérateur)](../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot (opérateur)](../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Types valeur Nullable](../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
