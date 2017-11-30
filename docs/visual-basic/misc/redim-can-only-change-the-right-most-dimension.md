---
title: "&#39; ReDim &#39; peut changer que la dimension la plus à droite"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 989a06f94824dfd051d1a7d2e7749dbb8c8e11a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39redim39-can-only-change-the-right-most-dimension"></a><span data-ttu-id="89991-102">&#39; ReDim &#39; peut changer que la dimension la plus à droite</span><span class="sxs-lookup"><span data-stu-id="89991-102">&#39;ReDim&#39; can only change the right-most dimension</span></span>
<span data-ttu-id="89991-103">Une instruction `ReDim` a tenté d’utiliser le mot clé `Preserve` pour modifier une dimension d’un tableau qui n’est pas la dernière dimension.</span><span class="sxs-lookup"><span data-stu-id="89991-103">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="89991-104">Lors de l’utilisation de `Preserve`, vous pouvez redimensionner uniquement la dernière dimension d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="89991-104">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="89991-105">Pour toutes les autres dimensions, vous devez spécifier la même taille que pour le tableau existant.</span><span class="sxs-lookup"><span data-stu-id="89991-105">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="89991-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="89991-106">To correct this error</span></span>  
  
-   <span data-ttu-id="89991-107">Supprimez le mot clé `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="89991-107">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89991-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="89991-108">See Also</span></span>  
 [<span data-ttu-id="89991-109">Tableaux en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89991-109">Arrays in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="89991-110">Dimensions du tableau dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89991-110">Array dimensions in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/arrays/array-dimensions.md)  
 [<span data-ttu-id="89991-111">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="89991-111">ReDim Statement</span></span>](../../visual-basic/language-reference/statements/redim-statement.md)  
 [<span data-ttu-id="89991-112">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="89991-112">Dim Statement</span></span>](../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="89991-113">Conserver - supprimer</span><span class="sxs-lookup"><span data-stu-id="89991-113">Preserve - delete</span></span>](http://msdn.microsoft.com/en-us/91badeab-b4e0-48b6-92c9-9f0c8f995d81)
