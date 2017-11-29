---
title: "&#39; Dir &#39; fonction doit d’abord être appelée avec un &#39; Chemin d’accès &#39; argument"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 843918fe9cb0b9dece076b5dc1373c3571588caa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a><span data-ttu-id="123b4-102">&#39; Dir &#39; fonction doit d’abord être appelée avec un &#39; Chemin d’accès &#39; argument</span><span class="sxs-lookup"><span data-stu-id="123b4-102">&#39;Dir&#39; function must first be called with a &#39;PathName&#39; argument</span></span>
<span data-ttu-id="123b4-103">Un appel initial à la `Dir` fonction n’inclut pas le `PathName` argument.</span><span class="sxs-lookup"><span data-stu-id="123b4-103">An initial call to the `Dir` function does not include the `PathName` argument.</span></span> <span data-ttu-id="123b4-104">Le premier appel à `Dir` doit inclure un `PathName`, mais les appels suivants à `Dir` n’avez pas besoin d’inclure des paramètres permettant d’extraire l’élément suivant.</span><span class="sxs-lookup"><span data-stu-id="123b4-104">The first call to `Dir` must include a `PathName`, but subsequent calls to `Dir` do not need to include parameters to retrieve the next item.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="123b4-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="123b4-105">To correct this error</span></span>  
  
1.  <span data-ttu-id="123b4-106">Fournir un `PathName` argument dans l’appel de fonction.</span><span class="sxs-lookup"><span data-stu-id="123b4-106">Supply a `PathName` argument in the function call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="123b4-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="123b4-107">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
