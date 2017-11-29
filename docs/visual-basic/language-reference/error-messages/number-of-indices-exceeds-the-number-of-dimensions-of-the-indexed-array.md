---
title: "Le nombre d'indices est supérieur au nombre de dimensions du tableau indexé"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30106
- vbc30106
helpviewer_keywords: BC30106
ms.assetid: 2c5363e1-62c2-4f5a-b675-c7337aeb363d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8fdf031734d441daca2073925f6d45d6ba9f1f52
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="number-of-indices-exceeds-the-number-of-dimensions-of-the-indexed-array"></a><span data-ttu-id="62490-102">Le nombre d'indices est supérieur au nombre de dimensions du tableau indexé</span><span class="sxs-lookup"><span data-stu-id="62490-102">Number of indices exceeds the number of dimensions of the indexed array</span></span>
<span data-ttu-id="62490-103">Le nombre d’index utilisés pour accéder à un élément de tableau doit être rigoureusement identique au rang du tableau, c’est-à-dire au nombre de dimensions déclarées pour celui-ci.</span><span class="sxs-lookup"><span data-stu-id="62490-103">The number of indices used to access an array element must be exactly the same as the rank of the array, that is, the number of dimensions declared for it.</span></span>  
  
 <span data-ttu-id="62490-104">**ID d’erreur :** BC30106</span><span class="sxs-lookup"><span data-stu-id="62490-104">**Error ID:** BC30106</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="62490-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="62490-105">To correct this error</span></span>  
  
-   <span data-ttu-id="62490-106">Supprimez des indices de la référence de tableau jusqu'à ce que le nombre total d’indices soit égal au rang du tableau.</span><span class="sxs-lookup"><span data-stu-id="62490-106">Remove subscripts from the array reference until the total number of subscripts equals the rank of the array.</span></span> <span data-ttu-id="62490-107">Exemple :</span><span class="sxs-lookup"><span data-stu-id="62490-107">For example:</span></span>  
  
    ```vb  
    Dim gameBoard(3, 3) As String  
  
    ' Incorrect code. The array has two dimensions.  
    gameBoard(1, 1, 1) = "X"  
    gameBoard(2, 1, 1) = "O"  
  
    ' Correct code.  
    gameBoard(0, 0) = "X"  
    gameBoard(1, 0) = "O"  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="62490-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="62490-108">See Also</span></span>  
 [<span data-ttu-id="62490-109">Tableaux</span><span class="sxs-lookup"><span data-stu-id="62490-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
