---
title: "Différences entre les arguments modifiables et non modifiables (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a><span data-ttu-id="ea67f-102">Différences entre les arguments modifiables et non modifiables (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea67f-102">Differences Between Modifiable and Nonmodifiable Arguments (Visual Basic)</span></span>
<span data-ttu-id="ea67f-103">Lorsque vous appelez une procédure, vous passez généralement un ou plusieurs arguments à celui-ci.</span><span class="sxs-lookup"><span data-stu-id="ea67f-103">When you call a procedure, you typically pass one or more arguments to it.</span></span> <span data-ttu-id="ea67f-104">Chaque argument correspond à un élément de programmation sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="ea67f-104">Each argument corresponds to an underlying programming element.</span></span> <span data-ttu-id="ea67f-105">Les éléments sous-jacents et les arguments peuvent être modifiables ou non.</span><span class="sxs-lookup"><span data-stu-id="ea67f-105">Both the underlying elements and the arguments themselves can be either modifiable or nonmodifiable.</span></span>  
  
## <a name="modifiable-and-nonmodifiable-elements"></a><span data-ttu-id="ea67f-106">Éléments non modifiables et non modifiables</span><span class="sxs-lookup"><span data-stu-id="ea67f-106">Modifiable and Nonmodifiable Elements</span></span>  
 <span data-ttu-id="ea67f-107">Un élément de programmation peut être un *élément modifiable*, qui peut avoir la valeur est modifiable ou un *élément non modifiable*, qui a une valeur fixe, une fois qu’elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="ea67f-107">A programming element can be either a *modifiable element*, which can have its value changed, or a *nonmodifiable element*, which has a fixed value once it has been created.</span></span>  
  
 <span data-ttu-id="ea67f-108">Le tableau suivant répertorie les éléments de programmation modifiables et non modifiables.</span><span class="sxs-lookup"><span data-stu-id="ea67f-108">The following table lists modifiable and nonmodifiable programming elements.</span></span>  
  
|<span data-ttu-id="ea67f-109">Éléments modifiables</span><span class="sxs-lookup"><span data-stu-id="ea67f-109">Modifiable elements</span></span>|<span data-ttu-id="ea67f-110">Éléments non modifiables</span><span class="sxs-lookup"><span data-stu-id="ea67f-110">Nonmodifiable elements</span></span>|  
|-------------------------|----------------------------|  
|<span data-ttu-id="ea67f-111">Les variables locales (déclarées à l’intérieur des procédures), y compris les variables d’objet, à l’exception en lecture seule</span><span class="sxs-lookup"><span data-stu-id="ea67f-111">Local variables (declared inside procedures), including object variables, except for read-only</span></span>|<span data-ttu-id="ea67f-112">Propriétés, champs et variables en lecture seule</span><span class="sxs-lookup"><span data-stu-id="ea67f-112">Read-only variables, fields, and properties</span></span>|  
|<span data-ttu-id="ea67f-113">Champs (variables membres de modules, les classes et structures), à l’exception en lecture seule</span><span class="sxs-lookup"><span data-stu-id="ea67f-113">Fields (member variables of modules, classes, and structures), except for read-only</span></span>|<span data-ttu-id="ea67f-114">Littéraux et des constantes</span><span class="sxs-lookup"><span data-stu-id="ea67f-114">Constants and literals</span></span>|  
|<span data-ttu-id="ea67f-115">Propriétés, à l’exception en lecture seule</span><span class="sxs-lookup"><span data-stu-id="ea67f-115">Properties, except for read-only</span></span>|<span data-ttu-id="ea67f-116">Membres de l’énumération</span><span class="sxs-lookup"><span data-stu-id="ea67f-116">Enumeration members</span></span>|  
|<span data-ttu-id="ea67f-117">Éléments de tableau</span><span class="sxs-lookup"><span data-stu-id="ea67f-117">Array elements</span></span>|<span data-ttu-id="ea67f-118">Expressions (même si leurs éléments sont modifiables)</span><span class="sxs-lookup"><span data-stu-id="ea67f-118">Expressions (even if their elements are modifiable)</span></span>|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a><span data-ttu-id="ea67f-119">Arguments modifiables et non modifiables</span><span class="sxs-lookup"><span data-stu-id="ea67f-119">Modifiable and Nonmodifiable Arguments</span></span>  
 <span data-ttu-id="ea67f-120">A *argument modifiable* est doté d’un élément sous-jacent modifiable.</span><span class="sxs-lookup"><span data-stu-id="ea67f-120">A *modifiable argument* is one with a modifiable underlying element.</span></span> <span data-ttu-id="ea67f-121">Le code appelant peut stocker une nouvelle valeur à tout moment, et si vous passez l’argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), le code dans la procédure peut également modifier l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="ea67f-121">The calling code can store a new value at any time, and if you pass the argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), the code in the procedure can also modify the underlying element in the calling code.</span></span>  
  
 <span data-ttu-id="ea67f-122">A *argument non modifiable* a un élément non modifiable sous-jacent ou est passé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="ea67f-122">A *nonmodifiable argument* either has a nonmodifiable underlying element or is passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span> <span data-ttu-id="ea67f-123">La procédure ne peut pas modifier l’élément sous-jacent dans le code appelant, même si elle est un élément modifiable.</span><span class="sxs-lookup"><span data-stu-id="ea67f-123">The procedure cannot modify the underlying element in the calling code, even if it is a modifiable element.</span></span> <span data-ttu-id="ea67f-124">S’il est un élément non modifiable, le code appelant ne peut pas modifier.</span><span class="sxs-lookup"><span data-stu-id="ea67f-124">If it is a nonmodifiable element, the calling code itself cannot modify it.</span></span>  
  
 <span data-ttu-id="ea67f-125">La procédure appelée peut modifier sa copie locale d’un argument non modifiable, mais cette modification n’affecte pas l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="ea67f-125">The called procedure might modify its local copy of a nonmodifiable argument, but that modification does not affect the underlying element in the calling code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea67f-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ea67f-126">See Also</span></span>  
 [<span data-ttu-id="ea67f-127">Procédures</span><span class="sxs-lookup"><span data-stu-id="ea67f-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="ea67f-128">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="ea67f-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="ea67f-129">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="ea67f-129">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="ea67f-130">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="ea67f-130">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="ea67f-131">Différences entre le passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="ea67f-131">Differences Between Passing an Argument By Value and By Reference</span></span>](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [<span data-ttu-id="ea67f-132">Guide pratique : modifier la valeur d’un argument de la procédure</span><span class="sxs-lookup"><span data-stu-id="ea67f-132">How to: Change the Value of a Procedure Argument</span></span>](./how-to-change-the-value-of-a-procedure-argument.md)  
 [<span data-ttu-id="ea67f-133">Guide pratique : protéger un argument de procédure contre les modifications de valeur</span><span class="sxs-lookup"><span data-stu-id="ea67f-133">How to: Protect a Procedure Argument Against Value Changes</span></span>](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [<span data-ttu-id="ea67f-134">Guide pratique : forcer le passage d’un argument par valeur</span><span class="sxs-lookup"><span data-stu-id="ea67f-134">How to: Force an Argument to Be Passed by Value</span></span>](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [<span data-ttu-id="ea67f-135">Passage des arguments par position et par nom</span><span class="sxs-lookup"><span data-stu-id="ea67f-135">Passing Arguments by Position and by Name</span></span>](./passing-arguments-by-position-and-by-name.md)  
 [<span data-ttu-id="ea67f-136">Types valeur et types référence</span><span class="sxs-lookup"><span data-stu-id="ea67f-136">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
