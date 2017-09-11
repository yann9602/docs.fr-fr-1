---
title: "Vue d’ensemble des constantes (Visual Basic) | Documents Microsoft"
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
- constants
ms.assetid: 29016fe8-78b3-4dc8-90b8-1cfec2fa8ac9
caps.latest.revision: 14
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
ms.openlocfilehash: 2df21b9e3e814c654b355472aa645481060c6f68
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="constants-overview-visual-basic"></a><span data-ttu-id="272a0-102">Vue d'ensemble des constantes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="272a0-102">Constants Overview (Visual Basic)</span></span>
<span data-ttu-id="272a0-103">Une constante est un nom significatif qui prend la place d’un nombre ou une chaîne qui ne change pas.</span><span class="sxs-lookup"><span data-stu-id="272a0-103">A constant is a meaningful name that takes the place of a number or string that does not change.</span></span> <span data-ttu-id="272a0-104">Les constantes stockent des valeurs qui, comme son nom l’indique, demeurent identiques lors de l’exécution d’une application.</span><span class="sxs-lookup"><span data-stu-id="272a0-104">Constants store values that, as the name implies, remain the same throughout the execution of an application.</span></span> <span data-ttu-id="272a0-105">Vous pouvez considérablement améliorer la lisibilité de votre code et le rendre plus facile à gérer à l’aide de constantes.</span><span class="sxs-lookup"><span data-stu-id="272a0-105">You can greatly improve the readability of your code and make it easier to maintain by using constants.</span></span> <span data-ttu-id="272a0-106">Les utiliser dans le code qui contient des valeurs qui réapparaissent ou qui dépend de certains nombres difficiles à mémoriser ou sans signification évidente.</span><span class="sxs-lookup"><span data-stu-id="272a0-106">Use them in code that contains values that reappear or that depends on certain numbers that are difficult to remember or have no obvious meaning.</span></span>  
  
## <a name="how-to-create-and-use-constants"></a><span data-ttu-id="272a0-107">Comment créer et utiliser des constantes</span><span class="sxs-lookup"><span data-stu-id="272a0-107">How to Create and Use Constants</span></span>  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="272a0-108">contient plusieurs constantes prédéfinies, principalement à l’aide de l’impression et d’affichage.</span><span class="sxs-lookup"><span data-stu-id="272a0-108"> contains a number of predefined constants, mainly using for printing and displaying.</span></span> <span data-ttu-id="272a0-109">Vous pouvez également créer vos propres constantes avec le `Const` instruction, en utilisant les mêmes instructions que vous le feriez pour la création d’un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="272a0-109">You can also create your own constants with the `Const` statement, using the same guidelines you would for creating a variable name.</span></span> <span data-ttu-id="272a0-110">Si `Option Strict` est `On`, vous devez déclarer explicitement le type de constante.</span><span class="sxs-lookup"><span data-stu-id="272a0-110">If `Option Strict` is `On`, you must explicitly declare the constant type.</span></span>  
  
 <span data-ttu-id="272a0-111">La portée d’une constante, qui est l’ensemble du code que vous pouvez vous y référer sans qualifier son nom, est identique à celle d’une variable déclarée au même emplacement.</span><span class="sxs-lookup"><span data-stu-id="272a0-111">A constant's scope, which is the set of all code that can refer to it without qualifying its name, is the same as that of a variable declared in the same location.</span></span> <span data-ttu-id="272a0-112">Pour créer une constante qui existe dans la portée d’une procédure particulière, vous devez la déclarer dans cette procédure.</span><span class="sxs-lookup"><span data-stu-id="272a0-112">To create a constant that exists within the scope of a particular procedure, declare it inside that procedure.</span></span> <span data-ttu-id="272a0-113">Pour créer une constante qui est disponible dans une application, déclarez-le à l’aide de le `Public` mot clé dans la section des déclarations de la classe.</span><span class="sxs-lookup"><span data-stu-id="272a0-113">To create a constant that is available throughout an application, declare it using the `Public` keyword in the declarations section of the class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="272a0-114">Bien que les constantes ressemblent un peu aux variables, les modifier ni leur assigner de nouvelles valeurs que possible à des variables.</span><span class="sxs-lookup"><span data-stu-id="272a0-114">Although constants somewhat resemble variables, you cannot modify them or assign new values to them as you can to variables.</span></span>  
  
 <span data-ttu-id="272a0-115">Les constantes utilisées dans votre code peuvent être définies par le modèle objet pour les contrôles ou les composants que vous utilisez, ou ils peuvent être définis par l’utilisateur (celles que vous créez vous-même).</span><span class="sxs-lookup"><span data-stu-id="272a0-115">The constants you use in your code can be defined by the object model for controls or components you work with, or they can be user-defined (that is, those you create yourself).</span></span>  
  
## <a name="compile-time-and-run-time-constants"></a><span data-ttu-id="272a0-116">Constantes de compilation et d’exécution</span><span class="sxs-lookup"><span data-stu-id="272a0-116">Compile-time and Run-time Constants</span></span>  
 <span data-ttu-id="272a0-117">Une constante de compilation est calculée au moment où que le code est compilé pendant une constante d’exécution peut être calculée uniquement pendant que l’application est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="272a0-117">A compile-time constant is computed at the time the code is compiled, while a run-time constant can only be computed while the application is running.</span></span> <span data-ttu-id="272a0-118">Une constante de compilation aura la même valeur chaque fois qu'une application s’exécute, une constante d’exécution peut être modifié chaque fois.</span><span class="sxs-lookup"><span data-stu-id="272a0-118">A compile-time constant will have the same value each time an application runs, while a run-time constant may change each time.</span></span> <span data-ttu-id="272a0-119">Constantes de compilation sont nécessaires pour les cas tels que les limites de tableau, les expressions de cas ou les initialiseurs d’énumérateur.</span><span class="sxs-lookup"><span data-stu-id="272a0-119">Compile-time constants are required for cases such as array bounds, case expressions, or enumerator initializers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="272a0-120">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="272a0-120">In This Section</span></span>  
  
|<span data-ttu-id="272a0-121">Définition</span><span class="sxs-lookup"><span data-stu-id="272a0-121">Definition</span></span>|<span data-ttu-id="272a0-122">Terme</span><span class="sxs-lookup"><span data-stu-id="272a0-122">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="272a0-123">Guide pratique : déclarer une constante</span><span class="sxs-lookup"><span data-stu-id="272a0-123">How to: Declare A Constant</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)|<span data-ttu-id="272a0-124">Explique comment utiliser le `Const` l’instruction pour déclarer une constante et définir sa valeur ; en déclarant une constante, vous attribuer un nom significatif à la valeur.</span><span class="sxs-lookup"><span data-stu-id="272a0-124">Explains how to use the `Const` statement to declare a constant and set its value; by declaring a constant, you assign a meaningful name to the value.</span></span>|  
|[<span data-ttu-id="272a0-125">Constantes définies par l’utilisateur</span><span class="sxs-lookup"><span data-stu-id="272a0-125">User-Defined Constants</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)|<span data-ttu-id="272a0-126">Décrit comment créer vos propres constantes, y compris des informations sur la portée et comment éviter les références circulaires.</span><span class="sxs-lookup"><span data-stu-id="272a0-126">Describes how to create your own constants, including information on scoping and how to avoid circular references.</span></span>|  
|[<span data-ttu-id="272a0-127">Constantes et types de données littérales</span><span class="sxs-lookup"><span data-stu-id="272a0-127">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)|<span data-ttu-id="272a0-128">Fournit des informations sur la façon dont les [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur initialise des constantes lorsque `Option Explicit` est désactivé.</span><span class="sxs-lookup"><span data-stu-id="272a0-128">Provides information on how the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compiler initializes constants when `Option Explicit` is turned off.</span></span>|  
|[<span data-ttu-id="272a0-129">Guide pratique : regrouper les valeurs de constante connexes</span><span class="sxs-lookup"><span data-stu-id="272a0-129">How to: Group Related Constant Values Together</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-group-related-constant-values-together.md)|<span data-ttu-id="272a0-130">Montre comment grouper des valeurs constantes qui sont liées.</span><span class="sxs-lookup"><span data-stu-id="272a0-130">Demonstrates how to group constant values that are related.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="272a0-131">Référence</span><span class="sxs-lookup"><span data-stu-id="272a0-131">Reference</span></span>  
  
|<span data-ttu-id="272a0-132">Définition</span><span class="sxs-lookup"><span data-stu-id="272a0-132">Definition</span></span>|<span data-ttu-id="272a0-133">Terme</span><span class="sxs-lookup"><span data-stu-id="272a0-133">Term</span></span>|  
|---|---|  
|[<span data-ttu-id="272a0-134">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="272a0-134">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)|<span data-ttu-id="272a0-135">Répertorie les constantes prédéfinies par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span><span class="sxs-lookup"><span data-stu-id="272a0-135">Lists the constants predefined by [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].</span></span>|  
|[<span data-ttu-id="272a0-136">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="272a0-136">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)|<span data-ttu-id="272a0-137">Décrit la `Const` instruction et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="272a0-137">Describes the `Const` statement and its use.</span></span>|  
|[<span data-ttu-id="272a0-138">Option Strict (instruction)</span><span class="sxs-lookup"><span data-stu-id="272a0-138">Option Strict Statement</span></span>](../../../../visual-basic/language-reference/statements/option-strict-statement.md)|<span data-ttu-id="272a0-139">Décrit la `Option Strict` instruction et son utilisation.</span><span class="sxs-lookup"><span data-stu-id="272a0-139">Describes the `Option Strict` statement and its use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="272a0-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="272a0-140">See Also</span></span>  
 <span data-ttu-id="272a0-141">[Vue d’ensemble des énumérations](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="272a0-141">[Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="272a0-142"> [Comment : initialiser une Variable tableau en Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span><span class="sxs-lookup"><span data-stu-id="272a0-142"> [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md)</span></span>
