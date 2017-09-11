---
title: "Comment : déclarer et appeler une propriété par défaut en Visual Basic | Documents Microsoft"
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
- defaults, properties
- properties [Visual Basic], default
- procedures, defining
- default properties, in Visual Basic
- Visual Basic code, procedures
- Visual Basic code, properties
- default properties
ms.assetid: 68b4026e-09ef-4613-808e-f6287494ff63
caps.latest.revision: 23
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
ms.openlocfilehash: 7cfd476def67ccf46e524da7943680f9e34b6a26
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-declare-and-call-a-default-property-in-visual-basic"></a><span data-ttu-id="7a875-102">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7a875-102">How to: Declare and Call a Default Property in Visual Basic</span></span>
<span data-ttu-id="7a875-103">A *propriété par défaut* est une propriété de classe ou structure que votre code peut accéder sans la spécifier.</span><span class="sxs-lookup"><span data-stu-id="7a875-103">A *default property* is a class or structure property that your code can access without specifying it.</span></span> <span data-ttu-id="7a875-104">Lorsque le code appelant nomme une classe ou de structure, mais pas une propriété, et le contexte autorise l’accès à une propriété, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] résout l’accès à cette classe ou de la propriété par défaut de la structure s’il en existe.</span><span class="sxs-lookup"><span data-stu-id="7a875-104">When calling code names a class or structure but not a property, and the context allows access to a property, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] resolves the access to that class or structure's default property if one exists.</span></span>  
  
 <span data-ttu-id="7a875-105">Une classe ou structure peut avoir au plus une propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="7a875-105">A class or structure can have at most one default property.</span></span> <span data-ttu-id="7a875-106">Toutefois, vous pouvez surcharger une propriété par défaut et avoir plusieurs versions de celui-ci.</span><span class="sxs-lookup"><span data-stu-id="7a875-106">However, you can overload a default property and have more than one version of it.</span></span>  
  
 <span data-ttu-id="7a875-107">Pour plus d’informations, consultez [par défaut](../../../../visual-basic/language-reference/modifiers/default.md).</span><span class="sxs-lookup"><span data-stu-id="7a875-107">For more information, see [Default](../../../../visual-basic/language-reference/modifiers/default.md).</span></span>  
  
### <a name="to-declare-a-default-property"></a><span data-ttu-id="7a875-108">Pour déclarer une propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="7a875-108">To declare a default property</span></span>  
  
1.  <span data-ttu-id="7a875-109">Déclarez la propriété de façon normale.</span><span class="sxs-lookup"><span data-stu-id="7a875-109">Declare the property in the normal way.</span></span> <span data-ttu-id="7a875-110">Ne spécifiez pas le `Shared` ou `Private` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="7a875-110">Do not specify the `Shared` or `Private` keyword.</span></span>  
  
2.  <span data-ttu-id="7a875-111">Inclure le `Default` mot clé dans la déclaration de propriété.</span><span class="sxs-lookup"><span data-stu-id="7a875-111">Include the `Default` keyword in the property declaration.</span></span>  
  
3.  <span data-ttu-id="7a875-112">Spécifiez au moins un paramètre de la propriété.</span><span class="sxs-lookup"><span data-stu-id="7a875-112">Specify at least one parameter for the property.</span></span> <span data-ttu-id="7a875-113">Vous ne pouvez pas définir une propriété par défaut qui ne prend pas au moins un argument.</span><span class="sxs-lookup"><span data-stu-id="7a875-113">You cannot define a default property that does not take at least one argument.</span></span>  
  
     <span data-ttu-id="7a875-114">[!code-vb[VbVbcnProcedures&#17;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-114">[!code-vb[VbVbcnProcedures#17](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_1.vb)]</span></span>  
  
### <a name="to-call-a-default-property"></a><span data-ttu-id="7a875-115">Pour appeler une propriété par défaut</span><span class="sxs-lookup"><span data-stu-id="7a875-115">To call a default property</span></span>  
  
1.  <span data-ttu-id="7a875-116">Déclarez une variable du type classe ou la structure conteneur.</span><span class="sxs-lookup"><span data-stu-id="7a875-116">Declare a variable of the containing class or structure type.</span></span>  
  
     <span data-ttu-id="7a875-117">[!code-vb[VbVbcnProcedures&#16;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-117">[!code-vb[VbVbcnProcedures#16](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_2.vb)]</span></span>  
  
2.  <span data-ttu-id="7a875-118">Utilisez le nom de variable seul dans une expression où vous incluriez normalement le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="7a875-118">Use the variable name alone in an expression where you would normally include the property name.</span></span>  
  
     <span data-ttu-id="7a875-119">[!code-vb[VbVbcnProcedures n °&21;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-119">[!code-vb[VbVbcnProcedures#21](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_3.vb)]</span></span>  
  
3.  <span data-ttu-id="7a875-120">Suivre le nom de variable avec une liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7a875-120">Follow the variable name with an argument list in parentheses.</span></span> <span data-ttu-id="7a875-121">Une propriété par défaut doit prendre au moins un argument.</span><span class="sxs-lookup"><span data-stu-id="7a875-121">A default property must take at least one argument.</span></span>  
  
     <span data-ttu-id="7a875-122">[!code-vb[VbVbcnProcedures&#20;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-122">[!code-vb[VbVbcnProcedures#20](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_4.vb)]</span></span>  
  
4.  <span data-ttu-id="7a875-123">Pour récupérer la valeur de propriété par défaut, utilisez le nom de variable avec une liste d’arguments dans une expression ou après l’égal (`=`) se connecter dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="7a875-123">To retrieve the default property value, use the variable name, with an argument list, in an expression or following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="7a875-124">[!code-vb[VbVbcnProcedures&#15;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-124">[!code-vb[VbVbcnProcedures#15](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_5.vb)]</span></span>  
  
5.  <span data-ttu-id="7a875-125">Pour définir la valeur de propriété par défaut, utilisez le nom de variable avec une liste d’arguments, sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="7a875-125">To set the default property value, use the variable name, with an argument list, on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="7a875-126">[!code-vb[VbVbcnProcedures&#14;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-126">[!code-vb[VbVbcnProcedures#14](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_6.vb)]</span></span>  
  
6.  <span data-ttu-id="7a875-127">Vous pouvez toujours spécifier le nom de propriété par défaut avec le nom de variable, comme vous le feriez pour accéder à n’importe quelle autre propriété.</span><span class="sxs-lookup"><span data-stu-id="7a875-127">You can always specify the default property name together with the variable name, just as you would do to access any other property.</span></span>  
  
     <span data-ttu-id="7a875-128">[!code-vb[VbVbcnProcedures n °&19;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-128">[!code-vb[VbVbcnProcedures#19](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_7.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a875-129">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a875-129">Example</span></span>  
 <span data-ttu-id="7a875-130">L’exemple suivant déclare une propriété par défaut sur une classe.</span><span class="sxs-lookup"><span data-stu-id="7a875-130">The following example declares a default property on a class.</span></span>  
  
 <span data-ttu-id="7a875-131">[!code-vb[VbVbcnProcedures&#12;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-131">[!code-vb[VbVbcnProcedures#12](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_8.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a875-132">Exemple</span><span class="sxs-lookup"><span data-stu-id="7a875-132">Example</span></span>  
 <span data-ttu-id="7a875-133">L’exemple suivant montre comment appeler la propriété par défaut `myProperty` sur la classe `class1`.</span><span class="sxs-lookup"><span data-stu-id="7a875-133">The following example demonstrates how to call the default property `myProperty` on class `class1`.</span></span> <span data-ttu-id="7a875-134">Stockent des valeurs dans les trois instructions d’assignation `myProperty`et le <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>appel lit les valeurs.</xref:Microsoft.VisualBasic.Interaction.MsgBox%2A></span><span class="sxs-lookup"><span data-stu-id="7a875-134">The three assignment statements store values in `myProperty`, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> call reads the values.</span></span>  
  
 <span data-ttu-id="7a875-135">[!code-vb[VbVbcnProcedures&#13;](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]</span><span class="sxs-lookup"><span data-stu-id="7a875-135">[!code-vb[VbVbcnProcedures#13](./codesnippet/VisualBasic/how-to-declare-and-call-a-default-property_9.vb)]</span></span>  
  
 <span data-ttu-id="7a875-136">L’utilisation la plus courante d’une propriété par défaut est le <xref:Microsoft.VisualBasic.Collection.Item%2A>propriété sur différentes classes de collection.</xref:Microsoft.VisualBasic.Collection.Item%2A></span><span class="sxs-lookup"><span data-stu-id="7a875-136">The most common use of a default property is the <xref:Microsoft.VisualBasic.Collection.Item%2A> property on various collection classes.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7a875-137">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="7a875-137">Robust Programming</span></span>  
 <span data-ttu-id="7a875-138">Propriétés par défaut peuvent entraîner une légère réduction de caractères de code source, mais ils peuvent rendre votre code plus difficile à lire.</span><span class="sxs-lookup"><span data-stu-id="7a875-138">Default properties can result in a small reduction in source code-characters, but they can make your code more difficult to read.</span></span> <span data-ttu-id="7a875-139">Si le code appelant n’est pas familiarisé avec votre classe ou structure, lorsqu’il fait référence au nom de classe ou structure qu’il n’est pas sûr si cette référence accède à la classe ou structure elle-même ou à une propriété par défaut.</span><span class="sxs-lookup"><span data-stu-id="7a875-139">If the calling code is not familiar with your class or structure, when it makes a reference to the class or structure name it cannot be certain whether that reference accesses the class or structure itself, or a default property.</span></span> <span data-ttu-id="7a875-140">Cela peut entraîner des erreurs du compilateur ou des erreurs de logique d’exécution subtiles.</span><span class="sxs-lookup"><span data-stu-id="7a875-140">This can lead to compiler errors or subtle run-time logic errors.</span></span>  
  
 <span data-ttu-id="7a875-141">Vous pouvez légèrement réduire le risque d’erreurs de propriété par défaut en utilisant toujours le [Option Strict, instruction](../../../../visual-basic/language-reference/statements/option-strict-statement.md) pour définir le contrôle de type de compilateur `On`.</span><span class="sxs-lookup"><span data-stu-id="7a875-141">You can somewhat reduce the chance of default property errors by always using the [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md) to set compiler type checking to `On`.</span></span>  
  
 <span data-ttu-id="7a875-142">Si vous envisagez d’utiliser une structure ou classe prédéfini dans votre code, vous devez déterminer s’il possède une propriété par défaut et si tel est le cas, ce que son nom est.</span><span class="sxs-lookup"><span data-stu-id="7a875-142">If you are planning to use a predefined class or structure in your code, you must determine whether it has a default property, and if so, what its name is.</span></span>  
  
 <span data-ttu-id="7a875-143">En raison de ces inconvénients, vous devez envisager de ne pas définir de propriétés par défaut.</span><span class="sxs-lookup"><span data-stu-id="7a875-143">Because of these disadvantages, you should consider not defining default properties.</span></span> <span data-ttu-id="7a875-144">Pour une meilleure lisibilité du code, vous devez également envisager de toujours faire explicitement référence à toutes les propriétés, même les propriétés par défaut.</span><span class="sxs-lookup"><span data-stu-id="7a875-144">For code readability, you should also consider always referring to all properties explicitly, even default properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a875-145">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7a875-145">See Also</span></span>  
 <span data-ttu-id="7a875-146">[Procédures de propriété](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-146">[Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="7a875-147"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-147"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="7a875-148"> [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-148"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="7a875-149"> [Par défaut](../../../../visual-basic/language-reference/modifiers/default.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-149"> [Default](../../../../visual-basic/language-reference/modifiers/default.md) </span></span>  
<span data-ttu-id="7a875-150"> [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-150"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="7a875-151"> [Comment : créer une propriété](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-151"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="7a875-152"> [Comment : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-152"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="7a875-153"> [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-153"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="7a875-154"> [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="7a875-154"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="7a875-155"> [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="7a875-155"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
