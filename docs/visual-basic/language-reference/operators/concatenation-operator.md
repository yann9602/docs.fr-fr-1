---
title: "&amp;Opérateur (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 76c8fc52a518dfe7850a5680b7d4f06f3d09bf73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="7001e-102">&amp;Opérateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7001e-102">&amp; Operator (Visual Basic)</span></span>
<span data-ttu-id="7001e-103">Génère une concaténation de chaîne de deux expressions.</span><span class="sxs-lookup"><span data-stu-id="7001e-103">Generates a string concatenation of two expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7001e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7001e-104">Syntax</span></span>  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="7001e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="7001e-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="7001e-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7001e-106">Required.</span></span> <span data-ttu-id="7001e-107">N’importe quel `String` ou `Object` variable.</span><span class="sxs-lookup"><span data-stu-id="7001e-107">Any `String` or `Object` variable.</span></span>  
  
 `expression1`  
 <span data-ttu-id="7001e-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7001e-108">Required.</span></span> <span data-ttu-id="7001e-109">Toute expression avec un type de données qui s’étend à `String`.</span><span class="sxs-lookup"><span data-stu-id="7001e-109">Any expression with a data type that widens to `String`.</span></span>  
  
 `expression2`  
 <span data-ttu-id="7001e-110">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7001e-110">Required.</span></span> <span data-ttu-id="7001e-111">Toute expression avec un type de données qui s’étend à `String`.</span><span class="sxs-lookup"><span data-stu-id="7001e-111">Any expression with a data type that widens to `String`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7001e-112">Remarques</span><span class="sxs-lookup"><span data-stu-id="7001e-112">Remarks</span></span>  
 <span data-ttu-id="7001e-113">Si le type de données de `expression1` ou `expression2` n’est pas `String` mais s’étend à `String`, il est converti en `String`.</span><span class="sxs-lookup"><span data-stu-id="7001e-113">If the data type of `expression1` or `expression2` is not `String` but widens to `String`, it is converted to `String`.</span></span> <span data-ttu-id="7001e-114">Si un des types de données ne s’étend pas à `String`, le compilateur génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="7001e-114">If either of the data types does not widen to `String`, the compiler generates an error.</span></span>  
  
 <span data-ttu-id="7001e-115">Type de données de `result` est `String`.</span><span class="sxs-lookup"><span data-stu-id="7001e-115">The data type of `result` is `String`.</span></span> <span data-ttu-id="7001e-116">Si un ou les deux expressions ont [rien](../../../visual-basic/language-reference/nothing.md) ou avoir la valeur <xref:System.DBNull.Value?displayProperty=nameWithType>, elles sont traitées comme une chaîne avec la valeur « ».</span><span class="sxs-lookup"><span data-stu-id="7001e-116">If one or both expressions evaluate to [Nothing](../../../visual-basic/language-reference/nothing.md) or have a value of <xref:System.DBNull.Value?displayProperty=nameWithType>, they are treated as a string with a value of "".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7001e-117">Le `&` opérateur peut être *surchargé*, ce qui signifie qu’une classe ou structure peut redéfinir son comportement lorsqu’un opérande a le type de cette classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="7001e-117">The `&` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7001e-118">Si votre code utilise cet opérateur sur une telle classe ou structure, assurez-vous que vous comprenez son comportement redéfini.</span><span class="sxs-lookup"><span data-stu-id="7001e-118">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7001e-119">Pour plus d’informations, consultez [procédures d’opérateur](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7001e-119">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7001e-120">Le caractère esperluette (&) peuvent également servir à identifier des variables en tant que type `Long`.</span><span class="sxs-lookup"><span data-stu-id="7001e-120">The ampersand (&) character can also be used to identify variables as type `Long`.</span></span> <span data-ttu-id="7001e-121">Pour plus d’informations, consultez [caractères de Type](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span><span class="sxs-lookup"><span data-stu-id="7001e-121">For more information, see [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7001e-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="7001e-122">Example</span></span>  
 <span data-ttu-id="7001e-123">Cet exemple utilise le `&` opérateur pour forcer la concaténation de chaîne.</span><span class="sxs-lookup"><span data-stu-id="7001e-123">This example uses the `&` operator to force string concatenation.</span></span> <span data-ttu-id="7001e-124">Le résultat est une valeur de chaîne représentant la concaténation de deux opérandes de chaîne.</span><span class="sxs-lookup"><span data-stu-id="7001e-124">The result is a string value representing the concatenation of the two string operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7001e-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7001e-125">See Also</span></span>  
 [<span data-ttu-id="7001e-126">&= (opérateur)</span><span class="sxs-lookup"><span data-stu-id="7001e-126">&= Operator</span></span>](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [<span data-ttu-id="7001e-127">opérateur de concaténation</span><span class="sxs-lookup"><span data-stu-id="7001e-127">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [<span data-ttu-id="7001e-128">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7001e-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="7001e-129">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="7001e-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="7001e-130">Opérateurs de concaténation dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7001e-130">Concatenation Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
