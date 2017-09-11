---
title: "Comment : appeler une procédure de propriété (Visual Basic) | Documents Microsoft"
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
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures, calling
- properties [Visual Basic], property procedures
- procedure calls, property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: 16
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
ms.openlocfilehash: d0d37fc2b7ae1d563a7e9d0a8e75343dd690089b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="73018-102">Comment : appeler une procédure de propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="73018-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="73018-103">Vous appelez une procédure de propriété en stockant une valeur dans la propriété ou de récupérer sa valeur.</span><span class="sxs-lookup"><span data-stu-id="73018-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="73018-104">Vous accédez à une propriété la même façon que vous accédez à une variable.</span><span class="sxs-lookup"><span data-stu-id="73018-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="73018-105">La propriété `Set` stocke une valeur et ses `Get` procédure récupère la valeur.</span><span class="sxs-lookup"><span data-stu-id="73018-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="73018-106">Toutefois, vous n’appelez pas explicitement ces procédures par nom.</span><span class="sxs-lookup"><span data-stu-id="73018-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="73018-107">Vous utilisez la propriété dans une instruction d’assignation ou une expression, comme vous stockiez ou récupérer la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="73018-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="73018-108">appelle les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="73018-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="73018-109">Pour appeler une procédure Get d’une propriété</span><span class="sxs-lookup"><span data-stu-id="73018-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="73018-110">Utiliser le nom de propriété dans une expression de la même manière que vous utiliseriez un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="73018-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="73018-111">Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.</span><span class="sxs-lookup"><span data-stu-id="73018-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="73018-112">ou</span><span class="sxs-lookup"><span data-stu-id="73018-112">-or-</span></span>  
  
     <span data-ttu-id="73018-113">Utilisez le nom de propriété suivant égaux (`=`) se connecter dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="73018-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="73018-114">L’exemple suivant lit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.Now%2A>propriété implicitement en appelant son `Get` procédure.</xref:Microsoft.VisualBasic.DateAndTime.Now%2A></span><span class="sxs-lookup"><span data-stu-id="73018-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     <span data-ttu-id="73018-115">[!code-vb[VbVbalrDateProperties n °&4;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="73018-115">[!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]</span></span>  
  
2.  <span data-ttu-id="73018-116">Si la propriété accepte des arguments, faites suivre le nom de propriété entre parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="73018-116">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="73018-117">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="73018-117">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="73018-118">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="73018-118">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="73018-119">Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="73018-119">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="73018-120">La valeur de la propriété participe à l’expression comme une variable ou constante le ferait, ou il est stocké dans la variable ou la propriété sur le côté gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="73018-120">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="73018-121">Pour appeler une propriété Set de la procédure</span><span class="sxs-lookup"><span data-stu-id="73018-121">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="73018-122">Utilisez le nom de propriété sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="73018-122">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="73018-123">L’exemple suivant définit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A>propriété implicitement en appelant le `Set` procédure.</xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span><span class="sxs-lookup"><span data-stu-id="73018-123">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     <span data-ttu-id="73018-124">[!code-vb[VbVbcnProcedures&#11;](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="73018-124">[!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]</span></span>  
  
2.  <span data-ttu-id="73018-125">Si la propriété accepte des arguments, faites suivre le nom de propriété entre parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="73018-125">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="73018-126">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="73018-126">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="73018-127">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="73018-127">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="73018-128">Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="73018-128">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="73018-129">La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="73018-129">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73018-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="73018-130">See Also</span></span>  
 <span data-ttu-id="73018-131">[Procédures de propriété](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="73018-131">[Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="73018-132"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="73018-132"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="73018-133"> [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="73018-133"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="73018-134"> [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="73018-134"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="73018-135"> [Comment : créer une propriété](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="73018-135"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="73018-136"> [Comment : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="73018-136"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="73018-137"> [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="73018-137"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="73018-138"> [Comment : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="73018-138"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md) </span></span>  
<span data-ttu-id="73018-139"> [Comment : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="73018-139"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md) </span></span>  
<span data-ttu-id="73018-140"> [Get (instruction)](../../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="73018-140"> [Get Statement](../../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="73018-141"> [Set (instruction)](../../../../visual-basic/language-reference/statements/set-statement.md)</span><span class="sxs-lookup"><span data-stu-id="73018-141"> [Set Statement](../../../../visual-basic/language-reference/statements/set-statement.md)</span></span>
