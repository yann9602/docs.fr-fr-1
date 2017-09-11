---
title: "Types de données en Visual Basic"
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
- data types [Visual Basic], declaring
- typing
- data types [Visual Basic]
- Visual Basic code, data types
- data types [Visual Basic], improving speed with
ms.assetid: 5e1b9aaf-c7ca-4b29-9b22-0e82ed8e85e2
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8b90a5e58d135a3769761ca431fd0c05f79e045f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="data-types-in-visual-basic"></a><span data-ttu-id="96d06-102">Types de données en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="96d06-102">Data Types in Visual Basic</span></span>
<span data-ttu-id="96d06-103">Le *type de données* d’un élément de programmation fait référence au type de données qu’il peut contenir et à la façon dont il stocke ces données.</span><span class="sxs-lookup"><span data-stu-id="96d06-103">The *data type* of a programming element refers to what kind of data it can hold and how it stores that data.</span></span> <span data-ttu-id="96d06-104">Les types de données s’appliquent à toutes les valeurs qui peuvent être stockées dans la mémoire de l’ordinateur ou qui participent à l’évaluation d’une expression.</span><span class="sxs-lookup"><span data-stu-id="96d06-104">Data types apply to all values that can be stored in computer memory or participate in the evaluation of an expression.</span></span> <span data-ttu-id="96d06-105">Chaque variable, littéral, constante, énumération, propriété, paramètre de procédure, argument de procédure et valeur de retour de procédure possède un type de données.</span><span class="sxs-lookup"><span data-stu-id="96d06-105">Every variable, literal, constant, enumeration, property, procedure parameter, procedure argument, and procedure return value has a data type.</span></span>  
  
## <a name="declared-data-types"></a><span data-ttu-id="96d06-106">Types de données déclarés</span><span class="sxs-lookup"><span data-stu-id="96d06-106">Declared Data Types</span></span>  
 <span data-ttu-id="96d06-107">Vous définissez un élément de programmation avec une instruction de déclaration et spécifiez son type de données avec la clause `As`.</span><span class="sxs-lookup"><span data-stu-id="96d06-107">You define a programming element with a declaration statement, and you specify its data type with the `As` clause.</span></span> <span data-ttu-id="96d06-108">Le tableau suivant présente les instructions que vous utilisez pour déclarer divers éléments.</span><span class="sxs-lookup"><span data-stu-id="96d06-108">The following table shows the statements you use to declare various elements.</span></span>  
  
|<span data-ttu-id="96d06-109">Élément de programmation</span><span class="sxs-lookup"><span data-stu-id="96d06-109">Programming element</span></span>|<span data-ttu-id="96d06-110">Déclaration de type de données</span><span class="sxs-lookup"><span data-stu-id="96d06-110">Data type declaration</span></span>|  
|-------------------------|---------------------------|  
|<span data-ttu-id="96d06-111">Variable</span><span class="sxs-lookup"><span data-stu-id="96d06-111">Variable</span></span>|<span data-ttu-id="96d06-112">Dans une [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)</span><span class="sxs-lookup"><span data-stu-id="96d06-112">In a [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)</span></span><br /><br /> <span data-ttu-id="96d06-113">`Dim`   `amount As Double`</span><span class="sxs-lookup"><span data-stu-id="96d06-113">`Dim`   `amount As Double`</span></span><br /><br /> <span data-ttu-id="96d06-114">`Static`   `yourName As String`</span><span class="sxs-lookup"><span data-stu-id="96d06-114">`Static`   `yourName As String`</span></span><br /><br /> <span data-ttu-id="96d06-115">`Public`   `billsPaid As Decimal = 0`</span><span class="sxs-lookup"><span data-stu-id="96d06-115">`Public`   `billsPaid As Decimal = 0`</span></span>|  
|<span data-ttu-id="96d06-116">Literal</span><span class="sxs-lookup"><span data-stu-id="96d06-116">Literal</span></span>|<span data-ttu-id="96d06-117">Avec un caractère de type de littéral ; consultez « Caractères de type de littéral » dans [Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span><span class="sxs-lookup"><span data-stu-id="96d06-117">With a literal type character; see "Literal Type Characters" in [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)</span></span><br /><br /> <span data-ttu-id="96d06-118">`Dim searchChar As Char = "."`  `C`</span><span class="sxs-lookup"><span data-stu-id="96d06-118">`Dim searchChar As Char = "."`  `C`</span></span>|  
|<span data-ttu-id="96d06-119">Constante</span><span class="sxs-lookup"><span data-stu-id="96d06-119">Constant</span></span>|<span data-ttu-id="96d06-120">Dans une [instruction Const](../../../../visual-basic/language-reference/statements/const-statement.md)</span><span class="sxs-lookup"><span data-stu-id="96d06-120">In a [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md)</span></span><br /><br /> <span data-ttu-id="96d06-121">`Const`   `modulus As Single = 4.17825F`</span><span class="sxs-lookup"><span data-stu-id="96d06-121">`Const`   `modulus As Single = 4.17825F`</span></span>|  
|<span data-ttu-id="96d06-122">Énumération</span><span class="sxs-lookup"><span data-stu-id="96d06-122">Enumeration</span></span>|<span data-ttu-id="96d06-123">Dans une instruction [Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="96d06-123">In an [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)</span></span><br /><br /> <span data-ttu-id="96d06-124">`Public`   `Enum`   `colors`</span><span class="sxs-lookup"><span data-stu-id="96d06-124">`Public`   `Enum`   `colors`</span></span>|  
|<span data-ttu-id="96d06-125">Propriété</span><span class="sxs-lookup"><span data-stu-id="96d06-125">Property</span></span>|<span data-ttu-id="96d06-126">Dans une [instruction Property](../../../../visual-basic/language-reference/statements/property-statement.md)</span><span class="sxs-lookup"><span data-stu-id="96d06-126">In a [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md)</span></span><br /><br /> <span data-ttu-id="96d06-127">`Property`   `region() As String`</span><span class="sxs-lookup"><span data-stu-id="96d06-127">`Property`   `region() As String`</span></span>|  
|<span data-ttu-id="96d06-128">Paramètre de procédure</span><span class="sxs-lookup"><span data-stu-id="96d06-128">Procedure parameter</span></span>|<span data-ttu-id="96d06-129">Dans une [instruction Sub](../../../../visual-basic/language-reference/statements/sub-statement.md), une [instruction Function](../../../../visual-basic/language-reference/statements/function-statement.md) ou une [instruction Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)</span><span class="sxs-lookup"><span data-stu-id="96d06-129">In a [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md), [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md), or [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)</span></span><br /><br /> <span data-ttu-id="96d06-130">`Sub addSale(ByVal`   `amount`   `As Double)`</span><span class="sxs-lookup"><span data-stu-id="96d06-130">`Sub addSale(ByVal`   `amount`   `As Double)`</span></span>|  
|<span data-ttu-id="96d06-131">Argument de procédure</span><span class="sxs-lookup"><span data-stu-id="96d06-131">Procedure argument</span></span>|<span data-ttu-id="96d06-132">Dans le code appelant ; chaque argument est un élément de programmation qui a déjà été déclaré, ou une expression qui contient des éléments déclarés</span><span class="sxs-lookup"><span data-stu-id="96d06-132">In the calling code; each argument is a programming element that has already been declared, or an expression containing declared elements</span></span><br /><br /> <span data-ttu-id="96d06-133">`subString = Left(`  `inputString`  `,`   `5`  `)`</span><span class="sxs-lookup"><span data-stu-id="96d06-133">`subString = Left(`  `inputString`  `,`   `5`  `)`</span></span>|  
|<span data-ttu-id="96d06-134">Valeur de retour de procédure</span><span class="sxs-lookup"><span data-stu-id="96d06-134">Procedure return value</span></span>|<span data-ttu-id="96d06-135">Dans une [instruction Function](../../../../visual-basic/language-reference/statements/function-statement.md) ou une [instruction Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)</span><span class="sxs-lookup"><span data-stu-id="96d06-135">In a [Function Statement](../../../../visual-basic/language-reference/statements/function-statement.md) or [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)</span></span><br /><br /> <span data-ttu-id="96d06-136">`Function convert(ByVal b As Byte)`   `As String`</span><span class="sxs-lookup"><span data-stu-id="96d06-136">`Function convert(ByVal b As Byte)`   `As String`</span></span>|  
  
 <span data-ttu-id="96d06-137">Pour obtenir la liste des types de données Visual Basic, consultez [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span><span class="sxs-lookup"><span data-stu-id="96d06-137">For a list of Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96d06-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="96d06-138">See Also</span></span>  
 <span data-ttu-id="96d06-139">[Caractères de type](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-139">[Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md) </span></span>  
 <span data-ttu-id="96d06-140">[Types de données élémentaires](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-140">[Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md) </span></span>  
 <span data-ttu-id="96d06-141">[Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-141">[Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
 <span data-ttu-id="96d06-142">[Types génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-142">[Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md) </span></span>  
 <span data-ttu-id="96d06-143">[Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-143">[Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
 <span data-ttu-id="96d06-144">[Conversions de type en Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-144">[Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md) </span></span>  
 <span data-ttu-id="96d06-145">[Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-145">[Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
 <span data-ttu-id="96d06-146">[Tuples](tuples.md)   </span><span class="sxs-lookup"><span data-stu-id="96d06-146">[Tuples](tuples.md)   </span></span>  
 <span data-ttu-id="96d06-147">[Dépannage des types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-147">[Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
 <span data-ttu-id="96d06-148">[Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="96d06-148">[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
 [<span data-ttu-id="96d06-149">Utilisation efficace des types de données</span><span class="sxs-lookup"><span data-stu-id="96d06-149">Efficient Use of Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

