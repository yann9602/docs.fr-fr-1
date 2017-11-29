---
title: "Comment : obtenir une valeur d'une propriété (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- property values [Visual Basic]
- Visual Basic code, procedures
- values [Visual Basic], properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6cde5408ea09398a79a3da01ae9b2d0202c58eaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="63941-102">Comment : obtenir une valeur d'une propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="63941-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="63941-103">Y compris le nom de propriété dans une expression permet de récupérer une valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="63941-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="63941-104">La propriété `Get` procédure récupère la valeur, mais vous ne l’appelez pas explicitement par son nom.</span><span class="sxs-lookup"><span data-stu-id="63941-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="63941-105">Vous utilisez la propriété comme vous utiliseriez une variable.</span><span class="sxs-lookup"><span data-stu-id="63941-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="63941-106">appelle les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="63941-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="63941-107">Pour récupérer une valeur d’une propriété</span><span class="sxs-lookup"><span data-stu-id="63941-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="63941-108">Utilisez le nom de propriété dans une expression de la même façon que vous utiliseriez un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="63941-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="63941-109">Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.</span><span class="sxs-lookup"><span data-stu-id="63941-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="63941-110">ou</span><span class="sxs-lookup"><span data-stu-id="63941-110">-or-</span></span>  
  
     <span data-ttu-id="63941-111">Utilisez le nom de propriété suivant égaux (`=`) connectez-vous à une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="63941-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="63941-112">L’exemple suivant lit la valeur de la [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` propriété implicitement en appelant son `Get` procédure.</span><span class="sxs-lookup"><span data-stu-id="63941-112">The following example reads the value of the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     [!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]  
  
2.  <span data-ttu-id="63941-113">Si la propriété accepte des arguments, faites suivre le nom de propriété avec des parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="63941-113">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="63941-114">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="63941-114">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="63941-115">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="63941-115">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="63941-116">Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="63941-116">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="63941-117">La valeur de la propriété participe à l’expression comme une variable ou constante serait, ou il est stocké dans la variable ou propriété sur le côté gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="63941-117">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63941-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63941-118">See Also</span></span>  
 [<span data-ttu-id="63941-119">Procédures</span><span class="sxs-lookup"><span data-stu-id="63941-119">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="63941-120">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="63941-120">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="63941-121">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="63941-121">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="63941-122">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="63941-122">Property Statement</span></span>](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="63941-123">Différences entre les propriétés et les Variables en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63941-123">Differences Between Properties and Variables in Visual Basic</span></span>](./differences-between-properties-and-variables.md)  
 [<span data-ttu-id="63941-124">Guide pratique : créer une propriété</span><span class="sxs-lookup"><span data-stu-id="63941-124">How to: Create a Property</span></span>](./how-to-create-a-property.md)  
 [<span data-ttu-id="63941-125">Guide pratique : déclarer une propriété avec des niveaux d’accès mixtes</span><span class="sxs-lookup"><span data-stu-id="63941-125">How to: Declare a Property with Mixed Access Levels</span></span>](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [<span data-ttu-id="63941-126">Guide pratique : appeler une procédure de propriété</span><span class="sxs-lookup"><span data-stu-id="63941-126">How to: Call a Property Procedure</span></span>](./how-to-call-a-property-procedure.md)  
 [<span data-ttu-id="63941-127">Comment : déclarer et appeler une propriété par défaut en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63941-127">How to: Declare and Call a Default Property in Visual Basic</span></span>](./how-to-declare-and-call-a-default-property.md)  
 [<span data-ttu-id="63941-128">Guide pratique : placer une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="63941-128">How to: Put a Value in a Property</span></span>](./how-to-put-a-value-in-a-property.md)
