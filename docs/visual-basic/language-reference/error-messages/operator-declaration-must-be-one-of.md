---
title: "Déclaration d’opérateur doit être de type : +,-, *,-, -, ^, &amp;, Like, Mod et, Or, Xor, pas &lt; &lt;, &gt; &gt;, =, &lt; &gt;, &lt;, &lt;=, &gt; , &gt;=, CType, IsTrue ou IsFalse"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords: BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 80c8358dd13105c18e73e94735a51b02d5bd22c5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not-ltlt-gtgt"></a><span data-ttu-id="25b56-102">Déclaration d’opérateur doit être de type : +,-, *,\,/, ^, &amp;, Like, Mod et, Or, Xor, pas &lt; &lt;, &gt; &gt;...</span><span class="sxs-lookup"><span data-stu-id="25b56-102">Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;...</span></span>
<span data-ttu-id="25b56-103">Vous pouvez déclarer uniquement un opérateur qui n’est éligible pour la surcharge.</span><span class="sxs-lookup"><span data-stu-id="25b56-103">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="25b56-104">Le tableau suivant répertorie les opérateurs que vous pouvez déclarer.</span><span class="sxs-lookup"><span data-stu-id="25b56-104">The following table lists the operators you can declare.</span></span>  
  
|<span data-ttu-id="25b56-105">Type</span><span class="sxs-lookup"><span data-stu-id="25b56-105">Type</span></span>|<span data-ttu-id="25b56-106">Opérateurs</span><span class="sxs-lookup"><span data-stu-id="25b56-106">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="25b56-107">Unaire</span><span class="sxs-lookup"><span data-stu-id="25b56-107">Unary</span></span>|<span data-ttu-id="25b56-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="25b56-108">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="25b56-109">Binaire</span><span class="sxs-lookup"><span data-stu-id="25b56-109">Binary</span></span>|<span data-ttu-id="25b56-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="25b56-110">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="25b56-111">Conversion (unaire)</span><span class="sxs-lookup"><span data-stu-id="25b56-111">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="25b56-112">Notez que le `=` opérateur dans la liste binaire est l’opérateur de comparaison, pas l’opérateur d’assignation.</span><span class="sxs-lookup"><span data-stu-id="25b56-112">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="25b56-113">**ID d’erreur :** BC33000</span><span class="sxs-lookup"><span data-stu-id="25b56-113">**Error ID:** BC33000</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="25b56-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="25b56-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="25b56-115">Sélectionnez un opérateur dans le jeu d’opérateurs surchargeables.</span><span class="sxs-lookup"><span data-stu-id="25b56-115">Select an operator from the set of overloadable operators.</span></span>  
  
2.  <span data-ttu-id="25b56-116">Si vous avez besoin des fonctionnalités de surcharge d’un opérateur que vous ne pouvez pas surcharger directement, créez une procédure `Function` qui accepte les paramètres appropriés et retourne la valeur adéquate.</span><span class="sxs-lookup"><span data-stu-id="25b56-116">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b56-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="25b56-117">See Also</span></span>  
 [<span data-ttu-id="25b56-118">Operator (instruction)</span><span class="sxs-lookup"><span data-stu-id="25b56-118">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="25b56-119">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="25b56-119">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)  
 [<span data-ttu-id="25b56-120">Guide pratique : définir un opérateur</span><span class="sxs-lookup"><span data-stu-id="25b56-120">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [<span data-ttu-id="25b56-121">Guide pratique : définir un opérateur de conversion</span><span class="sxs-lookup"><span data-stu-id="25b56-121">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="25b56-122">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="25b56-122">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
