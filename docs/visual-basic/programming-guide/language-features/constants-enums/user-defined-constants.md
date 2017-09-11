---
title: "Constantes (Visual Basic) définis par l’utilisateur | Documents Microsoft"
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
- constants, circular references
- Const statement [Visual Basic], user-defined constants
- user-defined constants
- scope, constants
- constants, user-defined
- circular references between constants
ms.assetid: a1206d5c-c45e-4ac2-970a-4a0be6a05fdd
caps.latest.revision: 19
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
ms.openlocfilehash: b1ab1501309823b1565d5198fff25edf2927a2ce
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="user-defined-constants-visual-basic"></a><span data-ttu-id="64b5c-102">Constantes définies par l'utilisateur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64b5c-102">User-Defined Constants (Visual Basic)</span></span>
<span data-ttu-id="64b5c-103">Une constante est un nom significatif qui prend la place d’un nombre ou une chaîne qui ne change pas.</span><span class="sxs-lookup"><span data-stu-id="64b5c-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="64b5c-104">Les constantes stockent des valeurs qui, comme son nom l’indique, demeurent constantes lors de l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="64b5c-104">Constants store values that, as the name implies, remain constant throughout the execution of an application.</span></span> <span data-ttu-id="64b5c-105">Vous pouvez utiliser les constantes qui sont définies par les contrôles ou les composants que vous utilisez, ou vous pouvez créer vos propres.</span><span class="sxs-lookup"><span data-stu-id="64b5c-105">You can use constants that are defined by the controls or components you work with, or you can create your own.</span></span> <span data-ttu-id="64b5c-106">Constantes que vous créez vous-même sont décrits comme *définie par l’utilisateur*.</span><span class="sxs-lookup"><span data-stu-id="64b5c-106">Constants you create yourself are described as *user-defined*.</span></span>  
  
 <span data-ttu-id="64b5c-107">Vous déclarez une constante avec la `Const` instruction, en utilisant les mêmes instructions que vous le feriez pour la création d’un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="64b5c-107">You declare a constant with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="64b5c-108">Si `Option Strict` est `On`, vous devez déclarer explicitement le type de constante.</span><span class="sxs-lookup"><span data-stu-id="64b5c-108">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
## <a name="const-statement-usage"></a><span data-ttu-id="64b5c-109">Utilisation de l’instruction const</span><span class="sxs-lookup"><span data-stu-id="64b5c-109">Const Statement Usage</span></span>  
 <span data-ttu-id="64b5c-110">Un `Const` instruction peut représenter une valeur mathématique ou de date/heure :</span><span class="sxs-lookup"><span data-stu-id="64b5c-110">A `Const` statement can represent a mathematical or date/time quantity:</span></span>  
  
 <span data-ttu-id="64b5c-111">[!code-vb[VbEnumsTask&#10;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="64b5c-111">[!code-vb[VbEnumsTask#10](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_1.vb)]</span></span>  
  
 <span data-ttu-id="64b5c-112">Elle peut également définir `String` constantes :</span><span class="sxs-lookup"><span data-stu-id="64b5c-112">It also can define `String` constants:</span></span>  
  
 <span data-ttu-id="64b5c-113">[!code-vb[VbEnumsTask&#13;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="64b5c-113">[!code-vb[VbEnumsTask#13](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_2.vb)]</span></span>  
  
 <span data-ttu-id="64b5c-114">L’expression située à droite du signe égal ( `=` ) est souvent un nombre ou une chaîne littérale, mais il peut également être une expression qui donne un nombre ou une chaîne (bien que cette expression ne peut pas contenir les appels aux fonctions).</span><span class="sxs-lookup"><span data-stu-id="64b5c-114">The expression on the right side of the equal sign ( `=` ) is often a number or literal string, but it also can be an expression that results in a number or string (although that expression cannot contain calls to functions).</span></span> <span data-ttu-id="64b5c-115">Vous pouvez même définir des constantes en termes de constantes définies préalablement :</span><span class="sxs-lookup"><span data-stu-id="64b5c-115">You can even define constants in terms of previously defined constants:</span></span>  
  
 <span data-ttu-id="64b5c-116">[!code-vb[VbEnumsTask&#15;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="64b5c-116">[!code-vb[VbEnumsTask#15](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_3.vb)]</span></span>  
  
## <a name="scope-of-user-defined-constants"></a><span data-ttu-id="64b5c-117">Portée des constantes définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="64b5c-117">Scope of User-Defined Constants</span></span>  
 <span data-ttu-id="64b5c-118">Un `Const` étendue de l’instruction est identique à celle d’une variable déclarée au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="64b5c-118">A `Const` statement's scope is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="64b5c-119">Vous pouvez spécifier l’étendue d’une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="64b5c-119">You can specify scope in any of the following ways:</span></span>  
  
-   <span data-ttu-id="64b5c-120">Pour créer une constante qui existe uniquement dans une procédure, vous devez le déclarer dans celle-ci.</span><span class="sxs-lookup"><span data-stu-id="64b5c-120">To create a constant that exists only within a procedure, declare it within that procedure.</span></span>  
  
-   <span data-ttu-id="64b5c-121">Pour créer une constante disponible pour toutes les procédures dans une classe, mais pas pour le code en dehors du module, déclarez-le dans la section des déclarations de la classe.</span><span class="sxs-lookup"><span data-stu-id="64b5c-121">To create a constant available to all procedures within a class, but not to any code outside that module, declare it in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="64b5c-122">Pour créer une constante qui est disponible pour tous les membres d’un assembly, mais pas pour les clients en dehors de l’assembly, déclarez-le à l’aide de le `Friend` mot clé dans la section des déclarations de la classe.</span><span class="sxs-lookup"><span data-stu-id="64b5c-122">To create a constant that is available to all members of an assembly, but not to outside clients of the assembly, declare it using the `Friend` keyword in the declarations section of the class.</span></span>  
  
-   <span data-ttu-id="64b5c-123">Pour créer une constante disponible tout au long de l’application, déclarez-le à l’aide de la `Public` (mot clé) dans les déclarations de section de la classe.</span><span class="sxs-lookup"><span data-stu-id="64b5c-123">To create a constant available throughout the application, declare it using the `Public` keyword in the declarations section the class.</span></span>  
  
 <span data-ttu-id="64b5c-124">Pour plus d’informations, consultez [Comment : déclarer une constante](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span><span class="sxs-lookup"><span data-stu-id="64b5c-124">For more information, see [How to: Declare A Constant](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md).</span></span>  
  
### <a name="avoiding-circular-references"></a><span data-ttu-id="64b5c-125">Éviter des références circulaires</span><span class="sxs-lookup"><span data-stu-id="64b5c-125">Avoiding Circular References</span></span>  
 <span data-ttu-id="64b5c-126">Étant donné que les constantes peuvent être définies en termes d’autres constantes, il est possible de créer par inadvertance un *cycle*, ou une référence circulaire entre deux constantes ou plus.</span><span class="sxs-lookup"><span data-stu-id="64b5c-126">Because constants can be defined in terms of other constants, it is possible to inadvertently create a *cycle*, or circular reference, between two or more constants.</span></span> <span data-ttu-id="64b5c-127">Un cycle se produit lorsque vous disposez de deux ou plusieurs constantes publiques, chacun d’eux est défini en termes de l’autre, comme dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="64b5c-127">A cycle occurs when you have two or more public constants, each of which is defined in terms of the other, as in the following example:</span></span>  
  
 <span data-ttu-id="64b5c-128">[!code-vb[VbEnumsTask&#16;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="64b5c-128">[!code-vb[VbEnumsTask#16](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_4.vb)]</span></span>  
<span data-ttu-id="64b5c-129">[!code-vb[VbEnumsTask&#17;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="64b5c-129">[!code-vb[VbEnumsTask#17](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/user-defined-constants_5.vb)]</span></span>  
  
 <span data-ttu-id="64b5c-130">Lorsqu’un cycle se produit, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] génère une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="64b5c-130">If a cycle occurs, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] generates a compiler error.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b5c-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64b5c-131">See Also</span></span>  
 <span data-ttu-id="64b5c-132">[Const (instruction)](../../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="64b5c-132">[Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="64b5c-133"> [Types de données littéraux et constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="64b5c-133"> [Constant and Literal Data Types](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md) </span></span>  
<span data-ttu-id="64b5c-134"> [Constantes et énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md) </span><span class="sxs-lookup"><span data-stu-id="64b5c-134"> [Constants and Enumerations](../../../../visual-basic/programming-guide/language-features/constants-enums/index.md) </span></span>  
<span data-ttu-id="64b5c-135"> [Constantes et énumérations](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="64b5c-135"> [Constants and Enumerations](../../../../visual-basic/language-reference/constants-and-enumerations.md) </span></span>  
<span data-ttu-id="64b5c-136"> [Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="64b5c-136"> [Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="64b5c-137"> [Vue d’ensemble des constantes](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span><span class="sxs-lookup"><span data-stu-id="64b5c-137"> [Constants Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md) </span></span>  
<span data-ttu-id="64b5c-138"> [Comment : déclarer une énumération](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="64b5c-138"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="64b5c-139"> [Énumérations et Qualification de noms](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="64b5c-139"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="64b5c-140"> [Option Strict (instruction)](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span><span class="sxs-lookup"><span data-stu-id="64b5c-140"> [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)</span></span>
