---
title: "Le nom de la variable de portée peut être déduit uniquement à partir d’un nom qualifié ou d’un nom simple sans arguments"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords: BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c986fcf188482c526c53ddf3019cec5163d0b62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="edb14-102">Le nom de la variable de portée peut être déduit uniquement à partir d’un nom qualifié ou d’un nom simple sans arguments</span><span class="sxs-lookup"><span data-stu-id="edb14-102">Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>
<span data-ttu-id="edb14-103">Un élément de programmation qui prend un ou plusieurs arguments est inclus dans une requête LINQ.</span><span class="sxs-lookup"><span data-stu-id="edb14-103">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="edb14-104">Le compilateur ne peut pas déduire d’une variable de portée à partir de cet élément de programmation.</span><span class="sxs-lookup"><span data-stu-id="edb14-104">The compiler is unable to infer a range variable from that programming element.</span></span>  
  
 <span data-ttu-id="edb14-105">**ID d’erreur :** BC36599</span><span class="sxs-lookup"><span data-stu-id="edb14-105">**Error ID:** BC36599</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="edb14-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="edb14-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="edb14-107">Fournissez un nom de variable explicit pour l’élément de programmation, comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="edb14-107">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a><span data-ttu-id="edb14-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="edb14-108">See Also</span></span>  
 [<span data-ttu-id="edb14-109">Introduction à LINQ en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="edb14-109">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="edb14-110">Select (clause)</span><span class="sxs-lookup"><span data-stu-id="edb14-110">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
