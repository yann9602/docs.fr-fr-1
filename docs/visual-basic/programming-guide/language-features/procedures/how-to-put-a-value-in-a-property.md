---
title: "Comment : placer une valeur dans une propriété (Visual Basic) | Documents Microsoft"
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
ms.assetid: c39401e5-b5fc-4439-8f31-ed640f7ce6ed
caps.latest.revision: 13
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
ms.openlocfilehash: c838141a27c30b11765d30ae8b0c19bccc929f4b
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-put-a-value-in-a-property-visual-basic"></a><span data-ttu-id="35fa0-102">Comment : placer une valeur dans une propriété (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35fa0-102">How to: Put a Value in a Property (Visual Basic)</span></span>
<span data-ttu-id="35fa0-103">Vous stockez une valeur dans une propriété en plaçant le nom de propriété sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="35fa0-103">You store a value in a property by putting the property name on the left side of an assignment statement.</span></span>  
  
 <span data-ttu-id="35fa0-104">La propriété `Set` stocke une valeur, mais vous ne l’appelez pas explicitement par son nom.</span><span class="sxs-lookup"><span data-stu-id="35fa0-104">The property's `Set` procedure stores a value, but you do not explicitly call it by name.</span></span> <span data-ttu-id="35fa0-105">Vous utilisez la propriété tout comme vous utiliseriez une variable.</span><span class="sxs-lookup"><span data-stu-id="35fa0-105">You use the property just as you would use a variable.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="35fa0-106">appelle les procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="35fa0-106"> makes the calls to the property's procedures.</span></span>  
  
### <a name="to-store-a-value-in-a-property"></a><span data-ttu-id="35fa0-107">Pour stocker une valeur dans une propriété</span><span class="sxs-lookup"><span data-stu-id="35fa0-107">To store a value in a property</span></span>  
  
1.  <span data-ttu-id="35fa0-108">Utilisez le nom de propriété sur le côté gauche d’une instruction d’assignation.</span><span class="sxs-lookup"><span data-stu-id="35fa0-108">Use the property name on the left side of an assignment statement.</span></span>  
  
     <span data-ttu-id="35fa0-109">L’exemple suivant définit la valeur de la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `TimeOfDay` propriété MIDI, en appelant implicitement sa `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="35fa0-109">The following example sets the value of the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] `TimeOfDay` property to noon, implicitly calling its `Set` procedure.</span></span>  
  
     <span data-ttu-id="35fa0-110">[!code-vb[VbVbcnProcedures&#11;](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="35fa0-110">[!code-vb[VbVbcnProcedures#11](./codesnippet/VisualBasic/how-to-put-a-value-in-a-property_1.vb)]</span></span>  
  
2.  <span data-ttu-id="35fa0-111">Si la propriété accepte des arguments, faites suivre le nom de propriété entre parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="35fa0-111">If the property takes arguments, follow the property name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="35fa0-112">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="35fa0-112">If there are no arguments, you can optionally omit the parentheses.</span></span>  
  
3.  <span data-ttu-id="35fa0-113">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="35fa0-113">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="35fa0-114">Assurez-vous de que fournir les arguments dans le même ordre que la propriété définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="35fa0-114">Be sure you supply the arguments in the same order that the property defines the corresponding parameters.</span></span>  
  
4.  <span data-ttu-id="35fa0-115">La valeur générée sur le côté droit de l’instruction d’assignation est stockée dans la propriété.</span><span class="sxs-lookup"><span data-stu-id="35fa0-115">The value generated on the right side of the assignment statement is stored in the property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fa0-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35fa0-116">See Also</span></span>  
 <span data-ttu-id="35fa0-117"><xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span><span class="sxs-lookup"><span data-stu-id="35fa0-117"><xref:Microsoft.VisualBasic.DateAndTime.TimeOfDay%2A></span></span>   
<span data-ttu-id="35fa0-118"> [Procédures de propriété](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="35fa0-118"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="35fa0-119"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="35fa0-119"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="35fa0-120"> [Property (instruction)](../../../../visual-basic/language-reference/statements/property-statement.md) </span><span class="sxs-lookup"><span data-stu-id="35fa0-120"> [Property Statement](../../../../visual-basic/language-reference/statements/property-statement.md) </span></span>  
<span data-ttu-id="35fa0-121"> [Différences entre les propriétés et les Variables en Visual Basic](./differences-between-properties-and-variables.md) </span><span class="sxs-lookup"><span data-stu-id="35fa0-121"> [Differences Between Properties and Variables in Visual Basic](./differences-between-properties-and-variables.md) </span></span>  
<span data-ttu-id="35fa0-122"> [Comment : créer une propriété](./how-to-create-a-property.md) </span><span class="sxs-lookup"><span data-stu-id="35fa0-122"> [How to: Create a Property](./how-to-create-a-property.md) </span></span>  
<span data-ttu-id="35fa0-123"> [Comment : déclarer une propriété avec des niveaux d’accès mixtes](./how-to-declare-a-property-with-mixed-access-levels.md) </span><span class="sxs-lookup"><span data-stu-id="35fa0-123"> [How to: Declare a Property with Mixed Access Levels](./how-to-declare-a-property-with-mixed-access-levels.md) </span></span>  
<span data-ttu-id="35fa0-124"> [Comment : appeler une procédure de propriété](./how-to-call-a-property-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="35fa0-124"> [How to: Call a Property Procedure](./how-to-call-a-property-procedure.md) </span></span>  
<span data-ttu-id="35fa0-125"> [Comment : déclarer et appeler une propriété par défaut en Visual Basic](./how-to-declare-and-call-a-default-property.md) </span><span class="sxs-lookup"><span data-stu-id="35fa0-125"> [How to: Declare and Call a Default Property in Visual Basic](./how-to-declare-and-call-a-default-property.md) </span></span>  
<span data-ttu-id="35fa0-126"> [Guide pratique : obtenir une valeur d’une propriété](./how-to-get-a-value-from-a-property.md)</span><span class="sxs-lookup"><span data-stu-id="35fa0-126"> [How to: Get a Value from a Property](./how-to-get-a-value-from-a-property.md)</span></span>
