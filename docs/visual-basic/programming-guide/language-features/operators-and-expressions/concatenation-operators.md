---
title: "Opérateurs de concaténation (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators [Visual Basic]
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators [Visual Basic]
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3a444cca76fbc41807b0c8b69bcbaedbd75c36eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="ca959-102">Opérateurs de concaténation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ca959-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="ca959-103">Les opérateurs de concaténation joignent plusieurs chaînes en une seule.</span><span class="sxs-lookup"><span data-stu-id="ca959-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="ca959-104">Il existe deux opérateurs de concaténation, `+` et `&`.</span><span class="sxs-lookup"><span data-stu-id="ca959-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="ca959-105">Les deux effectuent l'opération de concaténation de base, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="ca959-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="ca959-106">Ces opérateurs peuvent également concaténer les variables `String`, comme illustré ici.</span><span class="sxs-lookup"><span data-stu-id="ca959-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="ca959-107">Différences entre ces deux opérateurs de concaténation</span><span class="sxs-lookup"><span data-stu-id="ca959-107">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="ca959-108">Le [opérateur +](../../../../visual-basic/language-reference/operators/addition-operator.md) a pour objectif principal d’ajouter deux nombres.</span><span class="sxs-lookup"><span data-stu-id="ca959-108">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="ca959-109">Toutefois, il peut également concaténer des opérandes numériques avec des opérandes de chaîne.</span><span class="sxs-lookup"><span data-stu-id="ca959-109">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="ca959-110">L'opérateur `+` comporte un ensemble complexe de règles qui déterminent s'il faut ajouter, concaténer, signaler une erreur du compilateur ou lever une exception <xref:System.InvalidCastException> d'exécution.</span><span class="sxs-lookup"><span data-stu-id="ca959-110">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="ca959-111">Le [& opérateur](../../../../visual-basic/language-reference/operators/concatenation-operator.md) est défini uniquement pour `String` opérandes et il toujours s’étend ses opérandes `String`, quel que soit le paramètre de `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="ca959-111">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="ca959-112">L'opérateur `&` est recommandé pour la concaténation de chaîne car il est exclusivement défini pour les chaînes et limite les risques de conversion inattendue.</span><span class="sxs-lookup"><span data-stu-id="ca959-112">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="ca959-113">Performance : String et StringBuilder</span><span class="sxs-lookup"><span data-stu-id="ca959-113">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="ca959-114">Si vous effectuez un nombre important de manipulations sur une chaîne, telles que des concaténations, suppressions et remplacements, vos performances peuvent s'améliorer avec la classe <xref:System.Text.StringBuilder> de l'espace de noms <xref:System.Text>.</span><span class="sxs-lookup"><span data-stu-id="ca959-114">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="ca959-115">Elle prend une instruction supplémentaire pour créer et initialiser un objet <xref:System.Text.StringBuilder>, et une autre instruction pour convertir sa valeur finale en une `String`, mais vous pouvez rattraper le retard induit car <xref:System.Text.StringBuilder> peut s'exécuter plus rapidement.</span><span class="sxs-lookup"><span data-stu-id="ca959-115">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca959-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ca959-116">See Also</span></span>  
 [<span data-ttu-id="ca959-117">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="ca959-117">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="ca959-118">Types de méthodes de Manipulation de chaînes en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca959-118">Types of String Manipulation Methods in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md)  
 [<span data-ttu-id="ca959-119">Opérateurs arithmétiques en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca959-119">Arithmetic Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [<span data-ttu-id="ca959-120">Opérateurs de comparaison en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca959-120">Comparison Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="ca959-121">Opérateurs logiques et au niveau du bit en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ca959-121">Logical and Bitwise Operators in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
