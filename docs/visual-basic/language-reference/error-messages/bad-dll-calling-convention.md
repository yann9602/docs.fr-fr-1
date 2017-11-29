---
title: "Convention d’appel de DLL incorrecte"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: daa84e82d2fbe1041af56fdd5cc3855efd814ddf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="7720c-102">Convention d’appel de DLL incorrecte</span><span class="sxs-lookup"><span data-stu-id="7720c-102">Bad DLL calling convention</span></span>
<span data-ttu-id="7720c-103">Arguments passés à une bibliothèque de liens dynamiques (DLL) doivent correspondre exactement à ceux attendus par la routine.</span><span class="sxs-lookup"><span data-stu-id="7720c-103">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="7720c-104">Conventions d’appel traitent nombre, type et ordre des arguments.</span><span class="sxs-lookup"><span data-stu-id="7720c-104">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="7720c-105">Votre programme peut appeler une routine dans une DLL qui est passée du type incorrect ou le nombre d’arguments.</span><span class="sxs-lookup"><span data-stu-id="7720c-105">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="7720c-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="7720c-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="7720c-107">Assurez-vous que tous les types d’argument correspondent à ceux spécifiés dans la déclaration de la routine que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="7720c-107">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2.  <span data-ttu-id="7720c-108">Vérifiez que vous passez le même nombre d’arguments indiqué dans la déclaration de la routine que vous appelez.</span><span class="sxs-lookup"><span data-stu-id="7720c-108">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3.  <span data-ttu-id="7720c-109">Si la routine DLL attend des arguments par valeur, vérifiez que `ByVal` est spécifié pour ces arguments dans la déclaration de la routine.</span><span class="sxs-lookup"><span data-stu-id="7720c-109">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7720c-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7720c-110">See Also</span></span>  
 [<span data-ttu-id="7720c-111">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="7720c-111">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="7720c-112">Call (instruction)</span><span class="sxs-lookup"><span data-stu-id="7720c-112">Call Statement</span></span>](../../../visual-basic/language-reference/statements/call-statement.md)  
 [<span data-ttu-id="7720c-113">Declare (instruction)</span><span class="sxs-lookup"><span data-stu-id="7720c-113">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
