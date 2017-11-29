---
title: "&#39; #Region &#39; et &#39; #End Region &#39; les instructions ne sont pas valides dans les expressions lambda multiligne de corps de méthode"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords: BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 614d0c7324bfbf07bc5736c799e8b54937ead081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="39region39-and-39end-region39-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="6e738-102">&#39; #Region &#39; et &#39; #End Region &#39; les instructions ne sont pas valides dans les expressions lambda multiligne corps de méthode</span><span class="sxs-lookup"><span data-stu-id="6e738-102">&#39;#Region&#39; and &#39;#End Region&#39; statements are not valid within method bodies/multiline lambdas</span></span>
<span data-ttu-id="6e738-103">Le `#Region` bloc doit être déclaré au niveau de la classe, module ou d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="6e738-103">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="6e738-104">Une zone réductible peut inclure une ou plusieurs procédures, mais il ne peut pas commencer ou se terminer à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="6e738-104">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>  
  
 <span data-ttu-id="6e738-105">**ID d’erreur :** BC32025</span><span class="sxs-lookup"><span data-stu-id="6e738-105">**Error ID:** BC32025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6e738-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6e738-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="6e738-107">Assurez-vous que la procédure précédente est correctement terminée avec un `End Function` ou `End Sub` instruction.</span><span class="sxs-lookup"><span data-stu-id="6e738-107">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>  
  
2.  <span data-ttu-id="6e738-108">Vérifiez que le `#Region` et `#End Region` sont des directives dans le même bloc de code.</span><span class="sxs-lookup"><span data-stu-id="6e738-108">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e738-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e738-109">See Also</span></span>  
 [<span data-ttu-id="6e738-110">#Region (directive)</span><span class="sxs-lookup"><span data-stu-id="6e738-110">#Region Directive</span></span>](../../../visual-basic/language-reference/directives/region-directive.md)
