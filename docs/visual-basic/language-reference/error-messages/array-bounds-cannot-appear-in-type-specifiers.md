---
title: "Les tailles de tableau ne peuvent pas figurer dans les spécificateurs de type"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30638
- bc30638
helpviewer_keywords: BC30638
ms.assetid: 93b654f4-70fa-4a48-baed-ffae42075550
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770f86ca960110965b6917a22d284678ff8b6f8c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="array-bounds-cannot-appear-in-type-specifiers"></a><span data-ttu-id="309bc-102">Les tailles de tableau ne peuvent pas figurer dans les spécificateurs de type</span><span class="sxs-lookup"><span data-stu-id="309bc-102">Array bounds cannot appear in type specifiers</span></span>
<span data-ttu-id="309bc-103">Les tailles de tableau ne peuvent pas être déclarés en tant que partie d’un spécificateur de type de données.</span><span class="sxs-lookup"><span data-stu-id="309bc-103">Array sizes cannot be declared as part of a data type specifier.</span></span>  
  
 <span data-ttu-id="309bc-104">**ID d’erreur :** BC30638</span><span class="sxs-lookup"><span data-stu-id="309bc-104">**Error ID:** BC30638</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="309bc-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="309bc-105">To correct this error</span></span>  
  
-   <span data-ttu-id="309bc-106">Spécifiez la taille du tableau qui suit immédiatement le nom de variable au lieu de passer la taille du tableau après le type, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="309bc-106">Specify the size of the array immediately following the variable name instead of placing the array size after the type, as shown in the following example.</span></span>  
  
    ```  
    Dim Array(8) As Integer   
    ```  
  
-   <span data-ttu-id="309bc-107">Définir un tableau et initialisez-le avec le nombre voulu d’éléments, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="309bc-107">Define an array and initialize it with the desired number of elements, as shown in the following example.</span></span>  
  
    ```  
    Dim Array2() As Integer = New Integer(8) {}  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="309bc-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="309bc-108">See Also</span></span>  
 [<span data-ttu-id="309bc-109">Tableaux</span><span class="sxs-lookup"><span data-stu-id="309bc-109">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)
