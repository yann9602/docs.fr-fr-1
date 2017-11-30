---
title: "Comment : contrôler la disponibilité d'une variable (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 004fb101661fadeaee084e1f9374ca8332ac7234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a><span data-ttu-id="99c32-102">Comment : contrôler la disponibilité d'une variable (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="99c32-102">How to: Control the Availability of a Variable (Visual Basic)</span></span>
<span data-ttu-id="99c32-103">Contrôle de la disponibilité d’une variable en spécifiant son *niveau d’accès*.</span><span class="sxs-lookup"><span data-stu-id="99c32-103">You control the availability of a variable by specifying its *access level*.</span></span> <span data-ttu-id="99c32-104">Le niveau d’accès détermine quel code est autorisé à lire ou écrire dans la variable.</span><span class="sxs-lookup"><span data-stu-id="99c32-104">The access level determines what code has permission to read or write to the variable.</span></span>  
  
-   <span data-ttu-id="99c32-105">*Variables membres* (défini au niveau du module et en dehors de toute procédure) par défaut d’un accès public, ce qui signifie que tout code qui Affichez-les pour y accéder.</span><span class="sxs-lookup"><span data-stu-id="99c32-105">*Member variables* (defined at module level and outside any procedure) default to public access, which means any code that can see them can access them.</span></span> <span data-ttu-id="99c32-106">Vous pouvez le modifier en spécifiant un modificateur d’accès.</span><span class="sxs-lookup"><span data-stu-id="99c32-106">You can change this by specifying an access modifier.</span></span>  
  
-   <span data-ttu-id="99c32-107">*Variables locales* (défini à l’intérieur d’une procédure) nominalement ont un accès public, bien que seul le code dans leur procédure permettre y accéder.</span><span class="sxs-lookup"><span data-stu-id="99c32-107">*Local variables* (defined inside a procedure) nominally have public access, although only code within their procedure can access them.</span></span> <span data-ttu-id="99c32-108">Vous ne pouvez pas modifier le niveau d’accès d’une variable locale, mais vous pouvez modifier le niveau d’accès de la procédure qui le contient.</span><span class="sxs-lookup"><span data-stu-id="99c32-108">You cannot change the access level of a local variable, but you can change the access level of the procedure that contains it.</span></span>  
  
 <span data-ttu-id="99c32-109">Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="99c32-109">For more information, see [Access levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="private-and-public-access"></a><span data-ttu-id="99c32-110">Accès privé et Public</span><span class="sxs-lookup"><span data-stu-id="99c32-110">Private and Public Access</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a><span data-ttu-id="99c32-111">Pour rendre une variable accessible uniquement à partir de son module, classe ou structure</span><span class="sxs-lookup"><span data-stu-id="99c32-111">To make a variable accessible only from within its module, class, or structure</span></span>  
  
1.  <span data-ttu-id="99c32-112">Place le [instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pour la variable à l’intérieur du module, classe ou structure, mais en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="99c32-112">Place the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) for the variable inside the module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="99c32-113">Inclure le [privé](../../../../visual-basic/language-reference/modifiers/private.md) mot clé dans la `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="99c32-113">Include the [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="99c32-114">Vous pouvez lire ou écrire dans la variable à partir de n’importe où dans le module, classe ou structure, mais pas à l’extérieur.</span><span class="sxs-lookup"><span data-stu-id="99c32-114">You can read or write to the variable from anywhere within the module, class, or structure, but not from outside it.</span></span>  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a><span data-ttu-id="99c32-115">Pour rendre une variable accessible à partir de n’importe quel code qui peut le consulter</span><span class="sxs-lookup"><span data-stu-id="99c32-115">To make a variable accessible from any code that can see it</span></span>  
  
1.  <span data-ttu-id="99c32-116">Pour une variable membre, placez la `Dim` instruction de la variable à l’intérieur d’un module, classe ou structure, mais en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="99c32-116">For a member variable, place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="99c32-117">Inclure le [Public](../../../../visual-basic/language-reference/modifiers/public.md) mot clé dans la `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="99c32-117">Include the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="99c32-118">Vous pouvez lire ou écrire dans la variable à partir de n’importe quel code qui interagit avec votre assembly.</span><span class="sxs-lookup"><span data-stu-id="99c32-118">You can read or write to the variable from any code that interoperates with your assembly.</span></span>  
  
 <span data-ttu-id="99c32-119">ou</span><span class="sxs-lookup"><span data-stu-id="99c32-119">-or-</span></span>  
  
1.  <span data-ttu-id="99c32-120">Pour une variable locale, placez la `Dim` instruction de la variable à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="99c32-120">For a local variable, place the `Dim` statement for the variable inside a procedure.</span></span>  
  
2.  <span data-ttu-id="99c32-121">N’incluez pas le `Public` mot clé dans la `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="99c32-121">Do not include the `Public` keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="99c32-122">Vous pouvez lire ou écrire dans la variable à partir de n’importe où dans la procédure, mais pas à l’extérieur.</span><span class="sxs-lookup"><span data-stu-id="99c32-122">You can read or write to the variable from anywhere within the procedure, but not from outside it.</span></span>  
  
## <a name="protected-and-friend-access"></a><span data-ttu-id="99c32-123">Protégé et un accès ami</span><span class="sxs-lookup"><span data-stu-id="99c32-123">Protected and Friend Access</span></span>  
 <span data-ttu-id="99c32-124">Vous pouvez limiter le niveau d’accès d’une variable à sa classe et toutes les classes dérivées, ou à son assembly.</span><span class="sxs-lookup"><span data-stu-id="99c32-124">You can limit the access level of a variable to its class and any derived classes, or to its assembly.</span></span> <span data-ttu-id="99c32-125">Vous pouvez également spécifier l’union de ces limitations, ce qui autorise l’accès à partir du code dans n’importe quelle classe dérivée ou dans tout autre emplacement dans le même assembly.</span><span class="sxs-lookup"><span data-stu-id="99c32-125">You can also specify the union of these limitations, which allows access from code in any derived class or in any other place in the same assembly.</span></span> <span data-ttu-id="99c32-126">Vous spécifiez cette union en combinant les `Protected` et `Friend` mots clés dans la même déclaration.</span><span class="sxs-lookup"><span data-stu-id="99c32-126">You specify this union by combining the `Protected` and `Friend` keywords in the same declaration.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a><span data-ttu-id="99c32-127">Pour rendre une variable accessible uniquement à partir de sa classe et toutes les classes dérivées</span><span class="sxs-lookup"><span data-stu-id="99c32-127">To make a variable accessible only from within its class and any derived classes</span></span>  
  
1.  <span data-ttu-id="99c32-128">Place la `Dim` instruction de la variable à l’intérieur d’une classe, mais en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="99c32-128">Place the `Dim` statement for the variable inside a class, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="99c32-129">Inclure le [protégé](../../../../visual-basic/language-reference/modifiers/protected.md) mot clé dans la `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="99c32-129">Include the [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="99c32-130">Vous pouvez lire ou écrire dans la variable à partir de n’importe où dans la classe, ainsi que depuis toute classe dérivée à partir de celui-ci, mais pas en dehors de toute classe dans la chaîne de dérivation.</span><span class="sxs-lookup"><span data-stu-id="99c32-130">You can read or write to the variable from anywhere within the class, as well as from within any class derived from it, but not from outside any class in the derivation chain.</span></span>  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a><span data-ttu-id="99c32-131">Pour rendre une variable accessible uniquement à partir du même assembly</span><span class="sxs-lookup"><span data-stu-id="99c32-131">To make a variable accessible only from within the same assembly</span></span>  
  
1.  <span data-ttu-id="99c32-132">Place la `Dim` instruction de la variable à l’intérieur d’un module, classe ou structure, mais en dehors de toute procédure.</span><span class="sxs-lookup"><span data-stu-id="99c32-132">Place the `Dim` statement for the variable inside a module, class, or structure, but outside any procedure.</span></span>  
  
2.  <span data-ttu-id="99c32-133">Inclure le [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) mot clé dans la `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="99c32-133">Include the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) keyword in the `Dim` statement.</span></span>  
  
     <span data-ttu-id="99c32-134">Vous pouvez lire ou écrire dans la variable à partir de n’importe où dans le module, classe ou structure, ainsi qu’à partir de n’importe quel code dans le même assembly, mais pas à l’extérieur de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="99c32-134">You can read or write to the variable from anywhere within the module, class, or structure, as well as from any code in the same assembly, but not from outside the assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99c32-135">Exemple</span><span class="sxs-lookup"><span data-stu-id="99c32-135">Example</span></span>  
 <span data-ttu-id="99c32-136">L’exemple suivant montre des déclarations de variables avec `Public`, `Protected`, `Friend`, `Protected Friend`, et `Private` niveaux d’accès.</span><span class="sxs-lookup"><span data-stu-id="99c32-136">The following example shows declarations of variables with `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private` access levels.</span></span> <span data-ttu-id="99c32-137">Notez que lorsque la `Dim` instruction spécifie un niveau d’accès, vous n’avez pas besoin d’inclure le `Dim` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="99c32-137">Note that when the `Dim` statement specifies an access level, you do not need to include the `Dim` keyword.</span></span>  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a><span data-ttu-id="99c32-138">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="99c32-138">.NET Framework Security</span></span>  
 <span data-ttu-id="99c32-139">Le plus restrictif le niveau d’accès d’une variable, moins vous risquez constituant un code malveillant peut incorrect utiliser.</span><span class="sxs-lookup"><span data-stu-id="99c32-139">The more restrictive the access level of a variable, the smaller the chances that malicious code can make improper use of it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99c32-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="99c32-140">See Also</span></span>  
 [<span data-ttu-id="99c32-141">Niveaux d’accès dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="99c32-141">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="99c32-142">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="99c32-142">Dim Statement</span></span>](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="99c32-143">Public</span><span class="sxs-lookup"><span data-stu-id="99c32-143">Public</span></span>](../../../../visual-basic/language-reference/modifiers/public.md)  
 [<span data-ttu-id="99c32-144">Protected</span><span class="sxs-lookup"><span data-stu-id="99c32-144">Protected</span></span>](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [<span data-ttu-id="99c32-145">Friend</span><span class="sxs-lookup"><span data-stu-id="99c32-145">Friend</span></span>](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [<span data-ttu-id="99c32-146">Private</span><span class="sxs-lookup"><span data-stu-id="99c32-146">Private</span></span>](../../../../visual-basic/language-reference/modifiers/private.md)
