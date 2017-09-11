---
title: Function, instruction (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Function
dev_langs:
- VB
helpviewer_keywords:
- procedures, creating
- Function procedures, Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword, Function statements
- Private keyword, Function statements
- declarations, procedures
- procedures, declaration
- Public keyword, in Function statement
- ByVal keyword, Function statements
- procedures, recursive
- Implements keyword, Function statements
- procedures, returning values
- Exit statement, in Function procedures
- recursive procedures
- As keyword, in Function statement
- Optional keyword, Function statements
- Function statement
- Visual Basic code, Function procedures
- procedures, function
- ByRef keyword, Function statements
- Friend keyword, Function statements
- End keyword, Function statements
- Handles keyword, Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: 62
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
ms.openlocfilehash: d875fe6df3ef7ac9390346588b1c2d48497d7116
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="ac516-102">Function, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ac516-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="ac516-103">Déclare le nom, paramètres et le code qui définissent une `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac516-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac516-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="ac516-105">Composants</span><span class="sxs-lookup"><span data-stu-id="ac516-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="ac516-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-106">Optional.</span></span> <span data-ttu-id="ac516-107">Consultez la page [liste d’attributs](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="ac516-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-108">Optional.</span></span> <span data-ttu-id="ac516-109">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ac516-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="ac516-110">Public</span><span class="sxs-lookup"><span data-stu-id="ac516-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="ac516-111">Protected</span><span class="sxs-lookup"><span data-stu-id="ac516-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="ac516-112">Friend</span><span class="sxs-lookup"><span data-stu-id="ac516-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="ac516-113">Private</span><span class="sxs-lookup"><span data-stu-id="ac516-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="ac516-114">Consultez la page [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-114">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="ac516-115">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-115">Optional.</span></span> <span data-ttu-id="ac516-116">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ac516-116">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="ac516-117">Surcharges</span><span class="sxs-lookup"><span data-stu-id="ac516-117">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="ac516-118">Overrides</span><span class="sxs-lookup"><span data-stu-id="ac516-118">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="ac516-119">Overridable</span><span class="sxs-lookup"><span data-stu-id="ac516-119">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="ac516-120">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ac516-120">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="ac516-121">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ac516-121">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="ac516-122">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-122">Optional.</span></span> <span data-ttu-id="ac516-123">Consultez la page [partagé](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-123">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="ac516-124">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-124">Optional.</span></span> <span data-ttu-id="ac516-125">Consultez la page [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-125">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="ac516-126">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-126">Optional.</span></span> <span data-ttu-id="ac516-127">Consultez la page [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-127">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="ac516-128">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-128">Optional.</span></span> <span data-ttu-id="ac516-129">Consultez la page [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-129">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="ac516-130">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ac516-130">Required.</span></span> <span data-ttu-id="ac516-131">Nom de la procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-131">Name of the procedure.</span></span> <span data-ttu-id="ac516-132">Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-132">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="ac516-133">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-133">Optional.</span></span> <span data-ttu-id="ac516-134">Liste des paramètres de type pour une procédure générique.</span><span class="sxs-lookup"><span data-stu-id="ac516-134">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="ac516-135">Consultez la page [tapez liste](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-135">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="ac516-136">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-136">Optional.</span></span> <span data-ttu-id="ac516-137">Liste des noms de variables locales représentant les paramètres de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-137">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="ac516-138">Consultez la page [liste de paramètres](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-138">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="ac516-139">Requis si `Option Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="ac516-139">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="ac516-140">Type de données de la valeur retournée par cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-140">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="ac516-141">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-141">Optional.</span></span> <span data-ttu-id="ac516-142">Indique que cette procédure implémente une ou plusieurs `Function` procédures, chacune étant définie dans une interface implémentée par la classe ou la structure conteneur de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-142">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="ac516-143">Consultez la page [implémente l’instruction](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-143">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="ac516-144">Obligatoire si `Implements` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ac516-144">Required if `Implements` is supplied.</span></span> <span data-ttu-id="ac516-145">Liste des procédures `Function` en cours d'implémentation.</span><span class="sxs-lookup"><span data-stu-id="ac516-145">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="ac516-146">Chaque `implementedprocedure` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ac516-146">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="ac516-147">Élément</span><span class="sxs-lookup"><span data-stu-id="ac516-147">Part</span></span>|<span data-ttu-id="ac516-148">Description</span><span class="sxs-lookup"><span data-stu-id="ac516-148">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="ac516-149">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ac516-149">Required.</span></span> <span data-ttu-id="ac516-150">Nom d’une interface implémentée par cette procédure classe ou la structure conteneur.</span><span class="sxs-lookup"><span data-stu-id="ac516-150">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="ac516-151">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ac516-151">Required.</span></span> <span data-ttu-id="ac516-152">Nom par lequel la procédure est définie dans `interface`.</span><span class="sxs-lookup"><span data-stu-id="ac516-152">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="ac516-153">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-153">Optional.</span></span> <span data-ttu-id="ac516-154">Indique que cette procédure peut gérer un ou plusieurs événements spécifiques.</span><span class="sxs-lookup"><span data-stu-id="ac516-154">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="ac516-155">Consultez la page [gère](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-155">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="ac516-156">Obligatoire si `Handles` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ac516-156">Required if `Handles` is supplied.</span></span> <span data-ttu-id="ac516-157">Liste des événements gérés par cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-157">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="ac516-158">Chaque `eventspecifier` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ac516-158">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="ac516-159">Élément</span><span class="sxs-lookup"><span data-stu-id="ac516-159">Part</span></span>|<span data-ttu-id="ac516-160">Description</span><span class="sxs-lookup"><span data-stu-id="ac516-160">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="ac516-161">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ac516-161">Required.</span></span> <span data-ttu-id="ac516-162">Variable objet déclarée avec le type de données de la classe ou structure qui déclenche l’événement.</span><span class="sxs-lookup"><span data-stu-id="ac516-162">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="ac516-163">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ac516-163">Required.</span></span> <span data-ttu-id="ac516-164">Nom de l’événement que gère cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-164">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="ac516-165">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ac516-165">Optional.</span></span> <span data-ttu-id="ac516-166">Bloc d’instructions à exécuter dans cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-166">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="ac516-167">Met fin à la définition de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-167">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ac516-168">Remarques</span><span class="sxs-lookup"><span data-stu-id="ac516-168">Remarks</span></span>  
 <span data-ttu-id="ac516-169">Tout le code exécutable doit être à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-169">All executable code must be inside a procedure.</span></span> <span data-ttu-id="ac516-170">Chaque procédure, à son tour, est déclarée dans une classe, une structure ou un module qui correspond à la classe, structure ou module conteneur.</span><span class="sxs-lookup"><span data-stu-id="ac516-170">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="ac516-171">Pour retourner une valeur au code appelant, utilisez un `Function` procédure ; sinon, utilisez un `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-171">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="ac516-172">Définition d’une fonction</span><span class="sxs-lookup"><span data-stu-id="ac516-172">Defining a Function</span></span>  
 <span data-ttu-id="ac516-173">Vous pouvez définir un `Function` procédure uniquement au niveau du module.</span><span class="sxs-lookup"><span data-stu-id="ac516-173">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="ac516-174">Par conséquent, le contexte de déclaration pour une fonction doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="ac516-174">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="ac516-175">Pour plus d’informations, consultez [contextes de déclaration et niveaux d’accès par défaut](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-175">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="ac516-176">`Function`les procédures par défaut d’un accès public.</span><span class="sxs-lookup"><span data-stu-id="ac516-176">`Function` procedures default to public access.</span></span> <span data-ttu-id="ac516-177">Vous pouvez régler leurs niveaux d’accès avec les modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="ac516-177">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="ac516-178">Un `Function` procédure peut déclarer le type de données de la valeur renvoyée de la procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-178">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="ac516-179">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, une structure, une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="ac516-179">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="ac516-180">Si vous ne spécifiez pas le `returntype` , la procédure retourne `Object`.</span><span class="sxs-lookup"><span data-stu-id="ac516-180">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="ac516-181">Si cette procédure utilise le `Implements` (mot clé), la classe ou la structure conteneur doit également avoir un `Implements` instruction qui suit immédiatement sa `Class` ou `Structure` instruction.</span><span class="sxs-lookup"><span data-stu-id="ac516-181">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="ac516-182">Le `Implements` instruction doit inclure chaque interface spécifiée dans `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="ac516-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="ac516-183">Toutefois, le nom par lequel une interface définit les `Function` (dans `definedname`) n’a pas besoin de correspondre au nom de cette procédure (dans `name`).</span><span class="sxs-lookup"><span data-stu-id="ac516-183">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac516-184">Vous pouvez utiliser des expressions lambda pour définir des expressions de fonction inline.</span><span class="sxs-lookup"><span data-stu-id="ac516-184">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="ac516-185">Pour plus d’informations, consultez [Expression de fonction](../../../visual-basic/language-reference/operators/function-expression.md) et [Expressions Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-185">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="ac516-186">Retour d’une fonction</span><span class="sxs-lookup"><span data-stu-id="ac516-186">Returning from a Function</span></span>  
 <span data-ttu-id="ac516-187">Lorsque le `Function` procédure retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui a appelé la procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-187">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="ac516-188">Pour retourner une valeur à partir d’une fonction, vous pouvez assigner la valeur au nom de la fonction ou l’inclure dans un `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="ac516-188">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="ac516-189">La `Return` instruction assigne la valeur de retour et quitte la fonction, comme le montre l’exemple suivant simultanément.</span><span class="sxs-lookup"><span data-stu-id="ac516-189">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 <span data-ttu-id="ac516-190">[!code-vb[VbVbalrStatements&#24;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac516-190">[!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="ac516-191">L’exemple suivant affecte la valeur de retour pour le nom de la fonction `myFunction` , puis utilise la `Exit Function` instruction à retourner.</span><span class="sxs-lookup"><span data-stu-id="ac516-191">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 <span data-ttu-id="ac516-192">[!code-vb[VbVbalrStatements n °&23;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac516-192">[!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]</span></span>  
  
 <span data-ttu-id="ac516-193">Le `Exit Function` et `Return` instructions provoquent la sortie immédiate d’un `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="ac516-194">Un nombre quelconque de `Exit Function` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Function` et `Return` instructions.</span><span class="sxs-lookup"><span data-stu-id="ac516-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="ac516-195">Si vous utilisez `Exit Function` sans assigner une valeur à `name`, la procédure retourne la valeur par défaut pour le type de données spécifié dans `returntype`.</span><span class="sxs-lookup"><span data-stu-id="ac516-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="ac516-196">Si `returntype` n’est pas spécifié, la procédure retourne `Nothing`, qui est la valeur par défaut `Object`.</span><span class="sxs-lookup"><span data-stu-id="ac516-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="ac516-197">Appel d’une fonction</span><span class="sxs-lookup"><span data-stu-id="ac516-197">Calling a Function</span></span>  
 <span data-ttu-id="ac516-198">Vous appelez un `Function` procédure en utilisant le nom de procédure, suivi de la liste d’arguments entre parenthèses, dans une expression.</span><span class="sxs-lookup"><span data-stu-id="ac516-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="ac516-199">Vous pouvez omettre les parenthèses uniquement si vous ne fournissez des arguments.</span><span class="sxs-lookup"><span data-stu-id="ac516-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="ac516-200">Toutefois, votre code est plus lisible si vous incluez toujours les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="ac516-200">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="ac516-201">Vous appelez un `Function` procédure fonctionne de la même façon que vous appelez n’importe quelle bibliothèque comme `Sqrt`, `Cos`, ou `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="ac516-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="ac516-202">Vous pouvez également appeler une fonction à l’aide de la `Call` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="ac516-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="ac516-203">Dans ce cas, la valeur de retour est ignorée.</span><span class="sxs-lookup"><span data-stu-id="ac516-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="ac516-204">Utilisation de le `Call` mot clé n’est pas recommandé dans la plupart des cas.</span><span class="sxs-lookup"><span data-stu-id="ac516-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="ac516-205">Pour plus d’informations, consultez [instruction Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-205">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="ac516-206">Visual Basic réorganise quelquefois les expressions arithmétiques pour améliorer les performances internes.</span><span class="sxs-lookup"><span data-stu-id="ac516-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="ac516-207">Pour cette raison, vous ne devez pas utiliser un `Function` procédure dans une expression arithmétique quand la fonction change la valeur des variables dans la même expression.</span><span class="sxs-lookup"><span data-stu-id="ac516-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="ac516-208">Fonctions asynchrones</span><span class="sxs-lookup"><span data-stu-id="ac516-208">Async Functions</span></span>  
 <span data-ttu-id="ac516-209">Le *Async* fonctionnalité vous permet d’appeler des fonctions asynchrones sans utiliser de rappels explicites ou fractionner manuellement votre code entre plusieurs fonctions ou expressions lambda.</span><span class="sxs-lookup"><span data-stu-id="ac516-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="ac516-210">Si vous marquez une fonction avec la [Async](../../../visual-basic/language-reference/modifiers/async.md) modificateur, vous pouvez utiliser la [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="ac516-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="ac516-211">Lorsque le contrôle atteint une `Await` expression dans le `Async` (fonction), contrôle retourne à l’appelant, et la progression dans la fonction est suspendue jusqu'à ce que la tâche attendue se termine.</span><span class="sxs-lookup"><span data-stu-id="ac516-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="ac516-212">Lorsque la tâche est terminée, l’exécution peut reprendre dans la fonction.</span><span class="sxs-lookup"><span data-stu-id="ac516-212">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ac516-213">Un `Async` procédure retourne à l’appelant lorsqu’il rencontre le premier objet await qui n’est pas encore terminé ou qu’il arrive à la fin de la `Async` procédure, selon ce qui se produit en premier.</span><span class="sxs-lookup"><span data-stu-id="ac516-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="ac516-214">Un `Async` fonction peut avoir un type de retour de <xref:System.Threading.Tasks.Task%601> <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="ac516-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="ac516-215">Un exemple d’une `Async` fonction qui a un type de retour de <xref:System.Threading.Tasks.Task%601>est fourni ci-dessous.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="ac516-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="ac516-216">Un `Async` fonction ne peut pas déclarer de [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) paramètres.</span><span class="sxs-lookup"><span data-stu-id="ac516-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="ac516-217">A [Sub, instruction](sub-statement.md) peuvent également être marqués avec le `Async` modificateur.</span><span class="sxs-lookup"><span data-stu-id="ac516-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="ac516-218">Cela est principalement utilisé pour les gestionnaires d’événements, où une valeur ne peut pas être retournée.</span><span class="sxs-lookup"><span data-stu-id="ac516-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="ac516-219">Un `Async``Sub` procédure ne peut pas être attendue et que l’appelant d’une `Async``Sub` procédure ne peut pas intercepter des exceptions levées par le `Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-219">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="ac516-220">Pour plus d’informations sur `Async` , consultez [programmation asynchrone avec Async et Await](../../../visual-basic/programming-guide/concepts/async/index.md), [flux de contrôle dans les programmes Async](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), et [les Types de retour Async](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="ac516-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="ac516-221">Fonctions d’itérateur</span><span class="sxs-lookup"><span data-stu-id="ac516-221">Iterator Functions</span></span>  
 <span data-ttu-id="ac516-222">Un *itérateur* fonction effectue une itération personnalisée sur une collection, par exemple, une liste ou un tableau.</span><span class="sxs-lookup"><span data-stu-id="ac516-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="ac516-223">Une fonction d’itérateur utilise le [Yield](yield-statement.md) instruction pour retourner chaque élément un à la fois.</span><span class="sxs-lookup"><span data-stu-id="ac516-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="ac516-224">Lorsqu’un [Yield](yield-statement.md) instruction est atteinte, l’emplacement actuel dans le code est mémorisé.</span><span class="sxs-lookup"><span data-stu-id="ac516-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="ac516-225">L’exécution redémarrera à partir de cet emplacement la prochaine fois que la fonction d’itérateur est appelée.</span><span class="sxs-lookup"><span data-stu-id="ac516-225">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="ac516-226">Vous appelez un itérateur depuis le code client en utilisant un [For Each... Suivant](for-each-next-statement.md) instruction.</span><span class="sxs-lookup"><span data-stu-id="ac516-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="ac516-227">Le type de retour d’une fonction d’itérateur peut être <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="ac516-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="ac516-228">Pour plus d’informations, consultez [Itérateurs](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="ac516-228">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac516-229">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac516-229">Example</span></span>  
 <span data-ttu-id="ac516-230">L’exemple suivant utilise le `Function` instruction pour déclarer le nom, les paramètres et les code formant le corps d’un `Function` procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="ac516-231">Le `ParamArray` modificateur permet à la fonction d’accepter un nombre variable d’arguments.</span><span class="sxs-lookup"><span data-stu-id="ac516-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 <span data-ttu-id="ac516-232">[!code-vb[VbVbalrStatements&#25;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac516-232">[!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac516-233">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac516-233">Example</span></span>  
 <span data-ttu-id="ac516-234">L’exemple suivant appelle la fonction déclarée dans l’exemple précédent.</span><span class="sxs-lookup"><span data-stu-id="ac516-234">The following example invokes the function declared in the preceding example.</span></span>  
  
 <span data-ttu-id="ac516-235">[!code-vb[VbVbalrStatements&#26;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac516-235">[!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac516-236">Exemple</span><span class="sxs-lookup"><span data-stu-id="ac516-236">Example</span></span>  
 <span data-ttu-id="ac516-237">Dans l’exemple suivant, `DelayAsync` est un `Async``Function` qui a un type de retour de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="ac516-237">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="ac516-238">`DelayAsync` a une instruction `Return` qui retourne un entier.</span><span class="sxs-lookup"><span data-stu-id="ac516-238">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="ac516-239">Par conséquent, la déclaration de fonction de `DelayAsync` doit avoir un type de retour de `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="ac516-239">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="ac516-240">Étant donné que le type de retour est `Task(Of Integer)`, l’évaluation de la `Await` expression dans `DoSomethingAsync` génère un nombre entier.</span><span class="sxs-lookup"><span data-stu-id="ac516-240">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="ac516-241">Cela est illustré dans cette déclaration : `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="ac516-241">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="ac516-242">Le `startButton_Click` procédure est un exemple d’un `Async Sub` procédure.</span><span class="sxs-lookup"><span data-stu-id="ac516-242">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="ac516-243">Étant donné que `DoSomethingAsync` est un `Async` la tâche pour l’appel à une fonction, `DoSomethingAsync` doit être attendue, comme le montre l’instruction suivante : `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="ac516-243">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="ac516-244">Le `startButton_Click``Sub` procédure doit être définie avec la `Async` modificateur, car elle possède une `Await` expression.</span><span class="sxs-lookup"><span data-stu-id="ac516-244">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 <span data-ttu-id="ac516-245">[!code-vb[csAsyncMethod n °&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="ac516-245">[!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac516-246">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ac516-246">See Also</span></span>  
 <span data-ttu-id="ac516-247">[Sub (instruction)](sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-247">[Sub Statement](sub-statement.md) </span></span>  
<span data-ttu-id="ac516-248"> [Procédures Function](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-248"> [Function Procedures](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span></span>  
<span data-ttu-id="ac516-249"> [Liste de paramètres](parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-249"> [Parameter List](parameter-list.md) </span></span>  
<span data-ttu-id="ac516-250"> [Dim (instruction)](dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-250"> [Dim Statement](dim-statement.md) </span></span>  
<span data-ttu-id="ac516-251"> [Call, instruction](call-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-251"> [Call Statement](call-statement.md) </span></span>  
<span data-ttu-id="ac516-252"> [Of](of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-252"> [Of](of-clause.md) </span></span>  
<span data-ttu-id="ac516-253"> [Tableaux de paramètres](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-253"> [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span></span>  
<span data-ttu-id="ac516-254"> [Comment : utiliser une classe générique](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-254"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="ac516-255"> [Procédures de dépannage](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-255"> [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="ac516-256"> [Expressions lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="ac516-256"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="ac516-257"> [Expression de fonction](../../../visual-basic/language-reference/operators/function-expression.md)</span><span class="sxs-lookup"><span data-stu-id="ac516-257"> [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md)</span></span>

