---
title: "Comment : déclarer des énumérations (Visual Basic) | Documents Microsoft"
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
- declarations, enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: 24
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
ms.openlocfilehash: 7adaca7e7252ce7165a5fd27b5bc9c049388206c
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="e3d0b-102">Comment : déclarer des énumérations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3d0b-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="e3d0b-103">Vous créez une énumération avec la `Enum` instruction dans la section des déclarations d’une classe ou un module.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="e3d0b-104">Vous ne pouvez pas déclarer d’énumération dans une méthode.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="e3d0b-105">Pour spécifier le niveau d’accès approprié, utilisez `Private`, `Protected`, `Friend`, ou `Public`.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="e3d0b-106">Un `Enum` type possède un nom, un type sous-jacent et un ensemble de champs, chacun représentant une constante.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="e3d0b-107">Le nom doit être valide [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualificateur.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-107">The name must be a valid [!INCLUDE[vbprvblong](../../../../visual-basic/developing-apps/customizing-extending-my/includes/vbprvblong_md.md)] qualifier.</span></span> <span data-ttu-id="e3d0b-108">Le type sous-jacent doit être un des types d’entiers :`Byte`, `Short`, `Long` ou `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="e3d0b-109">`Integer` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-109">`Integer` is the default.</span></span> <span data-ttu-id="e3d0b-110">Les énumérations sont toujours fortement typées et ne sont pas interchangeables avec les types de nombre entier.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="e3d0b-111">Les énumérations ne peut pas avoir de valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="e3d0b-112">Si une énumération est assignée une valeur à virgule flottante `Option Strict On`, résulte d’une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="e3d0b-113">Si `Option Strict` est `Off`, la valeur est automatiquement convertie en la `Enum` type.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="e3d0b-114">Pour plus d’informations sur les noms et comment utiliser le `Imports` instruction pour rendre la qualification de noms inutiles, consultez [énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="e3d0b-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="e3d0b-115">Pour déclarer une énumération</span><span class="sxs-lookup"><span data-stu-id="e3d0b-115">To declare an enumeration</span></span>  
  
1.  <span data-ttu-id="e3d0b-116">Écrivez une déclaration qui inclut un niveau d’accès de code, le `Enum` (mot clé) et un nom valide, comme dans les exemples suivants, qui déclarent chacun un autre `Enum`.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     <span data-ttu-id="e3d0b-117">[!code-vb[VbEnumsTask n °&3;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="e3d0b-117">[!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]</span></span>  
  
2.  <span data-ttu-id="e3d0b-118">Définissez les constantes dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-118">Define the constants in the enumeration.</span></span> <span data-ttu-id="e3d0b-119">Par défaut, la première constante d’une énumération est initialisée à `0`, et les constantes suivantes sont initialisées à une valeur de plus que la constante précédente.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-119">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="e3d0b-120">Par exemple, l’énumération suivante, `Days`, contient une constante nommée `Sunday` avec la valeur `0`, une constante nommée `Monday` avec la valeur `1`, une constante nommée `Tuesday` avec la valeur de `2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-120">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     <span data-ttu-id="e3d0b-121">[!code-vb[VbEnumsTask n °&4;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="e3d0b-121">[!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]</span></span>  
  
3.  <span data-ttu-id="e3d0b-122">Vous pouvez affecter explicitement des valeurs à des constantes dans une énumération à l’aide d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-122">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="e3d0b-123">Vous pouvez affecter une valeur entière, y compris les nombres négatifs.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-123">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="e3d0b-124">Par exemple, vous souhaiterez peut-être constantes avec des valeurs inférieures à zéro pour représenter des conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-124">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="e3d0b-125">Dans l’énumération suivante, la constante `Invalid` est affectée de la valeur `–1`et la constante `Sunday` reçoit la valeur `0`.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-125">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="e3d0b-126">Car il s’agit de la première constante de l’énumération, `Saturday` est également initialisée à la valeur `0`.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-126">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="e3d0b-127">La valeur de `Monday` est `1` (plus que la valeur de `Sunday`), la valeur de `Tuesday` est `2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-127">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     <span data-ttu-id="e3d0b-128">[!code-vb[VbEnumsTask n °&5;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="e3d0b-128">[!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]</span></span>  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="e3d0b-129">Pour déclarer une énumération en tant que type explicite</span><span class="sxs-lookup"><span data-stu-id="e3d0b-129">To declare an enumeration as an explicit type</span></span>  
  
-   <span data-ttu-id="e3d0b-130">Spécifiez le type de l’énumération à l’aide de la `As` clause, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="e3d0b-130">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     <span data-ttu-id="e3d0b-131">[!code-vb[VbEnumsTask n °&6;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="e3d0b-131">[!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3d0b-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e3d0b-132">See Also</span></span>  
 <span data-ttu-id="e3d0b-133">[Énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="e3d0b-133">[Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="e3d0b-134"> [Comment : faire référence à un membre d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="e3d0b-134"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="e3d0b-135"> [Comment : parcourir une énumération dans Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="e3d0b-135"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="e3d0b-136"> [Comment : déterminer la chaîne associée à une valeur d’énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="e3d0b-136"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="e3d0b-137"> [Quand utiliser une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="e3d0b-137"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span></span>  
<span data-ttu-id="e3d0b-138"> [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="e3d0b-138"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="e3d0b-139"> [Types de données littéraux et constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="e3d0b-139"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="e3d0b-140"> [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span><span class="sxs-lookup"><span data-stu-id="e3d0b-140"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md)</span></span>
