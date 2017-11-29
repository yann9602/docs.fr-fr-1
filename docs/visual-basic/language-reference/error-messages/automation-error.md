---
title: Erreur Automation
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 790b171b8d4022bd6d8b038c4221f24805ae42f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="automation-error"></a><span data-ttu-id="cdd16-102">Erreur Automation</span><span class="sxs-lookup"><span data-stu-id="cdd16-102">Automation error</span></span>
<span data-ttu-id="cdd16-103">Une erreur s'est produite pendant l'exécution d'une méthode ou l'obtention / la définition d'une propriété de variable objet.</span><span class="sxs-lookup"><span data-stu-id="cdd16-103">An error occurred while executing a method or getting or setting a property of an object variable.</span></span> <span data-ttu-id="cdd16-104">L'application qui a créé l'objet a signalé l'erreur.</span><span class="sxs-lookup"><span data-stu-id="cdd16-104">The error was reported by the application that created the object.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cdd16-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="cdd16-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="cdd16-106">Vérifiez les propriétés de l'objet `Err` pour déterminer la source et la nature de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="cdd16-106">Check the properties of the `Err` object to determine the source and nature of the error.</span></span>  
  
2.  <span data-ttu-id="cdd16-107">Utilisez la `On Error Resume Next` instruction immédiatement avant l’instruction d’accès et recherchez les erreurs immédiatement après l’instruction d’accès.</span><span class="sxs-lookup"><span data-stu-id="cdd16-107">Use the `On Error Resume Next` statement immediately before the accessing statement, and then check for errors immediately after the accessing statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdd16-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cdd16-108">See Also</span></span>  
 [<span data-ttu-id="cdd16-109">Types d’erreurs</span><span class="sxs-lookup"><span data-stu-id="cdd16-109">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="cdd16-110">Nous contacter</span><span class="sxs-lookup"><span data-stu-id="cdd16-110">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
