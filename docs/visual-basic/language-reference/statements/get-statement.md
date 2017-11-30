---
title: Get, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Get
helpviewer_keywords:
- Get statement [Visual Basic], syntax
- Get statement [Visual Basic]
- properties [Visual Basic], read-only
- read-only properties
- Get keyword [Visual Basic]
- property procedures [Visual Basic], Get statements
ms.assetid: 56b05cdc-bd64-4dfd-bb12-824eacec6f94
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c1ff062a5e3bf41794bd5b4c90f1e188d6d97480
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="get-statement"></a><span data-ttu-id="70bc6-102">Get, instruction</span><span class="sxs-lookup"><span data-stu-id="70bc6-102">Get Statement</span></span>
<span data-ttu-id="70bc6-103">Déclare un `Get` procédure de propriété utilisée pour récupérer la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-103">Declares a `Get` property procedure used to retrieve the value of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70bc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70bc6-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Get()  
    [ statements ]  
End Get  
```  
  
## <a name="parts"></a><span data-ttu-id="70bc6-105">Composants</span><span class="sxs-lookup"><span data-stu-id="70bc6-105">Parts</span></span>  
  
|<span data-ttu-id="70bc6-106">Terme</span><span class="sxs-lookup"><span data-stu-id="70bc6-106">Term</span></span>|<span data-ttu-id="70bc6-107">Définition</span><span class="sxs-lookup"><span data-stu-id="70bc6-107">Definition</span></span>|  
|---|---|  
|`attributelist`|<span data-ttu-id="70bc6-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="70bc6-108">Optional.</span></span> <span data-ttu-id="70bc6-109">Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="70bc6-109">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>|  
|`accessmodifier`|<span data-ttu-id="70bc6-110">Facultatif sur l’une de le `Get` et `Set` instructions dans cette propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-110">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="70bc6-111">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="70bc6-111">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="70bc6-112">-   [Protégé](../../../visual-basic/language-reference/modifiers/protected.md)</span><span class="sxs-lookup"><span data-stu-id="70bc6-112">-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)</span></span><br /><span data-ttu-id="70bc6-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span><span class="sxs-lookup"><span data-stu-id="70bc6-113">-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)</span></span><br /><span data-ttu-id="70bc6-114">-   [Privé](../../../visual-basic/language-reference/modifiers/private.md)</span><span class="sxs-lookup"><span data-stu-id="70bc6-114">-   [Private](../../../visual-basic/language-reference/modifiers/private.md)</span></span><br />-   `Protected Friend`<br /><br /> <span data-ttu-id="70bc6-115">Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="70bc6-115">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>|  
|`statements`|<span data-ttu-id="70bc6-116">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="70bc6-116">Optional.</span></span> <span data-ttu-id="70bc6-117">Une ou plusieurs instructions qui s’exécutent lorsque le `Get` procédure de propriété est appelée.</span><span class="sxs-lookup"><span data-stu-id="70bc6-117">One or more statements that run when the `Get` property procedure is called.</span></span>|  
|`End Get`|<span data-ttu-id="70bc6-118">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="70bc6-118">Required.</span></span> <span data-ttu-id="70bc6-119">Termine la définition de la `Get` procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-119">Terminates the definition of the `Get` property procedure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70bc6-120">Remarques</span><span class="sxs-lookup"><span data-stu-id="70bc6-120">Remarks</span></span>  
 <span data-ttu-id="70bc6-121">Chaque propriété doit avoir un `Get` procédure de propriété, sauf si la propriété est marquée `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="70bc6-121">Every property must have a `Get` property procedure unless the property is marked `WriteOnly`.</span></span> <span data-ttu-id="70bc6-122">Le `Get` procédure est utilisée pour retourner la valeur actuelle de la propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-122">The `Get` procedure is used to return the current value of the property.</span></span>  
  
 <span data-ttu-id="70bc6-123">Visual Basic appelle automatiquement d’une propriété `Get` procédure lorsqu’une expression demande la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-123">Visual Basic automatically calls a property's `Get` procedure when an expression requests the property's value.</span></span>  
  
 <span data-ttu-id="70bc6-124">Le corps de la déclaration de propriété peut contenir uniquement la propriété `Get` et `Set` procédures entre le [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md) et `End Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="70bc6-124">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="70bc6-125">Il ne peut pas stocker de celles de ces procédures.</span><span class="sxs-lookup"><span data-stu-id="70bc6-125">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="70bc6-126">En particulier, il ne peut pas stocker la valeur de propriété en cours.</span><span class="sxs-lookup"><span data-stu-id="70bc6-126">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="70bc6-127">Vous devez stocker cette valeur en dehors de la propriété, car si vous le stockez dans les procédures de propriété, les autres procédures de propriété ne peut pas y accéder.</span><span class="sxs-lookup"><span data-stu-id="70bc6-127">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="70bc6-128">L’approche habituelle consiste à stocker la valeur dans un [privé](../../../visual-basic/language-reference/modifiers/private.md) variable déclarée au même niveau que la propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-128">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="70bc6-129">Vous devez définir un `Get` procédure à l’intérieur de la propriété à laquelle elle s’applique.</span><span class="sxs-lookup"><span data-stu-id="70bc6-129">You must define a `Get` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="70bc6-130">Le `Get` procédure par défaut est le niveau d’accès de sa propriété conteneur sauf si vous utilisez `accessmodifier` dans la `Get` instruction.</span><span class="sxs-lookup"><span data-stu-id="70bc6-130">The `Get` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Get` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="70bc6-131">Règles</span><span class="sxs-lookup"><span data-stu-id="70bc6-131">Rules</span></span>  
  
-   <span data-ttu-id="70bc6-132">**Niveaux d’accès mixtes.**</span><span class="sxs-lookup"><span data-stu-id="70bc6-132">**Mixed Access Levels.**</span></span> <span data-ttu-id="70bc6-133">Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour un le `Get` ou `Set` procédure, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="70bc6-133">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="70bc6-134">Si vous faites cela, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-134">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="70bc6-135">Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer le `Get` procédure `Private`, mais pas `Public`.</span><span class="sxs-lookup"><span data-stu-id="70bc6-135">For example, if the property is declared `Friend`, you can declare the `Get` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="70bc6-136">Si vous définissez un `ReadOnly` propriété, le `Get` procédure représente la propriété entière.</span><span class="sxs-lookup"><span data-stu-id="70bc6-136">If you are defining a `ReadOnly` property, the `Get` procedure represents the entire property.</span></span> <span data-ttu-id="70bc6-137">Vous ne pouvez pas déclarer un accès différent au niveau de `Get`, parce que seront définis à deux niveaux d’accès pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-137">You cannot declare a different access level for `Get`, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="70bc6-138">**Type de retour.**</span><span class="sxs-lookup"><span data-stu-id="70bc6-138">**Return Type.**</span></span> <span data-ttu-id="70bc6-139">Le [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md) peut déclarer le type de données de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="70bc6-139">The [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) can declare the data type of the value it returns.</span></span> <span data-ttu-id="70bc6-140">Le `Get` procédure retourne automatiquement ce type de données.</span><span class="sxs-lookup"><span data-stu-id="70bc6-140">The `Get` procedure automatically returns that data type.</span></span> <span data-ttu-id="70bc6-141">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, structure, classe ou d’interface.</span><span class="sxs-lookup"><span data-stu-id="70bc6-141">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="70bc6-142">Si le `Property` instruction ne spécifie pas `returntype`, la procédure retourne `Object`.</span><span class="sxs-lookup"><span data-stu-id="70bc6-142">If the `Property` statement does not specify `returntype`, the procedure returns `Object`.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="70bc6-143">Comportement</span><span class="sxs-lookup"><span data-stu-id="70bc6-143">Behavior</span></span>  
  
-   <span data-ttu-id="70bc6-144">**Retour d’une procédure.**</span><span class="sxs-lookup"><span data-stu-id="70bc6-144">**Returning from a Procedure.**</span></span> <span data-ttu-id="70bc6-145">Lorsque le `Get` procédure retourne au code appelant, l’exécution se poursuit au sein de l’instruction qui a demandé la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-145">When the `Get` procedure returns to the calling code, execution continues within the statement that requested the property value.</span></span>  
  
     <span data-ttu-id="70bc6-146">`Get`procédures de propriété peuvent retourner une valeur en utilisant le [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md) ou en affectant la valeur de retour au nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-146">`Get` property procedures can return a value using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or by assigning the return value to the property name.</span></span> <span data-ttu-id="70bc6-147">Pour plus d’informations, consultez « Valeur de retour » dans [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="70bc6-147">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="70bc6-148">Le `Exit Property` et `Return` instructions provoquent la sortie immédiate d’une procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-148">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="70bc6-149">Un nombre quelconque de `Exit Property` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Property` et `Return` instructions.</span><span class="sxs-lookup"><span data-stu-id="70bc6-149">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="70bc6-150">**Valeur de retour.**</span><span class="sxs-lookup"><span data-stu-id="70bc6-150">**Return Value.**</span></span> <span data-ttu-id="70bc6-151">Pour retourner une valeur d’un `Get` procédure, vous pouvez affecter la valeur au nom de propriété ou l’inclure dans un [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="70bc6-151">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span> <span data-ttu-id="70bc6-152">Le `Return` instruction assigne simultanément la `Get` procédure retourner de valeur et termine la procédure.</span><span class="sxs-lookup"><span data-stu-id="70bc6-152">The `Return` statement simultaneously assigns the `Get` procedure return value and exits the procedure.</span></span>  
  
     <span data-ttu-id="70bc6-153">Si vous utilisez `Exit Property` sans lui assigner une valeur au nom de propriété, le `Get` procédure retourne la valeur par défaut pour le type de données de la propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-153">If you use `Exit Property` without assigning a value to the property name, the `Get` procedure returns the default value for the property's data type.</span></span> <span data-ttu-id="70bc6-154">Pour plus d’informations, consultez « Valeur de retour » dans [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="70bc6-154">For more information, see "Return Value" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
     <span data-ttu-id="70bc6-155">L’exemple suivant illustre deux façons de la propriété en lecture seule `quoteForTheDay` peut retourner la valeur contenue dans la variable privée `quoteValue`.</span><span class="sxs-lookup"><span data-stu-id="70bc6-155">The following example illustrates two ways the read-only property `quoteForTheDay` can return the value held in the private variable `quoteValue`.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_2.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="70bc6-156">Exemple</span><span class="sxs-lookup"><span data-stu-id="70bc6-156">Example</span></span>  
 <span data-ttu-id="70bc6-157">L’exemple suivant utilise la `Get` instruction pour retourner la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="70bc6-157">The following example uses the `Get` statement to return the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#30](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/get-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="70bc6-158">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="70bc6-158">See Also</span></span>  
 [<span data-ttu-id="70bc6-159">Set (instruction)</span><span class="sxs-lookup"><span data-stu-id="70bc6-159">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="70bc6-160">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="70bc6-160">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="70bc6-161">Exit (instruction)</span><span class="sxs-lookup"><span data-stu-id="70bc6-161">Exit Statement</span></span>](../../../visual-basic/language-reference/statements/exit-statement.md)  
 [<span data-ttu-id="70bc6-162">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="70bc6-162">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="70bc6-163">Procédure pas à pas : définition de classes</span><span class="sxs-lookup"><span data-stu-id="70bc6-163">Walkthrough: Defining Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)
