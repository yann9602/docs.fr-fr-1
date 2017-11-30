---
title: "Les tableaux déclarés en tant que membres de structures ne peuvent pas être déclarés avec une taille initiale"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31043
- bc31043
helpviewer_keywords: BC31043
ms.assetid: 5bd90c71-1b78-444b-91e1-4789451ef085
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 983154a144a79991c86db5056ad0e0e563a3ba73
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-declared-as-structure-members-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="8a981-102">Les tableaux déclarés en tant que membres de structures ne peuvent pas être déclarés avec une taille initiale</span><span class="sxs-lookup"><span data-stu-id="8a981-102">Arrays declared as structure members cannot be declared with an initial size</span></span>
<span data-ttu-id="8a981-103">Un tableau dans une structure est déclaré avec une taille initiale.</span><span class="sxs-lookup"><span data-stu-id="8a981-103">An array in a structure is declared with an initial size.</span></span> <span data-ttu-id="8a981-104">Vous ne pouvez pas initialiser n’importe quel élément de structure, et la déclaration d’une taille de tableau est une forme de l’initialisation.</span><span class="sxs-lookup"><span data-stu-id="8a981-104">You cannot initialize any structure element, and declaring an array size is one form of initialization.</span></span>  
  
 <span data-ttu-id="8a981-105">**ID d’erreur :** BC31043</span><span class="sxs-lookup"><span data-stu-id="8a981-105">**Error ID:** BC31043</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8a981-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="8a981-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="8a981-107">Définissez le tableau dans votre structure en tant que dynamique (sans taille initiale).</span><span class="sxs-lookup"><span data-stu-id="8a981-107">Define the array in your structure as dynamic (no initial size).</span></span>  
  
2.  <span data-ttu-id="8a981-108">Si vous avez besoin d’une certaine taille de tableau, vous pouvez redimensionner un tableau dynamique avec un [instruction ReDim](../../../visual-basic/language-reference/statements/redim-statement.md) lorsque votre code est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="8a981-108">If you require a certain size of array, you can redimension a dynamic array with a [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) when your code is running.</span></span> <span data-ttu-id="8a981-109">L'exemple suivant illustre ce comportement.</span><span class="sxs-lookup"><span data-stu-id="8a981-109">The following example illustrates this.</span></span>  
  
    ```  
    Structure demoStruct  
        Public demoArray() As Integer  
    End Structure  
    Sub useStruct()  
        Dim struct As demoStruct  
        ReDim struct.demoArray(9)  
        Struct.demoArray(2) = 777  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="8a981-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8a981-110">See Also</span></span>  
 [<span data-ttu-id="8a981-111">Tableaux</span><span class="sxs-lookup"><span data-stu-id="8a981-111">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="8a981-112">Guide pratique : déclarer une structure</span><span class="sxs-lookup"><span data-stu-id="8a981-112">How to: Declare a Structure</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
