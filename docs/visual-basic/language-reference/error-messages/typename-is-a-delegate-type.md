---
title: "«&lt;typename&gt;&quot; est un type délégué | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32008
- vbc32008
dev_langs:
- VB
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 55532e269a7d6756157d324a2db14320df5d3f55
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="39lttypenamegt39-is-a-delegate-type"></a><span data-ttu-id="41541-102">«&lt;typename&gt;' est un type délégué</span><span class="sxs-lookup"><span data-stu-id="41541-102">&#39;&lt;typename&gt;&#39; is a delegate type</span></span>
<span data-ttu-id="41541-103">«\<typename >' est un type délégué.</span><span class="sxs-lookup"><span data-stu-id="41541-103">'\<typename>' is a delegate type.</span></span> <span data-ttu-id="41541-104">Une construction déléguée accepte une seule expression AddressOf en tant que liste d’arguments.</span><span class="sxs-lookup"><span data-stu-id="41541-104">Delegate construction permits only a single AddressOf expression as an argument list.</span></span> <span data-ttu-id="41541-105">Une expression AddressOf peut souvent être utilisée au lieu d’une construction déléguée.</span><span class="sxs-lookup"><span data-stu-id="41541-105">Often an AddressOf expression can be used instead of a delegate construction.</span></span>  
  
 <span data-ttu-id="41541-106">Un `New` clause crée une instance d’une classe déléguée fournit une liste d’arguments non valide au constructeur délégué.</span><span class="sxs-lookup"><span data-stu-id="41541-106">A `New` clause creating an instance of a delegate class supplies an invalid argument list to the delegate constructor.</span></span>  
  
 <span data-ttu-id="41541-107">Vous pouvez fournir une seule `AddressOf` expression lors de la création d’une nouvelle instance de délégué.</span><span class="sxs-lookup"><span data-stu-id="41541-107">You can supply only a single `AddressOf` expression when creating a new delegate instance.</span></span>  
  
 <span data-ttu-id="41541-108">Cette erreur peut se produire si vous ne passez pas d’arguments au constructeur délégué, si vous passez plusieurs arguments, ou si vous passez un argument unique qui n’est pas valide `AddressOf` expression.</span><span class="sxs-lookup"><span data-stu-id="41541-108">This error can result if you do not pass any arguments to the delegate constructor, if you pass more than one argument, or if you pass a single argument that is not a valid `AddressOf` expression.</span></span>  
  
 <span data-ttu-id="41541-109">**ID d’erreur :** BC32008</span><span class="sxs-lookup"><span data-stu-id="41541-109">**Error ID:** BC32008</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="41541-110">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="41541-110">To correct this error</span></span>  
  
-   <span data-ttu-id="41541-111">Utiliser un seul `AddressOf` expression dans la liste d’arguments pour la classe déléguée dans la `New` clause.</span><span class="sxs-lookup"><span data-stu-id="41541-111">Use a single `AddressOf` expression in the argument list for the delegate class in the `New` clause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41541-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="41541-112">See Also</span></span>  
 <span data-ttu-id="41541-113">[New, opérateur](../../../visual-basic/language-reference/operators/new-operator.md) </span><span class="sxs-lookup"><span data-stu-id="41541-113">[New Operator](../../../visual-basic/language-reference/operators/new-operator.md) </span></span>  
<span data-ttu-id="41541-114"> [AddressOf (opérateur)](../../../visual-basic/language-reference/operators/addressof-operator.md) </span><span class="sxs-lookup"><span data-stu-id="41541-114"> [AddressOf Operator](../../../visual-basic/language-reference/operators/addressof-operator.md) </span></span>  
<span data-ttu-id="41541-115"> [Délégués](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="41541-115"> [Delegates](../../../visual-basic/programming-guide/language-features/delegates/index.md) </span></span>  
<span data-ttu-id="41541-116"> [Guide pratique : appeler une méthode déléguée](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span><span class="sxs-lookup"><span data-stu-id="41541-116"> [How to: Invoke a Delegate Method](../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)</span></span>
