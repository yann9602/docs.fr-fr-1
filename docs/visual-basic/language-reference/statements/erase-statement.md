---
title: Erase, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 45a2b439cf5ad04d59cea59bb21d345d0057b322
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="ed47e-102">Erase, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ed47e-102">Erase Statement (Visual Basic)</span></span>
<span data-ttu-id="ed47e-103">Permet de libérer des variables tableau et de libérer la mémoire utilisée pour leurs éléments.</span><span class="sxs-lookup"><span data-stu-id="ed47e-103">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed47e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ed47e-104">Syntax</span></span>  
  
```  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="ed47e-105">Composants</span><span class="sxs-lookup"><span data-stu-id="ed47e-105">Parts</span></span>  
 `arraylist`  
 <span data-ttu-id="ed47e-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ed47e-106">Required.</span></span> <span data-ttu-id="ed47e-107">Liste des variables tableau à effacer.</span><span class="sxs-lookup"><span data-stu-id="ed47e-107">List of array variables to be erased.</span></span> <span data-ttu-id="ed47e-108">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="ed47e-108">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed47e-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="ed47e-109">Remarks</span></span>  
 <span data-ttu-id="ed47e-110">La `Erase` instruction peut apparaître uniquement au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="ed47e-110">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="ed47e-111">Cela signifie que vous pouvez libérer des tableaux à l’intérieur d’une procédure mais pas au niveau de la classe ou le module.</span><span class="sxs-lookup"><span data-stu-id="ed47e-111">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="ed47e-112">Le `Erase` instruction équivaut à assigner `Nothing` à chaque variable tableau.</span><span class="sxs-lookup"><span data-stu-id="ed47e-112">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ed47e-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="ed47e-113">Example</span></span>  
 <span data-ttu-id="ed47e-114">L’exemple suivant utilise la `Erase` instruction pour effacer deux tableaux et libérer leur mémoire (1 000 et 100 éléments de stockage, respectivement).</span><span class="sxs-lookup"><span data-stu-id="ed47e-114">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="ed47e-115">La `ReDim` instruction assigne ensuite une nouvelle instance de tableau au tableau à trois dimensions.</span><span class="sxs-lookup"><span data-stu-id="ed47e-115">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/erase-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ed47e-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed47e-116">See Also</span></span>  
 [<span data-ttu-id="ed47e-117">Nothing</span><span class="sxs-lookup"><span data-stu-id="ed47e-117">Nothing</span></span>](../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="ed47e-118">ReDim (instruction)</span><span class="sxs-lookup"><span data-stu-id="ed47e-118">ReDim Statement</span></span>](../../../visual-basic/language-reference/statements/redim-statement.md)
