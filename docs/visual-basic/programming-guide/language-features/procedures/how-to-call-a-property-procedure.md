---
title: "Comment : appeler une procédure de propriété (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- Visual Basic code, properties
- procedures [Visual Basic], calling
- properties [Visual Basic], property procedures
- procedure calls [Visual Basic], property procedures
ms.assetid: 96bc4d74-d9c3-4b7a-954d-58ac8553cd94
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf9080e3c2b23302257499f13e734231f3614495
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-call-a-property-procedure-visual-basic"></a><span data-ttu-id="c198f-102">Comment : appeler une procédure de propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c198f-102">How to: Call a Property Procedure (Visual Basic)</span></span>
<span data-ttu-id="c198f-103">Vous appelez une procédure de propriété en stockant une valeur dans la propriété ou de récupérer sa valeur.</span><span class="sxs-lookup"><span data-stu-id="c198f-103">You call a property procedure by storing a value in the property or retrieving its value.</span></span> <span data-ttu-id="c198f-104">Vous accédez à une propriété la même façon que vous accédez à une variable.</span><span class="sxs-lookup"><span data-stu-id="c198f-104">You access a property the same way you access a variable.</span></span>  
  
 <span data-ttu-id="c198f-105">La propriété `Set` stocke une valeur et son `Get` procédure récupère la valeur.</span><span class="sxs-lookup"><span data-stu-id="c198f-105">The property's `Set` procedure stores a value, and its `Get` procedure retrieves the value.</span></span> <span data-ttu-id="c198f-106">Toutefois, vous n’appelez pas explicitement ces procédures par nom.</span><span class="sxs-lookup"><span data-stu-id="c198f-106">However, you do not explicitly call these procedures by name.</span></span> <span data-ttu-id="c198f-107">Vous utilisez la propriété dans une instruction d’assignation ou une expression, tout comme vous permet de stocker ou récupérer la valeur d’une variable.</span><span class="sxs-lookup"><span data-stu-id="c198f-107">You use the property in an assignment statement or an expression, just as you would store or retrieve the value of a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="c198f-108">appelle les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="c198f-108"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-call-a-propertys-get-procedure"></a><span data-ttu-id="c198f-109">Pour appeler la procédure d’obtention d’une propriété</span><span class="sxs-lookup"><span data-stu-id="c198f-109">To call a property's Get procedure</span></span>  
  
1.  <span data-ttu-id="c198f-110">Utilisez le nom de propriété dans une expression de la même façon que vous utiliseriez un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="c198f-110">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="c198f-111">Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.</span><span class="sxs-lookup"><span data-stu-id="c198f-111">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="c198f-112">ou</span><span class="sxs-lookup"><span data-stu-id="c198f-112">-or-</span></span>  
  
     <span data-ttu-id="c198f-113">Utilisez le nom de propriété suivant égaux (`=`) connectez-vous à une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="c198f-113">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="c198f-114">L’exemple suivant lit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> propriété implicitement en appelant son `Get` procédure.</span><span class="sxs-lookup"><span data-stu-id="c198f-114">The following example reads the value of the <xref:Microsoft.VisualBasic.DateAndTime.Now%2A> property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-call-a-property-procedure_1.vb)]  
  
2.  <span data-ttu-id="c198f-115">Si la propriété accepte des arguments, faites suivre le nom de propriété avec des parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="c198f-115">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="c198f-116">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c198f-116">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="c198f-117">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c198f-117">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="c198f-118">Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="c198f-118">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="c198f-119">La valeur de la propriété participe à l’expression comme une variable ou constante serait, ou il est stocké dans la variable ou propriété sur le côté gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="c198f-119">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
### <a name="to-call-a-propertys-set-procedure"></a><span data-ttu-id="c198f-120">Pour appeler une propriété Set de la procédure</span><span class="sxs-lookup"><span data-stu-id="c198f-120">To call a property's Set procedure</span></span>  
  
1.  <span data-ttu-id="c198f-121">Utilisez le nom de propriété sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="c198f-121">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="c198f-122">L’exemple suivant définit la valeur de la <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> propriété implicitement en appelant le `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="c198f-122">The following example sets the value of the <xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A> property, implicitly calling the `Set` procedure.</span></span>  
  
     [!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-call-a-property-procedure_2.vb)]  
  
2.  <span data-ttu-id="c198f-123">Si la propriété accepte des arguments, faites suivre le nom de propriété avec des parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="c198f-123">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="c198f-124">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="c198f-124">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="c198f-125">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="c198f-125">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="c198f-126">Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="c198f-126">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="c198f-127">La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="c198f-127">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c198f-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c198f-128">See Also</span></span>  
 [<span data-ttu-id="c198f-129">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="c198f-129">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="c198f-130">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="c198f-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="c198f-131">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="c198f-131">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="c198f-132">Différences entre les propriétés et les Variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c198f-132">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="c198f-133">Guide pratique : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="c198f-133">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="c198f-134">Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes</span><span class="sxs-lookup"><span data-stu-id="c198f-134">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="c198f-135">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c198f-135">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="c198f-136">Guide pratique : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="c198f-136">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)  
 [<span data-ttu-id="c198f-137">Guide pratique : obtenir une valeur d’une propriété</span><span class="sxs-lookup"><span data-stu-id="c198f-137">How to: Get a Value from a Property</span></span>](./how-to-get-a-value-from-a-property.md)  
 [<span data-ttu-id="c198f-138">Get (instruction)</span><span class="sxs-lookup"><span data-stu-id="c198f-138">Get Statement</span></span>](../../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="c198f-139">Set (instruction)</span><span class="sxs-lookup"><span data-stu-id="c198f-139">Set Statement</span></span>](../../../../visual-basic/language-reference/statements/set-statement.md)
