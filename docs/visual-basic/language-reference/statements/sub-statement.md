---
title: Sub, instruction (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Sub
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, Sub statements
- procedures, creating
- declaring procedures, Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword, Sub statements
- Optional keyword, Sub statements
- declarations, procedures
- Sub keyword
- Handles keyword, Sub statements
- Protected Friend keyword
- ParamArray keyword, Sub statements
- Implements keyword, Sub statements
- Sub statement
- subroutines
- ByRef keyword, Sub statements
- Sub procedures, Sub statement
- recursive procedures
- Private keyword, Sub statements
- Friend keyword, Sub statements
- Exit statement, Sub statements
- procedures, Sub
- End keyword, Sub statements
- ByVal keyword, Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: 52
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
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 61853a4f2321837683997b8e4241b688bc9f622c
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="4793b-102">Sub, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4793b-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="4793b-103">Déclare le nom, paramètres et le code qui définissent une `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4793b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4793b-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="4793b-105">Composants</span><span class="sxs-lookup"><span data-stu-id="4793b-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="4793b-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-106">Optional.</span></span> <span data-ttu-id="4793b-107">Consultez la page [liste d’attributs](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="4793b-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-108">Optional.</span></span> <span data-ttu-id="4793b-109">Indique la définition d’une méthode partielle.</span><span class="sxs-lookup"><span data-stu-id="4793b-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="4793b-110">Consultez la page [méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="4793b-111">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-111">Optional.</span></span> <span data-ttu-id="4793b-112">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="4793b-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4793b-113">Public</span><span class="sxs-lookup"><span data-stu-id="4793b-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="4793b-114">Protected</span><span class="sxs-lookup"><span data-stu-id="4793b-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="4793b-115">Friend</span><span class="sxs-lookup"><span data-stu-id="4793b-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="4793b-116">Private</span><span class="sxs-lookup"><span data-stu-id="4793b-116">Private</span></span>](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="4793b-117">Consultez la page [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-117">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="4793b-118">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-118">Optional.</span></span> <span data-ttu-id="4793b-119">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="4793b-119">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4793b-120">Surcharges</span><span class="sxs-lookup"><span data-stu-id="4793b-120">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="4793b-121">Overrides</span><span class="sxs-lookup"><span data-stu-id="4793b-121">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="4793b-122">Overridable</span><span class="sxs-lookup"><span data-stu-id="4793b-122">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="4793b-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4793b-123">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="4793b-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="4793b-124">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="4793b-125">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-125">Optional.</span></span> <span data-ttu-id="4793b-126">Consultez la page [partagé](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-126">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="4793b-127">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-127">Optional.</span></span> <span data-ttu-id="4793b-128">Consultez la page [ombres](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-128">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="4793b-129">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-129">Optional.</span></span> <span data-ttu-id="4793b-130">Consultez la page [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-130">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="4793b-131">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4793b-131">Required.</span></span> <span data-ttu-id="4793b-132">Nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-132">Name of the procedure.</span></span> <span data-ttu-id="4793b-133">Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-133">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="4793b-134">Pour créer une procédure de constructeur pour une classe, définissez le nom d’un `Sub` procédure pour la `New` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="4793b-134">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="4793b-135">Pour plus d’informations, consultez [durée de vie : comment les objets sont création et destruction](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-135">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="4793b-136">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-136">Optional.</span></span> <span data-ttu-id="4793b-137">Liste des paramètres de type pour une procédure générique.</span><span class="sxs-lookup"><span data-stu-id="4793b-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="4793b-138">Consultez la page [tapez liste](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-138">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="4793b-139">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-139">Optional.</span></span> <span data-ttu-id="4793b-140">Liste des noms de variables locales représentant les paramètres de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="4793b-141">Consultez la page [liste de paramètres](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-141">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="4793b-142">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-142">Optional.</span></span> <span data-ttu-id="4793b-143">Indique que cette procédure implémente une ou plusieurs `Sub` procédures, chacune étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-143">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="4793b-144">Consultez la page [implémente l’instruction](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-144">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="4793b-145">Obligatoire si `Implements` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4793b-145">Required if `Implements` is supplied.</span></span> <span data-ttu-id="4793b-146">Liste des procédures `Sub` en cours d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="4793b-146">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="4793b-147">Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="4793b-147">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="4793b-148">Élément</span><span class="sxs-lookup"><span data-stu-id="4793b-148">Part</span></span>|<span data-ttu-id="4793b-149">Description</span><span class="sxs-lookup"><span data-stu-id="4793b-149">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="4793b-150">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4793b-150">Required.</span></span> <span data-ttu-id="4793b-151">Nom d’une interface implémentée par cette procédure classe ou la structure conteneur.</span><span class="sxs-lookup"><span data-stu-id="4793b-151">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="4793b-152">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4793b-152">Required.</span></span> <span data-ttu-id="4793b-153">Nom par lequel la procédure est définie dans `interface`.</span><span class="sxs-lookup"><span data-stu-id="4793b-153">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="4793b-154">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-154">Optional.</span></span> <span data-ttu-id="4793b-155">Indique que cette procédure peut gérer un ou plusieurs événements spécifiques.</span><span class="sxs-lookup"><span data-stu-id="4793b-155">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="4793b-156">Consultez la page [gère](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-156">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="4793b-157">Obligatoire si `Handles` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="4793b-157">Required if `Handles` is supplied.</span></span> <span data-ttu-id="4793b-158">Liste des événements gérés par cette procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-158">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="4793b-159">Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="4793b-159">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="4793b-160">Élément</span><span class="sxs-lookup"><span data-stu-id="4793b-160">Part</span></span>|<span data-ttu-id="4793b-161">Description</span><span class="sxs-lookup"><span data-stu-id="4793b-161">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="4793b-162">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4793b-162">Required.</span></span> <span data-ttu-id="4793b-163">Variable objet déclarée avec le type de données de la classe ou structure qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="4793b-163">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="4793b-164">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="4793b-164">Required.</span></span> <span data-ttu-id="4793b-165">Nom de l’événement que gère cette procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-165">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="4793b-166">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4793b-166">Optional.</span></span> <span data-ttu-id="4793b-167">Bloc d’instructions à exécuter dans cette procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-167">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="4793b-168">Met fin à la définition de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-168">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4793b-169">Remarques</span><span class="sxs-lookup"><span data-stu-id="4793b-169">Remarks</span></span>  
 <span data-ttu-id="4793b-170">Tout le code exécutable doit être à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-170">All executable code must be inside a procedure.</span></span> <span data-ttu-id="4793b-171">Utilisez un `Sub` procédure lorsque vous ne souhaitez pas retourner une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="4793b-171">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="4793b-172">Utilisez un `Function` procédure lorsque vous souhaitez retourner une valeur.</span><span class="sxs-lookup"><span data-stu-id="4793b-172">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="4793b-173">Définition d’une procédure Sub</span><span class="sxs-lookup"><span data-stu-id="4793b-173">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="4793b-174">Vous pouvez définir un `Sub` procédure uniquement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="4793b-174">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="4793b-175">Le contexte de déclaration pour une procédure sub doit, par conséquent, être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="4793b-175">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="4793b-176">Pour plus d’informations, consultez [contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-176">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="4793b-177">`Sub`les procédures par défaut d’un accès public.</span><span class="sxs-lookup"><span data-stu-id="4793b-177">`Sub` procedures default to public access.</span></span> <span data-ttu-id="4793b-178">Vous pouvez ajuster leurs niveaux d’accès à l’aide des modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="4793b-178">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="4793b-179">Si la procédure utilise le `Implements` (mot clé), la classe ou la structure conteneur doit avoir un `Implements` instruction qui suit immédiatement sa `Class` ou `Structure` instruction.</span><span class="sxs-lookup"><span data-stu-id="4793b-179">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="4793b-180">Le `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="4793b-180">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="4793b-181">Toutefois, le nom par lequel une interface définit les `Sub` (dans `definedname`) ne doit pas nécessairement correspondre au nom de cette procédure (dans `name`).</span><span class="sxs-lookup"><span data-stu-id="4793b-181">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="4793b-182">Retour d’une procédure Sub</span><span class="sxs-lookup"><span data-stu-id="4793b-182">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="4793b-183">Lorsqu’un `Sub` procédure retourne au code appelant, l’exécution se poursuit avec l’instruction après l’instruction qui l’a appelée.</span><span class="sxs-lookup"><span data-stu-id="4793b-183">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="4793b-184">L’exemple suivant affiche un retour d’un `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-184">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="4793b-185">Le `Exit Sub` et `Return` instructions provoquent la sortie immédiate d’un `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-185">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="4793b-186">Un nombre quelconque de `Exit Sub` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Sub` et `Return` instructions.</span><span class="sxs-lookup"><span data-stu-id="4793b-186">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="4793b-187">Appel d’une procédure Sub</span><span class="sxs-lookup"><span data-stu-id="4793b-187">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="4793b-188">Vous appelez un `Sub` procédure en utilisant le nom de procédure dans une instruction, puis en suivant ce nom à sa liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="4793b-188">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="4793b-189">Vous pouvez omettre les parenthèses uniquement si vous ne fournissez pas d’arguments.</span><span class="sxs-lookup"><span data-stu-id="4793b-189">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="4793b-190">Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="4793b-190">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="4793b-191">A `Sub` procédure et un `Function` procédure peut avoir des paramètres et effectuer une série d’instructions.</span><span class="sxs-lookup"><span data-stu-id="4793b-191">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="4793b-192">Toutefois, un `Function` procédure retourne une valeur, ainsi qu’un `Sub` procédure ne.</span><span class="sxs-lookup"><span data-stu-id="4793b-192">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="4793b-193">Par conséquent, vous ne pouvez pas utiliser un `Sub` procédure dans une expression.</span><span class="sxs-lookup"><span data-stu-id="4793b-193">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="4793b-194">Vous pouvez utiliser la `Call` (mot clé) lorsque vous appelez un `Sub` procédure, mais ce mot clé n’est pas recommandé pour la plupart des utilisations.</span><span class="sxs-lookup"><span data-stu-id="4793b-194">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="4793b-195">Pour plus d’informations, consultez [instruction Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-195">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="4793b-196">Visual Basic réorganise quelquefois les expressions arithmétiques pour améliorer les performances internes.</span><span class="sxs-lookup"><span data-stu-id="4793b-196">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="4793b-197">Pour cette raison, si votre liste d’arguments inclut des expressions qui appellent d’autres procédures, vous ne devez pas supposer que ces expressions seront appelées dans un ordre particulier.</span><span class="sxs-lookup"><span data-stu-id="4793b-197">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="4793b-198">Procédures Sub d’async</span><span class="sxs-lookup"><span data-stu-id="4793b-198">Async Sub Procedures</span></span>  
 <span data-ttu-id="4793b-199">À l’aide de la fonctionnalité Async, vous pouvez appeler des fonctions asynchrones sans utiliser de rappels explicites ou fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="4793b-199">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="4793b-200">Si vous marquez une procédure avec le [Async](../modifiers/async.md) modificateur, vous pouvez utiliser la [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-200">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="4793b-201">Lorsque le contrôle atteint une `Await` expression dans le `Async` procédure, contrôle retourne à l’appelant, et la progression de la procédure est suspendue jusqu'à ce que la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="4793b-201">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="4793b-202">Lorsque la tâche est terminée, l’exécution peut reprendre dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-202">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4793b-203">Un `Async` procédure retourne à l’appelant lorsque soit le premier objet await qui n’est pas encore terminé est rencontrée ou à la fin de la `Async` procédure est atteint, selon ce qui se produit en premier.</span><span class="sxs-lookup"><span data-stu-id="4793b-203">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="4793b-204">Vous pouvez également marquer un [Function, instruction](function-statement.md) avec la `Async` modificateur.</span><span class="sxs-lookup"><span data-stu-id="4793b-204">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="4793b-205">Un `Async` fonction peut avoir un type de retour de <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="4793b-205">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="4793b-206">Un exemple plus loin dans cette rubrique montre un `Async` fonction qui a un type de retour de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="4793b-206">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="4793b-207">`Async``Sub` procédures sont principalement utilisés pour les gestionnaires d’événements, où une valeur ne peut pas être retournée.</span><span class="sxs-lookup"><span data-stu-id="4793b-207">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="4793b-208">Un `Async``Sub` procédure ne peut pas être attendue et que l’appelant d’une `Async``Sub` procédure ne peut pas intercepter des exceptions qui le `Sub` lève une exception de la procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-208">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="4793b-209">Un `Async` procédure ne peut pas déclarer de [ByRef](../modifiers/byref.md) paramètres.</span><span class="sxs-lookup"><span data-stu-id="4793b-209">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="4793b-210">Pour plus d’informations sur `Async` les procédures, consultez [programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md), [flux de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), et [les Types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4793b-210">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4793b-211">Exemple</span><span class="sxs-lookup"><span data-stu-id="4793b-211">Example</span></span>  
 <span data-ttu-id="4793b-212">L’exemple suivant utilise le `Sub` instruction pour définir le nom, les paramètres et les code formant le corps d’un `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-212">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="4793b-213">[!code-vb[VbVbalrStatements&#58;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="4793b-213">[!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="4793b-214">Exemple</span><span class="sxs-lookup"><span data-stu-id="4793b-214">Example</span></span>  
 <span data-ttu-id="4793b-215">Dans l’exemple suivant, `DelayAsync` est une une `Async``Function` qui a un type de retour de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="4793b-215">In the following example, `DelayAsync` is an an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4793b-216">`DelayAsync` a une instruction `Return` qui retourne un entier.</span><span class="sxs-lookup"><span data-stu-id="4793b-216">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="4793b-217">Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour de `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="4793b-217">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="4793b-218">Étant donné que le type de retour est `Task(Of Integer)`, l’évaluation de la `Await` expression `DoSomethingAsync` génère un entier, comme le montre l’instruction suivante : `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="4793b-218">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="4793b-219">Le `startButton_Click` procédure est un exemple d’un `Async Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="4793b-219">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="4793b-220">Étant donné que `DoSomethingAsync` est un `Async` la tâche pour l’appel à une fonction, `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="4793b-220">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="4793b-221">Le `startButton_Click``Sub` procédure doit être définie avec la `Async` modificateur, car elle possède une `Await` expression.</span><span class="sxs-lookup"><span data-stu-id="4793b-221">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 <span data-ttu-id="4793b-222">[!code-vb[csAsyncMethod n °&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="4793b-222">[!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4793b-223">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4793b-223">See Also</span></span>  
 <span data-ttu-id="4793b-224">[Implements (instruction)](implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-224">[Implements Statement](implements-statement.md) </span></span>  
<span data-ttu-id="4793b-225"> [Function (instruction)](function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-225"> [Function Statement](function-statement.md) </span></span>  
<span data-ttu-id="4793b-226"> [Liste de paramètres](parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-226"> [Parameter List](parameter-list.md) </span></span>  
<span data-ttu-id="4793b-227"> [Dim (instruction)](dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-227"> [Dim Statement](dim-statement.md) </span></span>  
<span data-ttu-id="4793b-228"> [Call, instruction](call-statement.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-228"> [Call Statement](call-statement.md) </span></span>  
<span data-ttu-id="4793b-229"> [Of](of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-229"> [Of](of-clause.md) </span></span>  
<span data-ttu-id="4793b-230"> [Tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-230"> [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span></span>  
<span data-ttu-id="4793b-231"> [Comment : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-231"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="4793b-232"> [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="4793b-232"> [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="4793b-233"> [Méthodes partielles](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)</span><span class="sxs-lookup"><span data-stu-id="4793b-233"> [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)</span></span>

