---
title: "Procédures de propriété (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Set statement [Visual Basic], Property procedures
- Visual Basic code, procedures
- return values [Visual Basic], Property procedures
- syntax [Visual Basic], Property procedures
- procedures [Visual Basic], property
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], custom
- property procedures
- Get statement [Visual Basic], property procedures
ms.assetid: 46a98379-e1a2-45dd-a48c-b51213f5ab07
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cbdf49d5c3eb5ef71b25a060d62f55f19098f445
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="property-procedures-visual-basic"></a><span data-ttu-id="c2105-102">Procédures de propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2105-102">Property Procedures (Visual Basic)</span></span>
<span data-ttu-id="c2105-103">Une procédure de propriété est une série de [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] instructions qui manipulent une propriété personnalisée d’un module, classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="c2105-103">A property procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements that manipulate a custom property on a module, class, or structure.</span></span> <span data-ttu-id="c2105-104">Procédures de propriété sont également appelés *les accesseurs de propriété*.</span><span class="sxs-lookup"><span data-stu-id="c2105-104">Property procedures are also known as *property accessors*.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="c2105-105">Fournit des procédures de propriété suivantes :</span><span class="sxs-lookup"><span data-stu-id="c2105-105"> provides for the following property procedures:</span></span>  
  
-   <span data-ttu-id="c2105-106">A `Get` procédure retourne la valeur d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-106">A `Get` procedure returns the value of a property.</span></span> <span data-ttu-id="c2105-107">Elle est appelée lorsque vous accédez à la propriété dans une expression.</span><span class="sxs-lookup"><span data-stu-id="c2105-107">It is called when you access the property in an expression.</span></span>  
  
-   <span data-ttu-id="c2105-108">A `Set` procédure définit une propriété sur une valeur, y compris une référence d’objet.</span><span class="sxs-lookup"><span data-stu-id="c2105-108">A `Set` procedure sets a property to a value, including an object reference.</span></span> <span data-ttu-id="c2105-109">Il est appelé lorsque vous affectez une valeur à la propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-109">It is called when you assign a value to the property.</span></span>  
  
 <span data-ttu-id="c2105-110">Procédures de propriété sont généralement définies par paires, à l’aide de la `Get` et `Set` instructions, mais vous pouvez définir chaque procédure uniquement si la propriété est en lecture seule ([instruction Get](../../../../visual-basic/language-reference/statements/get-statement.md)) ou en écriture seule ([définie Instruction](../../../../visual-basic/language-reference/statements/set-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="c2105-110">You usually define property procedures in pairs, using the `Get` and `Set` statements, but you can define either procedure alone if the property is read-only ([Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md)) or write-only ([Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)).</span></span>  
  
 <span data-ttu-id="c2105-111">Vous pouvez omettre le `Get` et `Set` procédure lors de l’utilisation d’une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="c2105-111">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="c2105-112">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](./auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c2105-112">For more information, see [Auto-Implemented Properties](./auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="c2105-113">Vous pouvez définir des propriétés dans les classes, structures et les modules.</span><span class="sxs-lookup"><span data-stu-id="c2105-113">You can define properties in classes, structures, and modules.</span></span> <span data-ttu-id="c2105-114">Les propriétés sont `Public` par défaut, ce qui signifie que vous pouvez les appeler depuis n’importe où dans votre application qui peut accéder au conteneur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-114">Properties are `Public` by default, which means you can call them from anywhere in your application that can access the property's container.</span></span>  
  
 <span data-ttu-id="c2105-115">Pour obtenir une comparaison des propriétés et des variables, consultez [les différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md).</span><span class="sxs-lookup"><span data-stu-id="c2105-115">For a comparison of properties and variables, see [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md).</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="c2105-116">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="c2105-116">Declaration Syntax</span></span>  
 <span data-ttu-id="c2105-117">Une propriété est définie par un bloc de code placé entre le [Property, instruction](../../../../visual-basic/language-reference/statements/property-statement.md) et `End Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="c2105-117">A property itself is defined by a block of code enclosed within the [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) and the `End Property` statement.</span></span> <span data-ttu-id="c2105-118">À l’intérieur de ce bloc, chaque procédure de propriété apparaît sous la forme d’un bloc interne délimité par une instruction de déclaration (`Get` ou `Set`) et la mise en correspondance `End` déclaration.</span><span class="sxs-lookup"><span data-stu-id="c2105-118">Inside this block, each property procedure appears as an internal block enclosed within a declaration statement (`Get` or `Set`) and the matching `End` declaration.</span></span>  
  
 <span data-ttu-id="c2105-119">La syntaxe de déclaration d’une propriété et ses procédures est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c2105-119">The syntax for declaring a property and its procedures is as follows:</span></span>  
  
```  
[Default] [Modifiers] Property PropertyName[(ParameterList)] [As DataType]  
    [AccessLevel] Get  
        ' Statements of the Get procedure.  
        ' The following statement returns an expression as the property's value.  
        Return Expression  
    End Get  
    [AccessLevel] Set[(ByVal NewValue As DataType)]  
        ' Statements of the Set procedure.  
        ' The following statement assigns newvalue as the property's value.  
        LValue = NewValue  
    End Set  
End Property  
- or -  
[Default] [Modifiers] Property PropertyName [(ParameterList)] [As DataType]  
```  
  
 <span data-ttu-id="c2105-120">Le `Modifiers` peut spécifier de niveau d’accès et les informations concernant la surcharge, la substitution, le partage et l’occultation, ainsi que la propriété est en lecture seule ou en écriture seule.</span><span class="sxs-lookup"><span data-stu-id="c2105-120">The `Modifiers` can specify access level and information regarding overloading, overriding, sharing, and shadowing, as well as whether the property is read-only or write-only.</span></span> <span data-ttu-id="c2105-121">Le `AccessLevel` sur la `Get` ou `Set` procédure peut être n’importe quel niveau est plus restrictif que le niveau d’accès spécifié pour la propriété proprement dite.</span><span class="sxs-lookup"><span data-stu-id="c2105-121">The `AccessLevel` on the `Get` or `Set` procedure can be any level that is more restrictive than the access level specified for the property itself.</span></span> <span data-ttu-id="c2105-122">Pour plus d’informations, consultez [Property, instruction](../../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c2105-122">For more information, see [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="c2105-123">Type de données</span><span class="sxs-lookup"><span data-stu-id="c2105-123">Data Type</span></span>  
 <span data-ttu-id="c2105-124">Type de données d’une propriété et le niveau d’accès principal sont définis dans la `Property` instruction, pas dans les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-124">A property's data type and principal access level are defined in the `Property` statement, not in the property procedures.</span></span> <span data-ttu-id="c2105-125">Une propriété peut avoir uniquement un type de données.</span><span class="sxs-lookup"><span data-stu-id="c2105-125">A property can have only one data type.</span></span> <span data-ttu-id="c2105-126">Par exemple, vous ne pouvez pas définir une propriété pour stocker un `Decimal` valeur mais récupérer un `Double` valeur.</span><span class="sxs-lookup"><span data-stu-id="c2105-126">For example, you cannot define a property to store a `Decimal` value but retrieve a `Double` value.</span></span>  
  
### <a name="access-level"></a><span data-ttu-id="c2105-127">Niveau d’accès</span><span class="sxs-lookup"><span data-stu-id="c2105-127">Access Level</span></span>  
 <span data-ttu-id="c2105-128">Toutefois, vous pouvez définir un niveau d’accès principal pour une propriété et restreindre davantage le niveau d’accès de l’une de ses procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-128">However, you can define a principal access level for a property and further restrict the access level in one of its property procedures.</span></span> <span data-ttu-id="c2105-129">Par exemple, vous pouvez définir un `Public` propriété, puis définissez un `Private Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="c2105-129">For example, you can define a `Public` property and then define a `Private Set` procedure.</span></span> <span data-ttu-id="c2105-130">Le `Get` reste de la procédure `Public`.</span><span class="sxs-lookup"><span data-stu-id="c2105-130">The `Get` procedure remains `Public`.</span></span> <span data-ttu-id="c2105-131">Vous pouvez modifier le niveau d’accès dans l’une des procédures de la propriété, et vous pouvez uniquement le rendre plus restrictif que le niveau d’accès principal.</span><span class="sxs-lookup"><span data-stu-id="c2105-131">You can change the access level in only one of a property's procedures, and you can only make it more restrictive than the principal access level.</span></span> <span data-ttu-id="c2105-132">Pour plus d’informations, consultez [Comment : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="c2105-132">For more information, see [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="c2105-133">Déclaration de paramètre</span><span class="sxs-lookup"><span data-stu-id="c2105-133">Parameter Declaration</span></span>  
 <span data-ttu-id="c2105-134">Vous déclarez chaque paramètre de la même façon que vous le feriez pour [procédures Sub](./sub-procedures.md), sauf que le mécanisme de passage doit être `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="c2105-134">You declare each parameter the same way you do for [Sub Procedures](./sub-procedures.md), except that the passing mechanism must be `ByVal`.</span></span>  
  
 <span data-ttu-id="c2105-135">La syntaxe de chaque paramètre dans la liste de paramètres est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c2105-135">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 `[Optional] ByVal [ParamArray] parametername As datatype`  
  
 <span data-ttu-id="c2105-136">Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="c2105-136">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="c2105-137">La syntaxe pour spécifier une valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="c2105-137">The syntax for specifying a default value is as follows:</span></span>  
  
 `Optional ByVal parametername As datatype = defaultvalue`  
  
## <a name="property-value"></a><span data-ttu-id="c2105-138">Valeur de propriété</span><span class="sxs-lookup"><span data-stu-id="c2105-138">Property Value</span></span>  
 <span data-ttu-id="c2105-139">Dans un `Get` procédure, la valeur de retour est fournie à l’expression appelante en tant que la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-139">In a `Get` procedure, the return value is supplied to the calling expression as the value of the property.</span></span>  
  
 <span data-ttu-id="c2105-140">Dans un `Set` procédure, la nouvelle valeur de propriété est passée au paramètre de la `Set` instruction.</span><span class="sxs-lookup"><span data-stu-id="c2105-140">In a `Set` procedure, the new property value is passed to the parameter of the `Set` statement.</span></span> <span data-ttu-id="c2105-141">Si vous déclarez explicitement un paramètre, vous devez la déclarer avec le même type de données que la propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-141">If you explicitly declare a parameter, you must declare it with the same data type as the property.</span></span> <span data-ttu-id="c2105-142">Si vous ne déclarez pas un paramètre, le compilateur utilise le paramètre implicite `Value` pour représenter la nouvelle valeur à affecter à la propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-142">If you do not declare a parameter, the compiler uses the implicit parameter `Value` to represent the new value to be assigned to the property.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="c2105-143">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="c2105-143">Calling Syntax</span></span>  
 <span data-ttu-id="c2105-144">Vous appelez une procédure de propriété implicitement en faisant référence à la propriété.</span><span class="sxs-lookup"><span data-stu-id="c2105-144">You invoke a property procedure implicitly by making reference to the property.</span></span> <span data-ttu-id="c2105-145">Utiliser le nom de la propriété de la même façon que vous devez utiliser le nom d’une variable, sauf que vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c2105-145">You use the name of the property the same way you would use the name of a variable, except that you must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="c2105-146">Si aucun argument n’est fourni, vous pouvez omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c2105-146">If no arguments are supplied, you can optionally omit the parentheses.</span></span>  
  
 <span data-ttu-id="c2105-147">La syntaxe d’un appel implicite à un `Set` comme suit :</span><span class="sxs-lookup"><span data-stu-id="c2105-147">The syntax for an implicit call to a `Set` procedure is as follows:</span></span>  
  
 `propertyname[(argumentlist)] = expression`  
  
 <span data-ttu-id="c2105-148">La syntaxe d’un appel implicite à un `Get` comme suit :</span><span class="sxs-lookup"><span data-stu-id="c2105-148">The syntax for an implicit call to a `Get` procedure is as follows:</span></span>  
  
 `lvalue = propertyname[(argumentlist)]`  
  
 `Do While (propertyname[(argumentlist)] > expression)`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="c2105-149">Illustration de déclaration et d’appel</span><span class="sxs-lookup"><span data-stu-id="c2105-149">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="c2105-150">La propriété suivante stocke un nom complet en tant que les deux noms constitutifs, le prénom et le nom de famille.</span><span class="sxs-lookup"><span data-stu-id="c2105-150">The following property stores a full name as two constituent names, the first name and the last name.</span></span> <span data-ttu-id="c2105-151">Lorsque le code appelant lit `fullName`, le `Get` procédure combine les deux noms constitutifs et retourne le nom complet.</span><span class="sxs-lookup"><span data-stu-id="c2105-151">When the calling code reads `fullName`, the `Get` procedure combines the two constituent names and returns the full name.</span></span> <span data-ttu-id="c2105-152">Lorsque le code appelant assigne un nouveau nom complet, le `Set` procédure tente de diviser en deux noms constitutifs.</span><span class="sxs-lookup"><span data-stu-id="c2105-152">When the calling code assigns a new full name, the `Set` procedure attempts to break it into two constituent names.</span></span> <span data-ttu-id="c2105-153">S’il ne trouve pas d’un espace, il les stocke tout comme le prénom.</span><span class="sxs-lookup"><span data-stu-id="c2105-153">If it does not find a space, it stores it all as the first name.</span></span>  
  
 [!code-vb[VbVbcnProcedures#8](./codesnippet/VisualBasic/property-procedures_1.vb)]  
  
 <span data-ttu-id="c2105-154">L’exemple suivant montre des appels typiques aux procédures de propriété `fullName`.</span><span class="sxs-lookup"><span data-stu-id="c2105-154">The following example shows typical calls to the property procedures of `fullName`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#9](./codesnippet/VisualBasic/property-procedures_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="c2105-155">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c2105-155">See Also</span></span>  
 [<span data-ttu-id="c2105-156">Procédures</span><span class="sxs-lookup"><span data-stu-id="c2105-156">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="c2105-157">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="c2105-157">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="c2105-158">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="c2105-158">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="c2105-159">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="c2105-159">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c2105-160">Différences entre les propriétés et les Variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2105-160">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="c2105-161">Guide pratique : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="c2105-161">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="c2105-162">Guide pratique : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="c2105-162">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="c2105-163">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2105-163">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="c2105-164">Guide pratique : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="c2105-164">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="c2105-165">Guide pratique : obtenir une valeur d’une propriété</span><span class="sxs-lookup"><span data-stu-id="c2105-165">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)
