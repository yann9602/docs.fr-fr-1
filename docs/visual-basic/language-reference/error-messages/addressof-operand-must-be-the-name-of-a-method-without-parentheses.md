---
title: "&#39; AddressOf &#39; opérande doit être le nom d’une méthode (sans parenthèses)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords: BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 02c996f1c94250526982e35395288b07db619db7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a><span data-ttu-id="e7347-102">&#39; AddressOf &#39; opérande doit être le nom d’une méthode (sans parenthèses)</span><span class="sxs-lookup"><span data-stu-id="e7347-102">&#39;AddressOf&#39; operand must be the name of a method (without parentheses)</span></span>
<span data-ttu-id="e7347-103">L’opérateur `AddressOf` crée une instance de délégué de procédure qui fait référence à une procédure spécifique.</span><span class="sxs-lookup"><span data-stu-id="e7347-103">The `AddressOf` operator creates a procedure delegate instance that references a specific procedure.</span></span> <span data-ttu-id="e7347-104">La syntaxe est la suivante.</span><span class="sxs-lookup"><span data-stu-id="e7347-104">The syntax is as follows.</span></span>  
  
 <span data-ttu-id="e7347-105">`AddressOf` `procedurename`</span><span class="sxs-lookup"><span data-stu-id="e7347-105">`AddressOf` `procedurename`</span></span>  
  
 <span data-ttu-id="e7347-106">Vous avez inséré des parenthèses autour de l’argument qui suit `AddressOf`, où aucune n’est nécessaire.</span><span class="sxs-lookup"><span data-stu-id="e7347-106">You inserted parentheses around the argument following `AddressOf`, where none are needed.</span></span>  
  
 <span data-ttu-id="e7347-107">**ID d’erreur :** BC30577</span><span class="sxs-lookup"><span data-stu-id="e7347-107">**Error ID:** BC30577</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e7347-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="e7347-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="e7347-109">Supprimez les parenthèses autour de l’argument qui suit `AddressOf`.</span><span class="sxs-lookup"><span data-stu-id="e7347-109">Remove the parentheses around the argument following `AddressOf`.</span></span>  
  
2.  <span data-ttu-id="e7347-110">Assurez-vous que l’argument est un nom de méthode.</span><span class="sxs-lookup"><span data-stu-id="e7347-110">Make sure the argument is a method name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7347-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e7347-111">See Also</span></span>  
 [<span data-ttu-id="e7347-112">AddressOf (opérateur)</span><span class="sxs-lookup"><span data-stu-id="e7347-112">AddressOf Operator</span></span>](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [<span data-ttu-id="e7347-113">Délégués</span><span class="sxs-lookup"><span data-stu-id="e7347-113">Delegates</span></span>](../../../visual-basic/programming-guide/language-features/delegates/index.md)
