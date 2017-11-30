---
title: "Fonction imbriquée n’a pas une signature compatible avec le délégué &#39; &lt;nom_délégué&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords: BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 60cf15343023110561da3e3fcf202bd00394127a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-39ltdelegatenamegt39"></a><span data-ttu-id="66a55-102">Fonction imbriquée n’a pas une signature compatible avec le délégué &#39; &lt;nom_délégué&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="66a55-102">Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;</span></span>
<span data-ttu-id="66a55-103">Une expression lambda a été assignée à un délégué qui a une signature incompatible.</span><span class="sxs-lookup"><span data-stu-id="66a55-103">A lambda expression has been assigned to a delegate that has an incompatible signature.</span></span> <span data-ttu-id="66a55-104">Par exemple, dans le code suivant, le délégué `Del` a deux paramètres entiers.</span><span class="sxs-lookup"><span data-stu-id="66a55-104">For example, in the following code, delegate `Del` has two integer parameters.</span></span>  
  
```vb  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 <span data-ttu-id="66a55-105">L’erreur est déclenchée si une expression lambda avec un argument est déclarée comme type `Del`:</span><span class="sxs-lookup"><span data-stu-id="66a55-105">The error is raised if a lambda expression with one argument is declared as type `Del`:</span></span>  
  
```vb  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 <span data-ttu-id="66a55-106">**ID d’erreur :** BC36532</span><span class="sxs-lookup"><span data-stu-id="66a55-106">**Error ID:** BC36532</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="66a55-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="66a55-107">To correct this error</span></span>  
  
-   <span data-ttu-id="66a55-108">Ajustez la définition de délégué ou l’expression lambda assignée afin que les signatures sont compatibles.</span><span class="sxs-lookup"><span data-stu-id="66a55-108">Adjust either the delegate definition or the assigned lambda expression so that the signatures are compatible.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66a55-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="66a55-109">See Also</span></span>  
 [<span data-ttu-id="66a55-110">Conversion simplifiée des délégués</span><span class="sxs-lookup"><span data-stu-id="66a55-110">Relaxed Delegate Conversion</span></span>](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)  
 [<span data-ttu-id="66a55-111">Expressions lambda</span><span class="sxs-lookup"><span data-stu-id="66a55-111">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
