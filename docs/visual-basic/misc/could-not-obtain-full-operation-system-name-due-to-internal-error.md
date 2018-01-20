---
title: "Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDiagnosticInfo_FullOSName
ms.assetid: f69da02b-eb9a-4284-bb9e-3025517ae6c1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e90de5a2fd0699a449e05b9c32e7450b8bdc991
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="could-not-obtain-full-operation-system-name-due-to-internal-error"></a><span data-ttu-id="9c2ce-102">Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne</span><span class="sxs-lookup"><span data-stu-id="9c2ce-102">Could not obtain full operation system name due to internal error</span></span>
<span data-ttu-id="9c2ce-103">Impossible d’obtenir le nom complet du système d’exploitation en raison d’une erreur interne.</span><span class="sxs-lookup"><span data-stu-id="9c2ce-103">Could not obtain full operation system name due to internal error.</span></span> <span data-ttu-id="9c2ce-104">Ceci peut être dû au fait que WMI est absent de l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="9c2ce-104">This might be caused by WMI not existing on the current machine.</span></span>  
  
 <span data-ttu-id="9c2ce-105">Un appel à la propriété `My.Computer.Info.OSFullName` a échoué.</span><span class="sxs-lookup"><span data-stu-id="9c2ce-105">A call to the `My.Computer.Info.OSFullName` property failed.</span></span> <span data-ttu-id="9c2ce-106">WMI (Windows Management Instrumentation) n’est peut-être pas installé sur l’ordinateur actuel.</span><span class="sxs-lookup"><span data-stu-id="9c2ce-106">A possible cause for this failure is if Windows Management Instrumentation (WMI) is not installed on the current computer.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9c2ce-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9c2ce-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="9c2ce-108">Ajoutez un bloc `Try...Catch` autour de l’appel à la propriété `My.Computer.Info.OSFullName` .</span><span class="sxs-lookup"><span data-stu-id="9c2ce-108">Add a `Try...Catch` block around the call to the `My.Computer.Info.OSFullName` property.</span></span>  
  
2.  <span data-ttu-id="9c2ce-109">Pour plus d’informations sur WMI et comment l’installer, accédez à et recherchez « Windows Management Instrumentation Core ».</span><span class="sxs-lookup"><span data-stu-id="9c2ce-109">For more information about WMI and how to install it, go to  and search for "Windows Management Instrumentation Core".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c2ce-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9c2ce-110">See Also</span></span>  
 [<span data-ttu-id="9c2ce-111">My.Computer.Info.OSFullName</span><span class="sxs-lookup"><span data-stu-id="9c2ce-111">My.Computer.Info.OSFullName</span></span>](xref:Microsoft.VisualBasic.Devices.ComputerInfo.OSFullName)  
 [<span data-ttu-id="9c2ce-112">Exceptions et gestion des erreurs dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9c2ce-112">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/library/3e351e73-cf23-40ab-8b60-05794160529e)  
 [<span data-ttu-id="9c2ce-113">Try...Catch...Finally (instruction)</span><span class="sxs-lookup"><span data-stu-id="9c2ce-113">Try...Catch...Finally Statement</span></span>](../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
