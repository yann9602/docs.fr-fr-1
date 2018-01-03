---
title: Absence de roulette de souris
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrMouse_NoWheelIsPresent
ms.assetid: e924ffba-4af1-4247-9a6f-d19a03738f62
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c96f6efed793cfcd4a1a23099e2bba1f01e53437
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="no-mouse-wheel-is-present"></a><span data-ttu-id="6d3d7-102">Absence de roulette de souris</span><span class="sxs-lookup"><span data-stu-id="6d3d7-102">No mouse wheel is present</span></span>
<span data-ttu-id="6d3d7-103">La propriété `My.Computer.Mouse.WheelScrollLines` a été appelée, mais la souris ne possède pas de roulette de défilement.</span><span class="sxs-lookup"><span data-stu-id="6d3d7-103">The `My.Computer.Mouse.WheelScrollLines` property was called, but the mouse has no scroll wheel.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6d3d7-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6d3d7-104">To correct this error</span></span>  
  
-   <span data-ttu-id="6d3d7-105">Vérifiez la propriété `My.Computer.Mouse.WheelExists` pour déterminer si la souris a une roulette de défilement avant d’appeler la propriété `My.Computer.Mouse.WheelScrollLines` .</span><span class="sxs-lookup"><span data-stu-id="6d3d7-105">Check the `My.Computer.Mouse.WheelExists` property to see if the mouse has a scroll wheel before calling the `My.Computer.Mouse.WheelScrollLines` property.</span></span>  
  
     <span data-ttu-id="6d3d7-106">- ou -</span><span class="sxs-lookup"><span data-stu-id="6d3d7-106">-or-</span></span>  
  
-   <span data-ttu-id="6d3d7-107">Installez une souris dotée d’une roulette de défilement sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="6d3d7-107">Install a mouse with a scroll wheel on the computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d3d7-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d3d7-108">See Also</span></span>  
 [<span data-ttu-id="6d3d7-109">My.Computer.Mouse.WheelScrollLines</span><span class="sxs-lookup"><span data-stu-id="6d3d7-109">My.Computer.Mouse.WheelScrollLines</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelScrollLines)  
 [<span data-ttu-id="6d3d7-110">My.Computer.Mouse.WheelExists</span><span class="sxs-lookup"><span data-stu-id="6d3d7-110">My.Computer.Mouse.WheelExists</span></span>](xref:Microsoft.VisualBasic.Devices.Mouse.WheelExists)  
 [<span data-ttu-id="6d3d7-111">Exceptions et gestion des erreurs dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6d3d7-111">Exception and Error Handling in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/3e351e73-cf23-40ab-8b60-05794160529e)
