---
title: "Comment : référencer l'instance actuelle d'un objet (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], object
- objects [Visual Basic], referring to current instance
- instances [Visual Basic], referring to current
- current instance
- object variables [Visual Basic]
ms.assetid: 7f9b2c77-03cd-428f-adc2-b18070226e7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33ea612253b00e12f47258189da4ac7d8d98ade5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-the-current-instance-of-an-object-visual-basic"></a><span data-ttu-id="0c5f6-102">Comment : référencer l'instance actuelle d'un objet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c5f6-102">How to: Refer to the Current Instance of an Object (Visual Basic)</span></span>
<span data-ttu-id="0c5f6-103">Le *instance actuelle* d’un objet est l’instance dans laquelle le code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="0c5f6-103">The *current instance* of an object is the instance in which the code is currently executing.</span></span>  
  
 <span data-ttu-id="0c5f6-104">Vous utilisez la `Me` (mot clé) pour faire référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="0c5f6-104">You use the `Me` keyword to refer to the current instance.</span></span>  
  
### <a name="to-refer-to-the-current-instance"></a><span data-ttu-id="0c5f6-105">Pour faire référence à l’instance actuelle</span><span class="sxs-lookup"><span data-stu-id="0c5f6-105">To refer to the current instance</span></span>  
  
-   <span data-ttu-id="0c5f6-106">Utilisez le `Me` mot clé où vous utiliseriez normalement le nom d’une variable objet.</span><span class="sxs-lookup"><span data-stu-id="0c5f6-106">Use the `Me` keyword where you would normally use the name of an object variable.</span></span>  
  
    ```  
    Me.ForeColor = System.Drawing.Color.Crimson  
    Me.Close()  
    ```  
  
     <span data-ttu-id="0c5f6-107">Bien que `Me` se comporte comme un objet variable, vous ne peut pas déclarer ou affectez-lui quoi que ce soit.</span><span class="sxs-lookup"><span data-stu-id="0c5f6-107">Although `Me` behaves like an object variable, you cannot declare it or assign anything to it.</span></span> <span data-ttu-id="0c5f6-108">`Me`fait toujours référence à l’instance actuelle.</span><span class="sxs-lookup"><span data-stu-id="0c5f6-108">`Me` always refers to the current instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c5f6-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0c5f6-109">See Also</span></span>  
 [<span data-ttu-id="0c5f6-110">Variables objets</span><span class="sxs-lookup"><span data-stu-id="0c5f6-110">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="0c5f6-111">Assignation des variables objets</span><span class="sxs-lookup"><span data-stu-id="0c5f6-111">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="0c5f6-112">Me, My, MyBase et MyClass</span><span class="sxs-lookup"><span data-stu-id="0c5f6-112">Me, My, MyBase, and MyClass</span></span>](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
