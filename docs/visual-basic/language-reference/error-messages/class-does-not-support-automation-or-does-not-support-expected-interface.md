---
title: "Classe ne prend pas en charge l’automatisation ou ne prend pas en charge l’interface attendue | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID430
dev_langs:
- VB
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
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
ms.openlocfilehash: 8368ac123ce24dae41363e74c8b76773f64473b1
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="c9c12-102">La classe ne prend pas en charge Automation ou l'interface attendue</span><span class="sxs-lookup"><span data-stu-id="c9c12-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="c9c12-103">La classe que vous avez spécifiée dans l'appel de fonction `GetObject` ou `CreateObject` n'a exposé aucune interface programmable, ou vous avez modifié un projet .dll en .exe, ou vice versa.</span><span class="sxs-lookup"><span data-stu-id="c9c12-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c9c12-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c9c12-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="c9c12-105">Vérifiez la documentation de l'application qui a créé l'objet pour connaître les limitations relatives à l'utilisation de l'automatisation avec cette classe d'objet.</span><span class="sxs-lookup"><span data-stu-id="c9c12-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2.  <span data-ttu-id="c9c12-106">Si vous avez modifié un projet .dll en .exe ou vice versa, vous devez annuler manuellement l'inscription de l'ancien projet .dll ou .exe.</span><span class="sxs-lookup"><span data-stu-id="c9c12-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9c12-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c9c12-107">See Also</span></span>  
 <span data-ttu-id="c9c12-108">[Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md) </span><span class="sxs-lookup"><span data-stu-id="c9c12-108">[Error Types](../../../visual-basic/programming-guide/language-features/error-types.md) </span></span>  
<span data-ttu-id="c9c12-109"> [Nous contacter](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span><span class="sxs-lookup"><span data-stu-id="c9c12-109"> [Talk to Us](https://docs.microsoft.com/visualstudio/ide/talk-to-us)</span></span>
