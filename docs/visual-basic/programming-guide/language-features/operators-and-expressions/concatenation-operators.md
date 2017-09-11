---
title: "Opérateurs de concaténation dans Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- '& operator [Visual Basic], concatenation'
- concatenation operators
- operators [Visual Basic], concatenation
- Visual Basic code, operators
- + operator [Visual Basic], concatenation
- concatenation operators, Visual Basic strings
ms.assetid: e59908c3-89e0-41ae-933d-3e8826c16a04
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f255e168b9eb794ef846e0cc18dbbdba5941bec5
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="concatenation-operators-in-visual-basic"></a><span data-ttu-id="a2c5a-102">Opérateurs de concaténation (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a2c5a-102">Concatenation Operators in Visual Basic</span></span>
<span data-ttu-id="a2c5a-103">Les opérateurs de concaténation joignent plusieurs chaînes en une seule.</span><span class="sxs-lookup"><span data-stu-id="a2c5a-103">Concatenation operators join multiple strings into a single string.</span></span> <span data-ttu-id="a2c5a-104">Il existe deux opérateurs de concaténation, `+` et `&`.</span><span class="sxs-lookup"><span data-stu-id="a2c5a-104">There are two concatenation operators, `+` and `&`.</span></span> <span data-ttu-id="a2c5a-105">Les deux effectuent l'opération de concaténation de base, comme le montre l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a2c5a-105">Both carry out the basic concatenation operation, as the following example shows.</span></span>  
  
```vb
Dim x As String = "Mic" & "ro" & "soft" 
Dim y As String = "Mic" + "ro" + "soft" 
' The preceding statements set both x and y to "Microsoft".
```  
  
 <span data-ttu-id="a2c5a-106">Ces opérateurs peuvent également concaténer les variables `String`, comme illustré ici.</span><span class="sxs-lookup"><span data-stu-id="a2c5a-106">These operators can also concatenate `String` variables, as the following example shows.</span></span>  
  
 <span data-ttu-id="a2c5a-107">[!code-vb[VbVbalrOperators&#76;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a2c5a-107">[!code-vb[VbVbalrOperators#76](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operators_1.vb)]</span></span>  
  
## <a name="differences-between-the-two-concatenation-operators"></a><span data-ttu-id="a2c5a-108">Différences entre ces deux opérateurs de concaténation</span><span class="sxs-lookup"><span data-stu-id="a2c5a-108">Differences Between the Two Concatenation Operators</span></span>  
 <span data-ttu-id="a2c5a-109">Le [opérateur +](../../../../visual-basic/language-reference/operators/addition-operator.md) a pour objectif principal d’ajouter deux nombres.</span><span class="sxs-lookup"><span data-stu-id="a2c5a-109">The [+ Operator](../../../../visual-basic/language-reference/operators/addition-operator.md) has the primary purpose of adding two numbers.</span></span> <span data-ttu-id="a2c5a-110">Toutefois, il peut également concaténer des opérandes numériques avec des opérandes de chaîne.</span><span class="sxs-lookup"><span data-stu-id="a2c5a-110">However, it can also concatenate numeric operands with string operands.</span></span> <span data-ttu-id="a2c5a-111">Le `+` opérateur comporte un ensemble complexe de règles qui déterminent s’il faut ajouter, concaténer, signaler une erreur du compilateur ou lever une exécution <xref:System.InvalidCastException>exception.</xref:System.InvalidCastException></span><span class="sxs-lookup"><span data-stu-id="a2c5a-111">The `+` operator has a complex set of rules that determine whether to add, concatenate, signal a compiler error, or throw a run-time <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="a2c5a-112">Le [s’opérateur](../../../../visual-basic/language-reference/operators/concatenation-operator.md) est défini uniquement pour `String` opérandes et il étend toujours ses opérandes à `String`, quelle que soit la valeur de `Option Strict`.</span><span class="sxs-lookup"><span data-stu-id="a2c5a-112">The [& Operator](../../../../visual-basic/language-reference/operators/concatenation-operator.md) is defined only for `String` operands, and it always widens its operands to `String`, regardless of the setting of `Option Strict`.</span></span> <span data-ttu-id="a2c5a-113">L'opérateur `&` est recommandé pour la concaténation de chaîne car il est exclusivement défini pour les chaînes et limite les risques de conversion inattendue.</span><span class="sxs-lookup"><span data-stu-id="a2c5a-113">The `&` operator is recommended for string concatenation because it is defined exclusively for strings and reduces your chances of generating an unintended conversion.</span></span>  
  
## <a name="performance-string-and-stringbuilder"></a><span data-ttu-id="a2c5a-114">Performance : String et StringBuilder</span><span class="sxs-lookup"><span data-stu-id="a2c5a-114">Performance: String and StringBuilder</span></span>  
 <span data-ttu-id="a2c5a-115">Si vous effectuez un nombre important de manipulations sur une chaîne, telles que des concaténations, des suppressions et des remplacements, vos performances peuvent tirer profit de la <xref:System.Text.StringBuilder>classe dans le <xref:System.Text>espace de noms.</xref:System.Text> </xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="a2c5a-115">If you do a significant number of manipulations on a string, such as concatenations, deletions, and replacements, your performance might profit from the <xref:System.Text.StringBuilder> class in the <xref:System.Text> namespace.</span></span> <span data-ttu-id="a2c5a-116">Elle prend une instruction supplémentaire pour créer et initialiser un <xref:System.Text.StringBuilder>objet et une autre instruction pour convertir sa valeur finale à un `String`, mais vous pouvez effectuer une récupération parce que <xref:System.Text.StringBuilder>peut s’exécuter plus rapidement.</xref:System.Text.StringBuilder> </xref:System.Text.StringBuilder></span><span class="sxs-lookup"><span data-stu-id="a2c5a-116">It takes an extra instruction to create and initialize a <xref:System.Text.StringBuilder> object, and another instruction to convert its final value to a `String`, but you might recover this time because <xref:System.Text.StringBuilder> can perform faster.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2c5a-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a2c5a-117">See Also</span></span>  
 <span data-ttu-id="a2c5a-118">[Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="a2c5a-118">[Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="a2c5a-119"> [Types de méthodes de Manipulation de chaînes en Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md) </span><span class="sxs-lookup"><span data-stu-id="a2c5a-119"> [Types of String Manipulation Methods in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/types-of-string-manipulation-methods.md) </span></span>  
<span data-ttu-id="a2c5a-120"> [Opérateurs arithmétiques en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="a2c5a-120"> [Arithmetic Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md) </span></span>  
<span data-ttu-id="a2c5a-121"> [Opérateurs de comparaison en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span><span class="sxs-lookup"><span data-stu-id="a2c5a-121"> [Comparison Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md) </span></span>  
<span data-ttu-id="a2c5a-122"> [Opérateurs logiques et au niveau du bit en Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span><span class="sxs-lookup"><span data-stu-id="a2c5a-122"> [Logical and Bitwise Operators in Visual Basic](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)</span></span>
