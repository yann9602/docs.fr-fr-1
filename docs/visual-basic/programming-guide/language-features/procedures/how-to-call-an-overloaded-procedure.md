---
title: "Comment : appeler une procédure surchargée (Visual Basic) | Documents Microsoft"
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
- procedures, overloading
- procedures, calling
- procedures, multiple versions
- procedure calls, overloaded
ms.assetid: 3bb331fb-f6bc-406f-9ca0-9609b497014c
caps.latest.revision: 12
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
ms.openlocfilehash: 777df0cc81a4e0518773a0e8cc98d590d1c0cf0d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-call-an-overloaded-procedure-visual-basic"></a><span data-ttu-id="a0aeb-102">Comment : appeler une procédure surchargée (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0aeb-102">How to: Call an Overloaded Procedure (Visual Basic)</span></span>
<span data-ttu-id="a0aeb-103">L’avantage de la surcharge d’une procédure est la flexibilité de l’appel.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-103">The advantage of overloading a procedure is in the flexibility of the call.</span></span> <span data-ttu-id="a0aeb-104">Le code appelant peut obtenir les informations que nécessaires pour passer à la procédure, puis appelez un seul nom de procédure, quel que soit les arguments qu’il passe.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-104">The calling code can obtain the information it needs to pass to the procedure and then call a single procedure name, no matter what arguments it is passing.</span></span>  
  
### <a name="to-call-a-procedure-that-has-more-than-one-version-defined"></a><span data-ttu-id="a0aeb-105">Pour appeler une procédure qui possède plusieurs versions définies</span><span class="sxs-lookup"><span data-stu-id="a0aeb-105">To call a procedure that has more than one version defined</span></span>  
  
1.  <span data-ttu-id="a0aeb-106">Dans le code appelant, déterminez les données à passer à la procédure.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-106">In the calling code, determine which data to pass to the procedure.</span></span>  
  
2.  <span data-ttu-id="a0aeb-107">Écrire l’appel de procédure normalement, présenter les données dans la liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-107">Write the procedure call in the normal way, presenting the data in the argument list.</span></span> <span data-ttu-id="a0aeb-108">Assurez-vous que les arguments correspondent à la liste des paramètres dans l’une des versions de la procédure.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-108">Be sure the arguments match the parameter list in one of the versions defined for the procedure.</span></span>  
  
3.  <span data-ttu-id="a0aeb-109">Vous n’avez pas à déterminer la version de la procédure à appeler.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-109">You do not have to determine which version of the procedure to call.</span></span> [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="a0aeb-110">transmet le contrôle à la version correspondant à votre liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-110"> passes control to the version matching your argument list.</span></span>  
  
     <span data-ttu-id="a0aeb-111">L’exemple suivant appelle la `post` procédure déclarée dans [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md).</span><span class="sxs-lookup"><span data-stu-id="a0aeb-111">The following example calls the `post` procedure declared in [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md).</span></span> <span data-ttu-id="a0aeb-112">Il obtient l’identification de client, détermine s’il est un `String` ou `Integer`, puis dans les deux cas, appelle la même procédure.</span><span class="sxs-lookup"><span data-stu-id="a0aeb-112">It obtains the customer identification, determines whether it is a `String` or an `Integer`, and then in either case calls the same procedure.</span></span>  
  
     <span data-ttu-id="a0aeb-113">[!code-vb[VbVbcnProcedures&#56;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0aeb-113">[!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_1.vb)]</span></span>  
  
     <span data-ttu-id="a0aeb-114">[!code-vb[VbVbcnProcedures&#57;](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="a0aeb-114">[!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/how-to-call-an-overloaded-procedure_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0aeb-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a0aeb-115">See Also</span></span>  
 <span data-ttu-id="a0aeb-116">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-116">[Procedures](./index.md) </span></span>  
<span data-ttu-id="a0aeb-117"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-117"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="a0aeb-118"> [Surcharge de procédure](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-118"> [Procedure Overloading](./procedure-overloading.md) </span></span>  
<span data-ttu-id="a0aeb-119"> [Procédures de dépannage](./troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-119"> [Troubleshooting Procedures](./troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="a0aeb-120"> [Comment : définir plusieurs Versions d’une procédure](./how-to-define-multiple-versions-of-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-120"> [How to: Define Multiple Versions of a Procedure](./how-to-define-multiple-versions-of-a-procedure.md) </span></span>  
<span data-ttu-id="a0aeb-121"> [Comment : surcharger une procédure qui accepte des paramètres optionnels](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-121"> [How to: Overload a Procedure that Takes Optional Parameters](./how-to-overload-a-procedure-that-takes-optional-parameters.md) </span></span>  
<span data-ttu-id="a0aeb-122"> [Comment : surcharger une procédure qui accepte un nombre indéfini de paramètres](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-122"> [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md) </span></span>  
<span data-ttu-id="a0aeb-123"> [Considérations sur les surcharges de procédures](./considerations-in-overloading-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-123"> [Considerations in Overloading Procedures](./considerations-in-overloading-procedures.md) </span></span>  
<span data-ttu-id="a0aeb-124"> [Résolution de surcharge](./overload-resolution.md) </span><span class="sxs-lookup"><span data-stu-id="a0aeb-124"> [Overload Resolution](./overload-resolution.md) </span></span>  
<span data-ttu-id="a0aeb-125"> [Surcharges](../../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="a0aeb-125"> [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>
