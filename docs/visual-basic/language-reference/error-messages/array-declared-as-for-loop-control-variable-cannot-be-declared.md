---
title: "Un tableau déclaré en tant que variable de contrôle de boucle for ne peut pas être déclaré avec une taille initiale"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc32039
- bc32039
helpviewer_keywords: BC32039
ms.assetid: 1d8b6560-c9eb-4b71-a038-24c6f5a5ce46
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef36f14d5323a4592afe59573e249d8cfb218df9
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="array-declared-as-for-loop-control-variable-cannot-be-declared-with-an-initial-size"></a><span data-ttu-id="21961-102">Un tableau déclaré en tant que variable de contrôle de boucle for ne peut pas être déclaré avec une taille initiale</span><span class="sxs-lookup"><span data-stu-id="21961-102">Array declared as for loop control variable cannot be declared with an initial size</span></span>
<span data-ttu-id="21961-103">A `For Each` boucle utilise un tableau comme sa *élément* variable d’itération initialise mais ce tableau.</span><span class="sxs-lookup"><span data-stu-id="21961-103">A `For Each` loop uses an array as its *element* iteration variable but initializes that array.</span></span>  
  
 <span data-ttu-id="21961-104">Les instructions suivantes montrent comment cette erreur peut être générée.</span><span class="sxs-lookup"><span data-stu-id="21961-104">The following statements show how this error can be generated.</span></span>  
  
```  
Dim arrayList As New List(Of Integer())  
For Each listElement() As Integer In arrayList  
For Each listElement(1) As Integer In arrayList  
```  
  
 <span data-ttu-id="21961-105">La première `For Each` instruction est la méthode correcte pour accéder aux éléments de `arrayList`.</span><span class="sxs-lookup"><span data-stu-id="21961-105">The first `For Each` statement is the correct way to access elements of `arrayList`.</span></span> <span data-ttu-id="21961-106">La seconde `For Each` instruction génère cette erreur.</span><span class="sxs-lookup"><span data-stu-id="21961-106">The second `For Each` statement generates this error.</span></span>  
  
 <span data-ttu-id="21961-107">**ID d’erreur :** BC32039</span><span class="sxs-lookup"><span data-stu-id="21961-107">**Error ID:** BC32039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21961-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="21961-108">To correct this error</span></span>  
  
-   <span data-ttu-id="21961-109">Supprimez l’initialisation de la déclaration de la *élément* variable d’itération.</span><span class="sxs-lookup"><span data-stu-id="21961-109">Remove the initialization from the declaration of the *element* iteration variable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21961-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="21961-110">See Also</span></span>  
 [<span data-ttu-id="21961-111">For...Next (instruction)</span><span class="sxs-lookup"><span data-stu-id="21961-111">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="21961-112">Tableaux</span><span class="sxs-lookup"><span data-stu-id="21961-112">Arrays</span></span>](../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [<span data-ttu-id="21961-113">Collections</span><span class="sxs-lookup"><span data-stu-id="21961-113">Collections</span></span>](../../../standard/collections/index.md)
