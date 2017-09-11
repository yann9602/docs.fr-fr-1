---
title: "Différences entre le passage d’un Argument par valeur et par référence (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- procedures, passing arguments
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
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
ms.openlocfilehash: 706c64cd316791a748e2b68fe406e34084b04d5a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a><span data-ttu-id="c776b-102">Différences entre le passage d’un argument par valeur et par référence (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c776b-102">Differences Between Passing an Argument By Value and By Reference (Visual Basic)</span></span>
<span data-ttu-id="c776b-103">Lorsque vous passez un ou plusieurs arguments à une procédure, chaque argument correspond à un élément de programmation sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="c776b-103">When you pass one or more arguments to a procedure, each argument corresponds to an underlying programming element in the calling code.</span></span> <span data-ttu-id="c776b-104">Vous pouvez passer la valeur de cet élément sous-jacent, ou une référence à celle-ci.</span><span class="sxs-lookup"><span data-stu-id="c776b-104">You can pass either the value of this underlying element, or a reference to it.</span></span> <span data-ttu-id="c776b-105">Il s’agit du *mécanisme de transmission*.</span><span class="sxs-lookup"><span data-stu-id="c776b-105">This is known as the *passing mechanism*.</span></span>  
  
## <a name="passing-by-value"></a><span data-ttu-id="c776b-106">passer par valeur</span><span class="sxs-lookup"><span data-stu-id="c776b-106">Passing by Value</span></span>  
 <span data-ttu-id="c776b-107">Vous passez un argument *par valeur* en spécifiant le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mot clé pour le paramètre correspondant dans la définition de procédure.</span><span class="sxs-lookup"><span data-stu-id="c776b-107">You pass an argument *by value* by specifying the [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="c776b-108">Lorsque vous utilisez ce mécanisme de passage, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie la valeur de l’élément de programmation sous-jacent dans une variable locale de la procédure.</span><span class="sxs-lookup"><span data-stu-id="c776b-108">When you use this passing mechanism, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copies the value of the underlying programming element into a local variable in the procedure.</span></span> <span data-ttu-id="c776b-109">Le code de procédure n’a pas accès à l’élément sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="c776b-109">The procedure code does not have any access to the underlying element in the calling code.</span></span>  
  
## <a name="passing-by-reference"></a><span data-ttu-id="c776b-110">Le passage par référence</span><span class="sxs-lookup"><span data-stu-id="c776b-110">Passing by Reference</span></span>  
 <span data-ttu-id="c776b-111">Vous passez un argument *par référence* en spécifiant le [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot clé pour le paramètre correspondant dans la définition de procédure.</span><span class="sxs-lookup"><span data-stu-id="c776b-111">You pass an argument *by reference* by specifying the [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) keyword for the corresponding parameter in the procedure definition.</span></span> <span data-ttu-id="c776b-112">Lorsque vous utilisez ce mécanisme de passage, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit à la procédure une référence directe à l’élément de programmation sous-jacent dans le code appelant.</span><span class="sxs-lookup"><span data-stu-id="c776b-112">When you use this passing mechanism, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] gives the procedure a direct reference to the underlying programming element in the calling code.</span></span>  
  
## <a name="passing-mechanism-and-element-type"></a><span data-ttu-id="c776b-113">Mécanisme de passage et le Type d’élément</span><span class="sxs-lookup"><span data-stu-id="c776b-113">Passing Mechanism and Element Type</span></span>  
 <span data-ttu-id="c776b-114">Le choix du mécanisme de transmission n’est pas identique à la classification du type d’élément sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="c776b-114">The choice of passing mechanism is not the same as the classification of the underlying element type.</span></span> <span data-ttu-id="c776b-115">Passage par valeur ou par référence fait référence à ce que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit le code de procédure.</span><span class="sxs-lookup"><span data-stu-id="c776b-115">Passing by value or by reference refers to what [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] supplies to the procedure code.</span></span> <span data-ttu-id="c776b-116">Un type valeur ou un type référence fait référence à la façon dont un élément de programmation est stocké en mémoire.</span><span class="sxs-lookup"><span data-stu-id="c776b-116">A value type or reference type refers to how a programming element is stored in memory.</span></span>  
  
 <span data-ttu-id="c776b-117">Toutefois, le mécanisme de passage et le type d’élément sont reliés entre eux.</span><span class="sxs-lookup"><span data-stu-id="c776b-117">However, the passing mechanism and element type are interrelated.</span></span> <span data-ttu-id="c776b-118">La valeur d’un type référence est un pointeur vers les données ailleurs dans la mémoire.</span><span class="sxs-lookup"><span data-stu-id="c776b-118">The value of a reference type is a pointer to the data elsewhere in memory.</span></span> <span data-ttu-id="c776b-119">Cela signifie que lorsque vous passez un type référence par valeur, le code de procédure a un pointeur vers les données de l’élément sous-jacent, bien qu’il ne peut pas accéder à l’élément sous-jacent lui-même.</span><span class="sxs-lookup"><span data-stu-id="c776b-119">This means that when you pass a reference type by value, the procedure code has a pointer to the underlying element's data, even though it cannot access the underlying element itself.</span></span> <span data-ttu-id="c776b-120">Par exemple, si l’élément est une variable de tableau, le code de procédure n’a pas accès à la variable elle-même, mais il peut accéder aux membres du groupe.</span><span class="sxs-lookup"><span data-stu-id="c776b-120">For example, if the element is an array variable, the procedure code does not have access to the variable itself, but it can access the array members.</span></span>  
  
## <a name="ability-to-modify"></a><span data-ttu-id="c776b-121">Capacité à modifier</span><span class="sxs-lookup"><span data-stu-id="c776b-121">Ability to Modify</span></span>  
 <span data-ttu-id="c776b-122">Lorsque vous passez un élément non modifiable en tant qu’argument, la procédure ne peut jamais modifier dans le code appelant, qu’il soit passé `ByVal` ou `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="c776b-122">When you pass a nonmodifiable element as an argument, the procedure can never modify it in the calling code, whether it is passed `ByVal` or `ByRef`.</span></span>  
  
 <span data-ttu-id="c776b-123">Pour un élément modifiable, le tableau suivant résume l’interaction entre le type d’élément et le mécanisme de passage.</span><span class="sxs-lookup"><span data-stu-id="c776b-123">For a modifiable element, the following table summarizes the interaction between the element type and the passing mechanism.</span></span>  
  
|<span data-ttu-id="c776b-124">Type d'élément</span><span class="sxs-lookup"><span data-stu-id="c776b-124">Element type</span></span>|<span data-ttu-id="c776b-125">Passé`ByVal`</span><span class="sxs-lookup"><span data-stu-id="c776b-125">Passed `ByVal`</span></span>|<span data-ttu-id="c776b-126">Passé`ByRef`</span><span class="sxs-lookup"><span data-stu-id="c776b-126">Passed `ByRef`</span></span>|  
|------------------|--------------------|--------------------|  
|<span data-ttu-id="c776b-127">Type de valeur (contient uniquement une valeur)</span><span class="sxs-lookup"><span data-stu-id="c776b-127">Value type (contains only a value)</span></span>|<span data-ttu-id="c776b-128">La procédure ne peut pas modifier la variable ou l’un de ses membres.</span><span class="sxs-lookup"><span data-stu-id="c776b-128">The procedure cannot change the variable or any of its members.</span></span>|<span data-ttu-id="c776b-129">La procédure peut modifier la variable et ses membres.</span><span class="sxs-lookup"><span data-stu-id="c776b-129">The procedure can change the variable and its members.</span></span>|  
|<span data-ttu-id="c776b-130">Type référence (contient un pointeur vers une instance de classe ou une structure)</span><span class="sxs-lookup"><span data-stu-id="c776b-130">Reference type (contains a pointer to a class or structure instance)</span></span>|<span data-ttu-id="c776b-131">La procédure ne peut pas modifier la variable, mais peut modifier les membres de l’instance vers laquelle il pointe.</span><span class="sxs-lookup"><span data-stu-id="c776b-131">The procedure cannot change the variable but can change members of the instance to which it points.</span></span>|<span data-ttu-id="c776b-132">La procédure peut modifier la variable et les membres de l’instance vers laquelle il pointe.</span><span class="sxs-lookup"><span data-stu-id="c776b-132">The procedure can change the variable and members of the instance to which it points.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c776b-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c776b-133">See Also</span></span>  
 <span data-ttu-id="c776b-134">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-134">[Procedures](./index.md) </span></span>  
<span data-ttu-id="c776b-135"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-135"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="c776b-136"> [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-136"> [How to: Pass Arguments to a Procedure](./how-to-pass-arguments-to-a-procedure.md) </span></span>  
<span data-ttu-id="c776b-137"> [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-137"> [Passing Arguments by Value and by Reference](./passing-arguments-by-value-and-by-reference.md) </span></span>  
<span data-ttu-id="c776b-138"> [Différences entre les Arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-138"> [Differences Between Modifiable and Nonmodifiable Arguments](./differences-between-modifiable-and-nonmodifiable-arguments.md) </span></span>  
<span data-ttu-id="c776b-139"> [Comment : modifier la valeur d’un Argument de procédure](./how-to-change-the-value-of-a-procedure-argument.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-139"> [How to: Change the Value of a Procedure Argument](./how-to-change-the-value-of-a-procedure-argument.md) </span></span>  
<span data-ttu-id="c776b-140"> [Comment : protéger un Argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-140"> [How to: Protect a Procedure Argument Against Value Changes](./how-to-protect-a-procedure-argument-against-value-changes.md) </span></span>  
<span data-ttu-id="c776b-141"> [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-141"> [How to: Force an Argument to Be Passed by Value](./how-to-force-an-argument-to-be-passed-by-value.md) </span></span>  
<span data-ttu-id="c776b-142"> [Passage des Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md) </span><span class="sxs-lookup"><span data-stu-id="c776b-142"> [Passing Arguments by Position and by Name](./passing-arguments-by-position-and-by-name.md) </span></span>  
<span data-ttu-id="c776b-143"> [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span><span class="sxs-lookup"><span data-stu-id="c776b-143"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)</span></span>
