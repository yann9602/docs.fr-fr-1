---
title: "Comment : déclarer des énumérations (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- enumerations [Visual Basic], declaring
- declaring enumerations [Visual Basic]
ms.assetid: db4ca1c3-f429-4c81-ae81-29e0157b29fd
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 938550ebbfcf099729db3de96b809549cb234d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-enumerations-visual-basic"></a><span data-ttu-id="a03a1-102">Comment : déclarer des énumérations (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a03a1-102">How to: Declare Enumerations (Visual Basic)</span></span>
<span data-ttu-id="a03a1-103">Vous créez une énumération avec la `Enum` instruction dans la section des déclarations d’une classe ou un module.</span><span class="sxs-lookup"><span data-stu-id="a03a1-103">You create an enumeration with the `Enum` statement in the declarations section of a class or module.</span></span> <span data-ttu-id="a03a1-104">Vous ne pouvez pas déclarer une énumération au sein d’une méthode.</span><span class="sxs-lookup"><span data-stu-id="a03a1-104">You cannot declare an enumeration within a method.</span></span> <span data-ttu-id="a03a1-105">Pour spécifier le niveau d’accès approprié, utilisez `Private`, `Protected`, `Friend`, ou `Public`.</span><span class="sxs-lookup"><span data-stu-id="a03a1-105">To specify the appropriate level of access, use `Private`, `Protected`, `Friend`, or `Public`.</span></span>  
  
 <span data-ttu-id="a03a1-106">Un `Enum` type possède un nom, un type sous-jacent et un ensemble de champs, chacun représentant une constante.</span><span class="sxs-lookup"><span data-stu-id="a03a1-106">An `Enum` type has a name, an underlying type, and a set of fields, each representing a constant.</span></span> <span data-ttu-id="a03a1-107">Le nom doit être un qualificateur Visual Basic .NET valide.</span><span class="sxs-lookup"><span data-stu-id="a03a1-107">The name must be a valid Visual Basic .NET qualifier.</span></span> <span data-ttu-id="a03a1-108">Le type sous-jacent doit être un des types d’entiers :`Byte`, `Short`, `Long` ou `Integer`.</span><span class="sxs-lookup"><span data-stu-id="a03a1-108">The underlying type must be one of the integer types—`Byte`, `Short`, `Long` or `Integer`.</span></span> <span data-ttu-id="a03a1-109">`Integer` est la valeur par défaut.</span><span class="sxs-lookup"><span data-stu-id="a03a1-109">`Integer` is the default.</span></span> <span data-ttu-id="a03a1-110">Les énumérations sont toujours fortement typées et ne sont pas interchangeables avec les types de nombre entier.</span><span class="sxs-lookup"><span data-stu-id="a03a1-110">Enumerations are always strongly typed and are not interchangeable with integer number types.</span></span>  
  
 <span data-ttu-id="a03a1-111">Les énumérations ne peut pas avoir de valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="a03a1-111">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="a03a1-112">Si une énumération est assignée une valeur à virgule flottante `Option Strict On`, résulte d’une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="a03a1-112">If an enumeration is assigned a floating-point value with `Option Strict On`, a compiler error results.</span></span> <span data-ttu-id="a03a1-113">Si `Option Strict` est `Off`, la valeur est automatiquement convertie en la `Enum` type.</span><span class="sxs-lookup"><span data-stu-id="a03a1-113">If `Option Strict` is `Off`, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="a03a1-114">Pour plus d’informations sur les noms et comment utiliser le `Imports` instruction pour rendre la qualification de noms inutiles, consultez [énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="a03a1-114">For information on names, and how to use the `Imports` statement to make name qualification unnecessary, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-declare-an-enumeration"></a><span data-ttu-id="a03a1-115">Pour déclarer une énumération</span><span class="sxs-lookup"><span data-stu-id="a03a1-115">To declare an enumeration</span></span>  
  
1.  <span data-ttu-id="a03a1-116">Écrivez une déclaration qui inclut un niveau d’accès de code, la `Enum` (mot clé) et un nom valide, comme dans les exemples suivants, chacun d’eux déclare une autre `Enum`.</span><span class="sxs-lookup"><span data-stu-id="a03a1-116">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name, as in the following examples, each of which declares a different `Enum`.</span></span>  
  
     [!code-vb[VbEnumsTask#3](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_1.vb)]  
  
2.  <span data-ttu-id="a03a1-117">Définissez les constantes dans l’énumération.</span><span class="sxs-lookup"><span data-stu-id="a03a1-117">Define the constants in the enumeration.</span></span> <span data-ttu-id="a03a1-118">Par défaut, la première constante d’une énumération est initialisée à `0`, et les constantes suivantes sont initialisées à une valeur de plus que la constante précédente.</span><span class="sxs-lookup"><span data-stu-id="a03a1-118">By default, the first constant in an enumeration is initialized to `0`, and subsequent constants are initialized to a value of one more than the previous constant.</span></span> <span data-ttu-id="a03a1-119">Par exemple, l’énumération suivante, `Days`, contient une constante nommée `Sunday` avec la valeur `0`, une constante nommée `Monday` avec la valeur `1`, une constante nommée `Tuesday` avec la valeur de `2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="a03a1-119">For example, the following enumeration, `Days`, contains a constant named `Sunday` with the value `0`, a constant named `Monday` with the value `1`, a constant named `Tuesday` with the value of `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#4](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_2.vb)]  
  
3.  <span data-ttu-id="a03a1-120">Vous pouvez affecter explicitement des valeurs à des constantes dans une énumération à l’aide d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="a03a1-120">You can explicitly assign values to constants in an enumeration by using an assignment statement.</span></span> <span data-ttu-id="a03a1-121">Vous pouvez affecter une valeur entière, y compris les nombres négatifs.</span><span class="sxs-lookup"><span data-stu-id="a03a1-121">You can assign any integer value, including negative numbers.</span></span> <span data-ttu-id="a03a1-122">Par exemple, vous souhaiterez peut-être constantes avec des valeurs inférieures à zéro pour représenter les conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="a03a1-122">For example, you may want constants with values less than zero to represent error conditions.</span></span> <span data-ttu-id="a03a1-123">Dans l’énumération suivante, la constante `Invalid` est explicitement affectée de la valeur `–1`et la constante `Sunday` reçoit la valeur `0`.</span><span class="sxs-lookup"><span data-stu-id="a03a1-123">In the following enumeration, the constant `Invalid` is explicitly assigned the value `–1`, and the constant `Sunday` is assigned the value `0`.</span></span> <span data-ttu-id="a03a1-124">Car il s’agit de la première constante dans l’énumération, `Saturday` est également initialisée à la valeur `0`.</span><span class="sxs-lookup"><span data-stu-id="a03a1-124">Because it is the first constant in the enumeration, `Saturday` is also initialized to the value `0`.</span></span> <span data-ttu-id="a03a1-125">La valeur de `Monday` est `1` (plus que la valeur de `Sunday`) ; la valeur de `Tuesday` est `2`, et ainsi de suite.</span><span class="sxs-lookup"><span data-stu-id="a03a1-125">The value of `Monday` is `1` (one more than the value of `Sunday`); the value of `Tuesday` is `2`, and so on.</span></span>  
  
     [!code-vb[VbEnumsTask#5](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_3.vb)]  
  
### <a name="to-declare-an-enumeration-as-an-explicit-type"></a><span data-ttu-id="a03a1-126">Pour déclarer une énumération comme un type explicite</span><span class="sxs-lookup"><span data-stu-id="a03a1-126">To declare an enumeration as an explicit type</span></span>  
  
-   <span data-ttu-id="a03a1-127">Spécifiez le type de l’énumération à l’aide de la `As` clause, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="a03a1-127">Specify the type of the enum by using the `As` clause, as shown in the following example.</span></span>  
  
     [!code-vb[VbEnumsTask#6](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-enumerations_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a03a1-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a03a1-128">See Also</span></span>  
 [<span data-ttu-id="a03a1-129">Énumérations et qualification de noms</span><span class="sxs-lookup"><span data-stu-id="a03a1-129">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="a03a1-130">Guide pratique : faire référence à un membre d’énumération</span><span class="sxs-lookup"><span data-stu-id="a03a1-130">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="a03a1-131">Comment : parcourir une énumération dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a03a1-131">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="a03a1-132">Guide pratique : déterminer la chaîne associée à une valeur d’énumération</span><span class="sxs-lookup"><span data-stu-id="a03a1-132">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="a03a1-133">Quand utiliser une énumération</span><span class="sxs-lookup"><span data-stu-id="a03a1-133">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="a03a1-134">Vue d’ensemble des constantes</span><span class="sxs-lookup"><span data-stu-id="a03a1-134">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="a03a1-135">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="a03a1-135">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="a03a1-136">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="a03a1-136">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
