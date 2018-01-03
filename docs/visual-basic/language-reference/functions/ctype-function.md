---
title: Fonction CType (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d804ce75929592675068fdc434a1ba7429fa5373
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="ctype-function-visual-basic"></a>Fonction CType (Visual Basic)
Retourne le résultat d’une conversion explicite d’une expression dans un type de données spécifié, objet, structure, classe ou une interface.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a>Composants  
 `expression`  
 Toute expression valide. Si la valeur de `expression` est en dehors de la plage autorisée par `typename`, Visual Basic lève une exception.  
  
 `typename`  
 Toute expression qui est autorisée dans un `As` clause dans un `Dim` instruction, autrement dit, le nom de n’importe quel type de données objet, structure, classe ou interface.  
  
## <a name="remarks"></a>Notes  
  
> [!TIP]
>  Vous pouvez également utiliser les fonctions suivantes pour effectuer une conversion de type :  
>   
>  -   Fonctions de conversion de type comme `CByte`, `CDbl`, et `CInt` qui effectuer une conversion vers un type de données spécifique. Pour plus d’informations, consultez [les fonctions de Conversion de Type](../../../visual-basic/language-reference/functions/type-conversion-functions.md).  
> -   [Opérateur DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) ou [opérateur TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md). Ces opérateurs requièrent qu’un type hériter ou implémenter l’autre type. Elles peuvent fournir un peu de meilleures performances que `CType` lors de la conversion vers et depuis le `Object` type de données.  
  
 `CType`est en ligne compilé, ce qui signifie que le code de conversion fait partie du code qui évalue l’expression. Dans certains cas, le code s’exécute plus rapidement, car aucune procédure n’est appelées pour effectuer la conversion.  
  
 Si aucune conversion n’est définie à partir de `expression` à `typename` (par exemple, de `Integer` à `Date`), Visual Basic affiche un message d’erreur de compilation.  
  
 Si une conversion échoue au moment de l’exécution, l’exception appropriée est levée. Si une conversion restrictive échoue, un <xref:System.OverflowException> est le résultat le plus courant. Si la conversion n’est pas définie, un <xref:System.InvalidCastException> dans levée. Par exemple, cela peut se produire si `expression` est de type `Object` et son type au moment de l’exécution n’a pas de conversion `typename`.  
  
 Si le type de données de `expression` ou `typename` est une classe ou une structure que vous avez définie, vous pouvez définir `CType` sur cette classe ou structure comme un opérateur de conversion. Cela rend `CType` agissent comme un *opérateur surchargé*. Si vous faites cela, vous pouvez contrôler le comportement des conversions vers et à partir de votre classe ou structure, y compris les exceptions pouvant être levées.  
  
## <a name="overloading"></a>Surcharge  
 Le `CType` opérateur peut également être surchargé sur une classe ou structure définie en dehors de votre code. Si votre code convertit vers ou à partir d’une classe ou une structure, veillez à ce que vous comprenez le comportement de son `CType` opérateur. Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="converting-dynamic-objects"></a>Conversion d’objets dynamiques  
 Conversions de types d’objets dynamiques sont effectuées par les conversions dynamiques définies par l’utilisateur qui utilisent la <xref:System.Dynamic.DynamicObject.TryConvert%2A> ou <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> méthodes. Si vous travaillez avec des objets dynamiques, utilisez le <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> méthode pour convertir l’objet dynamique.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant utilise le `CType` fonction pour convertir une expression pour la `Single` type de données.  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 Pour obtenir des exemples supplémentaires, consultez [Conversions implicites et explicites](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [Fonctions de conversion de types](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Fonctions de conversion](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Operator (instruction)](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Guide pratique : définir un opérateur de conversion](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [Conversion de type dans le .NET Framework](../../../standard/base-types/type-conversion.md)
