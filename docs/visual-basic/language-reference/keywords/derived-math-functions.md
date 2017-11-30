---
title: "Fonctions mathématiques dérivées (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arithmetic operations, derived math functions
- cosecant function
- arcsecant function
- arccotangent function
- functions [Visual Basic], derived math functions
- inverse functions
- math functions, derived
- derived math functions
- cotangent function
- angles
- secant function
- trigonometric functions
- logarithms
- arccosecant function
- hyperbolic functions
- arcsine function
- degrees
- arccosine function
ms.assetid: 63e449d8-9444-44fb-8db1-6d9cf346e2aa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5816fa4c8c384eca116fa1512950a3588c6e3392
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="derived-math-functions-visual-basic"></a><span data-ttu-id="33589-102">Fonctions mathématiques dérivées (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33589-102">Derived Math Functions (Visual Basic)</span></span>
<span data-ttu-id="33589-103">Le tableau suivant présente les fonctions mathématiques non intrinsèques qui peuvent être dérivées des fonctions mathématiques intrinsèques de le <xref:System.Math?displayProperty=nameWithType> objet.</span><span class="sxs-lookup"><span data-stu-id="33589-103">The following table shows non-intrinsic math functions that can be derived from the intrinsic math functions of the <xref:System.Math?displayProperty=nameWithType> object.</span></span> <span data-ttu-id="33589-104">Vous pouvez accéder à des fonctions mathématiques intrinsèques en ajoutant `Imports System.Math` à votre projet ou un fichier.</span><span class="sxs-lookup"><span data-stu-id="33589-104">You can access the intrinsic math functions by adding `Imports System.Math` to your file or project.</span></span>  
  
|<span data-ttu-id="33589-105">Fonction</span><span class="sxs-lookup"><span data-stu-id="33589-105">Function</span></span>|<span data-ttu-id="33589-106">Équivalents</span><span class="sxs-lookup"><span data-stu-id="33589-106">Derived equivalents</span></span>|  
|--------------|-------------------------|  
|<span data-ttu-id="33589-107">Sécante (Sec(x))</span><span class="sxs-lookup"><span data-stu-id="33589-107">Secant (Sec(x))</span></span>|<span data-ttu-id="33589-108">1 / COS (x)</span><span class="sxs-lookup"><span data-stu-id="33589-108">1 / Cos(x)</span></span>|  
|<span data-ttu-id="33589-109">Cosécante (Csc(x))</span><span class="sxs-lookup"><span data-stu-id="33589-109">Cosecant (Csc(x))</span></span>|<span data-ttu-id="33589-110">1 / sin (x)</span><span class="sxs-lookup"><span data-stu-id="33589-110">1 / Sin(x)</span></span>|  
|<span data-ttu-id="33589-111">Cotangente (Ctan(x))</span><span class="sxs-lookup"><span data-stu-id="33589-111">Cotangent (Ctan(x))</span></span>|<span data-ttu-id="33589-112">1 / tan (x)</span><span class="sxs-lookup"><span data-stu-id="33589-112">1 / Tan(x)</span></span>|  
|<span data-ttu-id="33589-113">Sinus inverse (Asin(x))</span><span class="sxs-lookup"><span data-stu-id="33589-113">Inverse sine (Asin(x))</span></span>|<span data-ttu-id="33589-114">ATAN (x / Sqrt (-x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="33589-114">Atan(x / Sqrt(-x * x + 1))</span></span>|  
|<span data-ttu-id="33589-115">Cosinus inverse (Acos(x))</span><span class="sxs-lookup"><span data-stu-id="33589-115">Inverse cosine (Acos(x))</span></span>|<span data-ttu-id="33589-116">ATAN (-x / Sqrt (-x * x + 1)) + 2 \* Atan(1)</span><span class="sxs-lookup"><span data-stu-id="33589-116">Atan(-x / Sqrt(-x * x + 1)) + 2 \* Atan(1)</span></span>|  
|<span data-ttu-id="33589-117">Sécante (Asec(x))</span><span class="sxs-lookup"><span data-stu-id="33589-117">Inverse secant (Asec(x))</span></span>|<span data-ttu-id="33589-118">2 * Atan(1) – Atan(Sign(x) / Sqrt (x \* x-1))</span><span class="sxs-lookup"><span data-stu-id="33589-118">2 * Atan(1) – Atan(Sign(x) / Sqrt(x \* x – 1))</span></span>|  
|<span data-ttu-id="33589-119">Cosécante inverse (Acsc(x))</span><span class="sxs-lookup"><span data-stu-id="33589-119">Inverse cosecant (Acsc(x))</span></span>|<span data-ttu-id="33589-120">ATAN(Sign(x) / Sqrt (x * x-1))</span><span class="sxs-lookup"><span data-stu-id="33589-120">Atan(Sign(x) / Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="33589-121">Cotangente inverse (Acot(x))</span><span class="sxs-lookup"><span data-stu-id="33589-121">Inverse cotangent (Acot(x))</span></span>|<span data-ttu-id="33589-122">2 * Atan(1) - ATAN (x)</span><span class="sxs-lookup"><span data-stu-id="33589-122">2 * Atan(1) - Atan(x)</span></span>|  
|<span data-ttu-id="33589-123">Sinus hyperbolique (Sinh(x))</span><span class="sxs-lookup"><span data-stu-id="33589-123">Hyperbolic sine (Sinh(x))</span></span>|<span data-ttu-id="33589-124">(EXP (x) – Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="33589-124">(Exp(x) – Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="33589-125">Cosinus hyperbolique (Cosh(x))</span><span class="sxs-lookup"><span data-stu-id="33589-125">Hyperbolic cosine (Cosh(x))</span></span>|<span data-ttu-id="33589-126">(EXP (x) + Exp(-x)) / 2</span><span class="sxs-lookup"><span data-stu-id="33589-126">(Exp(x) + Exp(-x)) / 2</span></span>|  
|<span data-ttu-id="33589-127">Tangente hyperbolique (TANH</span><span class="sxs-lookup"><span data-stu-id="33589-127">Hyperbolic tangent (Tanh(x))</span></span>|<span data-ttu-id="33589-128">(EXP (x) – Exp(-x)) / (EXP (x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="33589-128">(Exp(x) – Exp(-x)) / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="33589-129">Sécante hyperbolique (Sech(x))</span><span class="sxs-lookup"><span data-stu-id="33589-129">Hyperbolic secant (Sech(x))</span></span>|<span data-ttu-id="33589-130">2 / (EXP (x) + Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="33589-130">2 / (Exp(x) + Exp(-x))</span></span>|  
|<span data-ttu-id="33589-131">Cosécante hyperbolique (Csch(x))</span><span class="sxs-lookup"><span data-stu-id="33589-131">Hyperbolic cosecant (Csch(x))</span></span>|<span data-ttu-id="33589-132">2 / (EXP (x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="33589-132">2 / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="33589-133">Cotangente hyperbolique (Coth(x))</span><span class="sxs-lookup"><span data-stu-id="33589-133">Hyperbolic cotangent (Coth(x))</span></span>|<span data-ttu-id="33589-134">(EXP (x) + Exp(-x)) / (EXP (x) – Exp(-x))</span><span class="sxs-lookup"><span data-stu-id="33589-134">(Exp(x) + Exp(-x)) / (Exp(x) – Exp(-x))</span></span>|  
|<span data-ttu-id="33589-135">Sinus hyperbolique inverse (Asinh(x))</span><span class="sxs-lookup"><span data-stu-id="33589-135">Inverse hyperbolic sine (Asinh(x))</span></span>|<span data-ttu-id="33589-136">Journal (x + Sqrt (x * x + 1))</span><span class="sxs-lookup"><span data-stu-id="33589-136">Log(x + Sqrt(x * x + 1))</span></span>|  
|<span data-ttu-id="33589-137">Cosinus hyperbolique inverse (Acosh(x))</span><span class="sxs-lookup"><span data-stu-id="33589-137">Inverse hyperbolic cosine (Acosh(x))</span></span>|<span data-ttu-id="33589-138">Journal (x + Sqrt (x * x-1))</span><span class="sxs-lookup"><span data-stu-id="33589-138">Log(x + Sqrt(x * x – 1))</span></span>|  
|<span data-ttu-id="33589-139">Tangente hyperbolique inverse (Atanh(x))</span><span class="sxs-lookup"><span data-stu-id="33589-139">Inverse hyperbolic tangent (Atanh(x))</span></span>|<span data-ttu-id="33589-140">Journal ((1 + x) / (1 – x)) / 2</span><span class="sxs-lookup"><span data-stu-id="33589-140">Log((1 + x) / (1 – x)) / 2</span></span>|  
|<span data-ttu-id="33589-141">Sécante hyperbolique inverse (AsecH(x))</span><span class="sxs-lookup"><span data-stu-id="33589-141">Inverse hyperbolic secant (AsecH(x))</span></span>|<span data-ttu-id="33589-142">Journal ((Sqrt (-x * x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="33589-142">Log((Sqrt(-x * x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="33589-143">Cosécante hyperbolique inverse (Acsch(x))</span><span class="sxs-lookup"><span data-stu-id="33589-143">Inverse hyperbolic cosecant (Acsch(x))</span></span>|<span data-ttu-id="33589-144">Log((Sign(x) * Sqrt (x \* x + 1) + 1) / x)</span><span class="sxs-lookup"><span data-stu-id="33589-144">Log((Sign(x) * Sqrt(x \* x + 1) + 1) / x)</span></span>|  
|<span data-ttu-id="33589-145">Cotangente hyperbolique inverse (Acoth(x))</span><span class="sxs-lookup"><span data-stu-id="33589-145">Inverse hyperbolic cotangent (Acoth(x))</span></span>|<span data-ttu-id="33589-146">Journal ((x + 1) / (n-1)) / 2</span><span class="sxs-lookup"><span data-stu-id="33589-146">Log((x + 1) / (x – 1)) / 2</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33589-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33589-147">See Also</span></span>  
 [<span data-ttu-id="33589-148">Fonctions mathématiques</span><span class="sxs-lookup"><span data-stu-id="33589-148">Math Functions</span></span>](../../../visual-basic/language-reference/functions/math-functions.md)
