---
title: Reprendre sans gestion d'erreur
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID20
ms.assetid: f9631804-fd36-4443-b36c-30db827e6176
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f86361b1e5310359288a97c5f41f017a344c30b4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="resume-without-error"></a><span data-ttu-id="5bd4c-102">Reprendre sans gestion d'erreur</span><span class="sxs-lookup"><span data-stu-id="5bd4c-102">Resume without error</span></span>
<span data-ttu-id="5bd4c-103">A `Resume` instruction apparaît en dehors du code de gestion des erreurs ou le code est passé dans un gestionnaire d’erreurs, même si aucune erreur s’est produite.</span><span class="sxs-lookup"><span data-stu-id="5bd4c-103">A `Resume` statement appeared outside error-handling code, or the code jumped into an error handler even though there was no error.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5bd4c-104">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5bd4c-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="5bd4c-105">Déplacer la `Resume` instruction dans un gestionnaire d’erreurs ou de le supprimer.</span><span class="sxs-lookup"><span data-stu-id="5bd4c-105">Move the `Resume` statement into an error handler, or delete it.</span></span>  
  
2.  <span data-ttu-id="5bd4c-106">Passages à des étiquettes ne peuvent pas se produire entre procédures, recherchez dans la procédure pour l’étiquette qui identifie le Gestionnaire d’erreurs.</span><span class="sxs-lookup"><span data-stu-id="5bd4c-106">Jumps to labels cannot occur across procedures, so search the procedure for the label that identifies the error handler.</span></span> <span data-ttu-id="5bd4c-107">Si vous trouvez une étiquette dupliquée spécifiée comme cible d’un `GoTo` instruction qui n’est pas un `On Error GoTo` instruction, modifiez l’étiquette de ligne pour s’accorder avec sa cible prévue.</span><span class="sxs-lookup"><span data-stu-id="5bd4c-107">If you find a duplicate label specified as the target of a `GoTo` statement that isn't an `On Error GoTo` statement, change the line label to agree with its intended target.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd4c-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5bd4c-108">See Also</span></span>  
 [<span data-ttu-id="5bd4c-109">Resume (instruction)</span><span class="sxs-lookup"><span data-stu-id="5bd4c-109">Resume Statement</span></span>](../../../visual-basic/language-reference/statements/resume-statement.md)  
 [<span data-ttu-id="5bd4c-110">On Error (instruction)</span><span class="sxs-lookup"><span data-stu-id="5bd4c-110">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
