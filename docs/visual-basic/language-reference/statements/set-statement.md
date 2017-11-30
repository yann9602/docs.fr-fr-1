---
title: Set, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Set
helpviewer_keywords:
- property procedures [Visual Basic], Set statements
- Set statement [Visual Basic]
- Set statement [Visual Basic], syntax
- write-only properties
- properties [Visual Basic], write-only
ms.assetid: 9ecc27b4-df84-420d-9075-db25455fb3cd
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3b18e6c858e64e78d7ab85fdaafd70e510f7a02f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="set-statement-visual-basic"></a><span data-ttu-id="f0826-102">Set, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f0826-102">Set Statement (Visual Basic)</span></span>
<span data-ttu-id="f0826-103">Déclare un `Set` procédure de propriété utilisée pour affecter une valeur à une propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-103">Declares a `Set` property procedure used to assign a value to a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0826-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0826-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] Set (ByVal value [ As datatype ])  
    [ statements ]  
End Set  
```  
  
## <a name="parts"></a><span data-ttu-id="f0826-105">Composants</span><span class="sxs-lookup"><span data-stu-id="f0826-105">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="f0826-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0826-106">Optional.</span></span> <span data-ttu-id="f0826-107">Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="f0826-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `accessmodifier`  
 <span data-ttu-id="f0826-108">Facultatif sur l’une de le `Get` et `Set` instructions dans cette propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-108">Optional on at most one of the `Get` and `Set` statements in this property.</span></span> <span data-ttu-id="f0826-109">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="f0826-109">Can be one of the following:</span></span>  
  
-   [<span data-ttu-id="f0826-110">Protected</span><span class="sxs-lookup"><span data-stu-id="f0826-110">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
-   [<span data-ttu-id="f0826-111">Friend</span><span class="sxs-lookup"><span data-stu-id="f0826-111">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
-   [<span data-ttu-id="f0826-112">Private</span><span class="sxs-lookup"><span data-stu-id="f0826-112">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
-   `Protected Friend`  
  
 <span data-ttu-id="f0826-113">Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="f0826-113">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 `value`  
 <span data-ttu-id="f0826-114">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f0826-114">Required.</span></span> <span data-ttu-id="f0826-115">Paramètre contenant la nouvelle valeur pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-115">Parameter containing the new value for the property.</span></span>  
  
 `datatype`  
 <span data-ttu-id="f0826-116">Obligatoire si `Option Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="f0826-116">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="f0826-117">Type de données de la `value` paramètre.</span><span class="sxs-lookup"><span data-stu-id="f0826-117">Data type of the `value` parameter.</span></span> <span data-ttu-id="f0826-118">Le type de données spécifié doit être le même que le type de données de la propriété où cette `Set` instruction est déclarée.</span><span class="sxs-lookup"><span data-stu-id="f0826-118">The data type specified must be the same as the data type of the property where this `Set` statement is declared.</span></span>  
  
 `statements`  
 <span data-ttu-id="f0826-119">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="f0826-119">Optional.</span></span> <span data-ttu-id="f0826-120">Une ou plusieurs instructions qui s’exécutent lorsque le `Set` procédure de propriété est appelée.</span><span class="sxs-lookup"><span data-stu-id="f0826-120">One or more statements that run when the `Set` property procedure is called.</span></span>  
  
 `End Set`  
 <span data-ttu-id="f0826-121">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="f0826-121">Required.</span></span> <span data-ttu-id="f0826-122">Termine la définition de la `Set` procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-122">Terminates the definition of the `Set` property procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0826-123">Remarques</span><span class="sxs-lookup"><span data-stu-id="f0826-123">Remarks</span></span>  
 <span data-ttu-id="f0826-124">Chaque propriété doit avoir un `Set` procédure de propriété, sauf si la propriété est marquée `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="f0826-124">Every property must have a `Set` property procedure unless the property is marked `ReadOnly`.</span></span> <span data-ttu-id="f0826-125">Le `Set` procédure est utilisée pour définir la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-125">The `Set` procedure is used to set the value of the property.</span></span>  
  
 <span data-ttu-id="f0826-126">Visual Basic appelle automatiquement d’une propriété `Set` procédure lors d’une instruction d’assignation fournit une valeur à stocker dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-126">Visual Basic automatically calls a property's `Set` procedure when an assignment statement provides a value to be stored in the property.</span></span>  
  
 <span data-ttu-id="f0826-127">Visual Basic passe un paramètre à la `Set` procédure pendant les assignations de propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-127">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="f0826-128">Si vous ne fournissez pas un paramètre pour `Set`, l’environnement de développement intégré (IDE) utilise un paramètre implicite nommé `value`.</span><span class="sxs-lookup"><span data-stu-id="f0826-128">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="f0826-129">Le paramètre conserve la valeur à affecter à la propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-129">The parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="f0826-130">En général, stockez la valeur dans une variable locale privée et de la retourner chaque fois que le `Get` procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="f0826-130">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
 <span data-ttu-id="f0826-131">Le corps de la déclaration de propriété peut contenir uniquement la propriété `Get` et `Set` procédures entre le [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md) et `End Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="f0826-131">The body of the property declaration can contain only the property's `Get` and `Set` procedures between the [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="f0826-132">Il ne peut pas stocker de celles de ces procédures.</span><span class="sxs-lookup"><span data-stu-id="f0826-132">It cannot store anything other than those procedures.</span></span> <span data-ttu-id="f0826-133">En particulier, il ne peut pas stocker la valeur de propriété en cours.</span><span class="sxs-lookup"><span data-stu-id="f0826-133">In particular, it cannot store the property's current value.</span></span> <span data-ttu-id="f0826-134">Vous devez stocker cette valeur en dehors de la propriété, car si vous le stockez dans les procédures de propriété, les autres procédures de propriété ne peut pas y accéder.</span><span class="sxs-lookup"><span data-stu-id="f0826-134">You must store this value outside the property, because if you store it inside either of the property procedures, the other property procedure cannot access it.</span></span> <span data-ttu-id="f0826-135">L’approche habituelle consiste à stocker la valeur dans un [privé](../../../visual-basic/language-reference/modifiers/private.md) variable déclarée au même niveau que la propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-135">The usual approach is to store the value in a [Private](../../../visual-basic/language-reference/modifiers/private.md) variable declared at the same level as the property.</span></span> <span data-ttu-id="f0826-136">Vous devez définir un `Set` procédure à l’intérieur de la propriété à laquelle elle s’applique.</span><span class="sxs-lookup"><span data-stu-id="f0826-136">You must define a `Set` procedure inside the property to which it applies.</span></span>  
  
 <span data-ttu-id="f0826-137">Le `Set` procédure par défaut est le niveau d’accès de sa propriété conteneur sauf si vous utilisez `accessmodifier` dans la `Set` instruction.</span><span class="sxs-lookup"><span data-stu-id="f0826-137">The `Set` procedure defaults to the access level of its containing property unless you use `accessmodifier` in the `Set` statement.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="f0826-138">Règles</span><span class="sxs-lookup"><span data-stu-id="f0826-138">Rules</span></span>  
  
-   <span data-ttu-id="f0826-139">**Niveaux d’accès mixtes.**</span><span class="sxs-lookup"><span data-stu-id="f0826-139">**Mixed Access Levels.**</span></span> <span data-ttu-id="f0826-140">Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour un le `Get` ou `Set` procédure, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="f0826-140">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="f0826-141">Si vous faites cela, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-141">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="f0826-142">Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer le `Set` procédure `Private`, mais pas `Public`.</span><span class="sxs-lookup"><span data-stu-id="f0826-142">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="f0826-143">Si vous définissez un `WriteOnly` propriété, le `Set` procédure représente la propriété entière.</span><span class="sxs-lookup"><span data-stu-id="f0826-143">If you are defining a `WriteOnly` property, the `Set` procedure represents the entire property.</span></span> <span data-ttu-id="f0826-144">Vous ne pouvez pas déclarer un accès différent au niveau de `Set`, parce que seront définis à deux niveaux d’accès pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-144">You cannot declare a different access level for `Set`, because that would set two access levels for the property.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="f0826-145">Comportement</span><span class="sxs-lookup"><span data-stu-id="f0826-145">Behavior</span></span>  
  
-   <span data-ttu-id="f0826-146">**Retour d’une procédure de propriété.**</span><span class="sxs-lookup"><span data-stu-id="f0826-146">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="f0826-147">Lorsque le `Set` procédure retourne au code appelant, l’exécution se poursuit après l’instruction qui a fourni la valeur à stocker.</span><span class="sxs-lookup"><span data-stu-id="f0826-147">When the `Set` procedure returns to the calling code, execution continues following the statement that provided the value to be stored.</span></span>  
  
     <span data-ttu-id="f0826-148">`Set`procédures de propriété peuvent retourner à l’aide du [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md) ou [instruction Exit](../../../visual-basic/language-reference/statements/exit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f0826-148">`Set` property procedures can return using either the [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) or the [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md).</span></span>  
  
     <span data-ttu-id="f0826-149">Le `Exit Property` et `Return` instructions provoquent la sortie immédiate d’une procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-149">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="f0826-150">Un nombre quelconque de `Exit Property` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Property` et `Return` instructions.</span><span class="sxs-lookup"><span data-stu-id="f0826-150">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0826-151">Exemple</span><span class="sxs-lookup"><span data-stu-id="f0826-151">Example</span></span>  
 <span data-ttu-id="f0826-152">L’exemple suivant utilise la `Set` instruction pour définir la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="f0826-152">The following example uses the `Set` statement to set the value of a property.</span></span>  
  
 [!code-vb[VbVbalrStatements#55](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/set-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f0826-153">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0826-153">See Also</span></span>  
 [<span data-ttu-id="f0826-154">Get (instruction)</span><span class="sxs-lookup"><span data-stu-id="f0826-154">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="f0826-155">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="f0826-155">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="f0826-156">Sub (instruction)</span><span class="sxs-lookup"><span data-stu-id="f0826-156">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="f0826-157">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="f0826-157">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
