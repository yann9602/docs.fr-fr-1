---
title: "Comment : appeler une procédure qui ne retourne pas de valeur (Visual Basic) | Documents Microsoft"
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
- procedure calls, returning values
- Visual Basic code, procedures
- procedures, calling
ms.assetid: 259b49a3-a3c1-4254-ba8c-73cdc4127703
caps.latest.revision: 17
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
ms.openlocfilehash: 26120b763d2ecedb3aa43adb08e4c87c2b1e0be1
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-a-procedure-that-does-not-return-a-value-visual-basic"></a><span data-ttu-id="19c4a-102">Comment : appeler une procédure qui ne retourne pas de valeur (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="19c4a-102">How to: Call a Procedure that Does Not Return a Value (Visual Basic)</span></span>
<span data-ttu-id="19c4a-103">Un `Sub` procédure ne retourne pas de valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="19c4a-103">A `Sub` procedure does not return a value to the calling code.</span></span> <span data-ttu-id="19c4a-104">Vous l’appelez explicitement avec une instruction d’appel autonome.</span><span class="sxs-lookup"><span data-stu-id="19c4a-104">You call it explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="19c4a-105">Vous ne pouvez pas l’appeler en utilisant simplement son nom dans une expression.</span><span class="sxs-lookup"><span data-stu-id="19c4a-105">You cannot call it by simply using its name within an expression.</span></span>  
  
### <a name="to-call-a-sub-procedure"></a><span data-ttu-id="19c4a-106">Pour appeler une procédure Sub</span><span class="sxs-lookup"><span data-stu-id="19c4a-106">To call a Sub procedure</span></span>  
  
1.  <span data-ttu-id="19c4a-107">Spécifiez le nom de la `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="19c4a-107">Specify the name of the `Sub` procedure.</span></span>  
  
2.  <span data-ttu-id="19c4a-108">Suivre le nom de procédure avec des parenthèses pour encadrer la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="19c4a-108">Follow the procedure name with parentheses to enclose the argument list.</span></span> <span data-ttu-id="19c4a-109">S’il n’y a pas d’arguments, vous pouvez éventuellement omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="19c4a-109">If there are no arguments, you can optionally omit the parentheses.</span></span> <span data-ttu-id="19c4a-110">Toutefois, à l’aide de parenthèses rend votre code plus facile à lire.</span><span class="sxs-lookup"><span data-stu-id="19c4a-110">However, using the parentheses makes your code easier to read.</span></span>  
  
3.  <span data-ttu-id="19c4a-111">Placez les arguments dans la liste d’arguments entre parenthèses, séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="19c4a-111">Place the arguments in the argument list within the parentheses, separated by commas.</span></span> <span data-ttu-id="19c4a-112">Assurez-vous de fournir les arguments dans le même ordre que les `Sub` procédure définit les paramètres correspondants.</span><span class="sxs-lookup"><span data-stu-id="19c4a-112">Be sure you supply the arguments in the same order that the `Sub` procedure defines the corresponding parameters.</span></span>  
  
     <span data-ttu-id="19c4a-113">L’exemple suivant appelle la [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>fonction pour activer une fenêtre d’application.</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A></span><span class="sxs-lookup"><span data-stu-id="19c4a-113">The following example calls the [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] <xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> function to activate an application window.</span></span> <span data-ttu-id="19c4a-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A>accepte le titre de la fenêtre comme unique argument.</xref:Microsoft.VisualBasic.Interaction.AppActivate%2A></span><span class="sxs-lookup"><span data-stu-id="19c4a-114"><xref:Microsoft.VisualBasic.Interaction.AppActivate%2A> takes the window title as its sole argument.</span></span> <span data-ttu-id="19c4a-115">Il ne retourne pas de valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="19c4a-115">It does not return a value to the calling code.</span></span> <span data-ttu-id="19c4a-116">Si un processus Notepad n’est pas en cours d’exécution, l’exemple lève un <xref:System.ArgumentException>.</xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="19c4a-116">If a Notepad process is not running, the example throws an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="19c4a-117">Le `Shell` procédure suppose que les applications se trouvent dans les chemins d’accès spécifiés.</span><span class="sxs-lookup"><span data-stu-id="19c4a-117">The `Shell` procedure assumes the applications are in the paths specified.</span></span>  
  
     <span data-ttu-id="19c4a-118">[!code-vb[VbVbalrCatRef&#11;](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="19c4a-118">[!code-vb[VbVbalrCatRef#11](./codesnippet/VisualBasic/how-to-call-a-procedure-that-does-not-return-a-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c4a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="19c4a-119">See Also</span></span>  
 <span data-ttu-id="19c4a-120"><xref:Microsoft.VisualBasic.Interaction.Shell%2A></xref:Microsoft.VisualBasic.Interaction.Shell%2A></span><span class="sxs-lookup"><span data-stu-id="19c4a-120"><xref:Microsoft.VisualBasic.Interaction.Shell%2A></span></span>   
 <span data-ttu-id="19c4a-121"><xref:System.ArgumentException></xref:System.ArgumentException></span><span class="sxs-lookup"><span data-stu-id="19c4a-121"><xref:System.ArgumentException></span></span>   
<span data-ttu-id="19c4a-122"> [Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="19c4a-122"> [Procedures](./index.md) </span></span>  
<span data-ttu-id="19c4a-123"> [Procédures Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="19c4a-123"> [Sub Procedures](./sub-procedures.md) </span></span>  
<span data-ttu-id="19c4a-124"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="19c4a-124"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="19c4a-125"> [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="19c4a-125"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="19c4a-126"> [Comment : créer une procédure](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="19c4a-126"> [How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
<span data-ttu-id="19c4a-127"> [Comment : appeler une procédure qui retourne une valeur](./how-to-call-a-procedure-that-returns-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="19c4a-127"> [How to: Call a Procedure That Returns a Value](./how-to-call-a-procedure-that-returns-a-value.md) </span></span>  
<span data-ttu-id="19c4a-128"> [Comment : appeler un gestionnaire d’événements en Visual Basic](./how-to-call-an-event-handler.md)</span><span class="sxs-lookup"><span data-stu-id="19c4a-128"> [How to: Call an Event Handler in Visual Basic](./how-to-call-an-event-handler.md)</span></span>
