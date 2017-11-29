---
title: La classe ne prend pas en charge Automation ou l'interface attendue
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6528ceabeb7fb7a1cdc0beff2fd362632a0a0c9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="0395c-102">La classe ne prend pas en charge Automation ou l'interface attendue</span><span class="sxs-lookup"><span data-stu-id="0395c-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="0395c-103">La classe que vous avez spécifiée dans l'appel de fonction `GetObject` ou `CreateObject` n'a exposé aucune interface programmable, ou vous avez modifié un projet .dll en .exe, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="0395c-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0395c-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="0395c-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="0395c-105">Vérifiez la documentation de l'application qui a créé l'objet pour connaître les limitations relatives à l'utilisation de l'automatisation avec cette classe d'objet.</span><span class="sxs-lookup"><span data-stu-id="0395c-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2.  <span data-ttu-id="0395c-106">Si vous avez modifié un projet .dll en .exe ou vice versa, vous devez annuler manuellement l'inscription de l'ancien projet .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="0395c-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0395c-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0395c-107">See Also</span></span>  
 [<span data-ttu-id="0395c-108">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="0395c-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="0395c-109">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="0395c-109">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
