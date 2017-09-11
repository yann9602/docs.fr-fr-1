---
title: "Comment : obtenir une valeur d’une propriété (Visual Basic) | Documents Microsoft"
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
- property values
- Visual Basic code, procedures
- values, properties
- Visual Basic code, properties
- properties [Visual Basic], values
ms.assetid: 3954423e-6ab7-4a4c-b55c-a8d27be47891
caps.latest.revision: 11
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
ms.openlocfilehash: 719a4fc9ff163fb4437ea40c8265a5e36232347e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-get-a-value-from-a-property-visual-basic"></a><span data-ttu-id="8b0e7-102">Comment : obtenir une valeur d'une propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b0e7-102">How to: Get a Value from a Property (Visual Basic)</span></span>
<span data-ttu-id="8b0e7-103">Vous récupérez une valeur de propriété en incluant le nom de propriété dans une expression.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-103">You retrieve a property's value by including the property name in an expression.</span></span>  
  
 <span data-ttu-id="8b0e7-104">La propriété `Get` procédure récupère la valeur, mais vous ne l’appelez pas explicitement par son nom.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-104">The property's `Get` procedure retrieves the value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="8b0e7-105">Vous utilisez la propriété tout comme vous utiliseriez une variable.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="8b0e7-106">appelle les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-retrieve-a-value-from-a-property"></a><span data-ttu-id="8b0e7-107">Pour récupérer une valeur d’une propriété</span><span class="sxs-lookup"><span data-stu-id="8b0e7-107">To retrieve a value from a property</span></span>  
  
1.  <span data-ttu-id="8b0e7-108">Utiliser le nom de propriété dans une expression de la même manière que vous utiliseriez un nom de variable.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-108">Use the property name in an expression the same way you would use a variable name.</span></span> <span data-ttu-id="8b0e7-109">Vous pouvez utiliser une propriété partout où vous pouvez utiliser une variable ou une constante.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-109">You can use a property anywhere you can use a variable or a constant.</span></span>  
  
     <span data-ttu-id="8b0e7-110">ou</span><span class="sxs-lookup"><span data-stu-id="8b0e7-110">-or-</span></span>  
  
     <span data-ttu-id="8b0e7-111">Utilisez le nom de propriété suivant égaux (`=`) se connecter dans une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-111">Use the property name following the equal (`=`) sign in an assignment statement.</span></span>  
  
     <span data-ttu-id="8b0e7-112">L’exemple suivant lit la valeur de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `Now` propriété implicitement en appelant son `Get` procédure.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-112">The following example reads the value of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `Now` property, implicitly calling its `Get` procedure.</span></span>  
  
     <span data-ttu-id="8b0e7-113">[!code-vb[VbVbalrDateProperties n °&4;](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="8b0e7-113">[!code-vb[VbVbalrDateProperties#4](./codesnippet/VisualBasic/how-to-get-a-value-from-a-property_1.vb)]</span></span>  
  
2.  <span data-ttu-id="8b0e7-114">Si la propriété accepte des arguments, faites suivre le nom de propriété entre parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-114">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="8b0e7-115">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-115">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="8b0e7-116">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-116">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="8b0e7-117">Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-117">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
 <span data-ttu-id="8b0e7-118">La valeur de la propriété participe à l’expression comme une variable ou constante le ferait, ou il est stocké dans la variable ou la propriété sur le côté gauche de l’instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="8b0e7-118">The value of the property participates in the expression just as a variable or constant would, or it is stored in the variable or property on the left side of the assignment statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b0e7-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8b0e7-119">See Also</span></span>  
 <span data-ttu-id="8b0e7-120">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-120">[Procedures](./index.md) </span></span>  
<span data-ttu-id="8b0e7-121"> [Procédures de propriété](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-121"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="8b0e7-122"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-122"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="8b0e7-123"> [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-123"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="8b0e7-124"> [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-124"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="8b0e7-125"> [Comment : créer une propriété](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-125"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="8b0e7-126"> [Comment : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-126"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="8b0e7-127"> [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-127"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="8b0e7-128"> [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="8b0e7-128"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="8b0e7-129"> [Guide pratique : placer une valeur dans une propriété](./how-to-put-a-value-in-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="8b0e7-129"> [How to: Put a Value in a Property](./how-to-put-a-value-in-a-property.md)</span></span>
