---
title: Enum, instruction (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Enum
helpviewer_keywords:
- enumerated constants [Visual Basic]
- Enum statement [Visual Basic]
- Private keyword [Visual Basic], Enum statements
- Public keyword [Visual Basic], in Enum statement
- variables [Visual Basic], enumeration
- constants [Visual Basic], enumerated
ms.assetid: a45e51f1-65ff-48e1-bf32-79130f137377
caps.latest.revision: "44"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a8244318e0be8e50f3384b56cf63e59182b6cda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="enum-statement-visual-basic"></a><span data-ttu-id="2cac4-102">Enum, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cac4-102">Enum Statement (Visual Basic)</span></span>
<span data-ttu-id="2cac4-103">Déclare une énumération et définit les valeurs de ses membres.</span><span class="sxs-lookup"><span data-stu-id="2cac4-103">Declares an enumeration and defines the values of its members.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cac4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cac4-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ]  [ Shadows ]   
Enum enumerationname [ As datatype ]   
   memberlist  
End Enum  
```  
  
## <a name="parts"></a><span data-ttu-id="2cac4-105">Composants</span><span class="sxs-lookup"><span data-stu-id="2cac4-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="2cac4-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="2cac4-106">Optional.</span></span> <span data-ttu-id="2cac4-107">Liste des attributs qui s’appliquent à cette énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-107">List of attributes that apply to this enumeration.</span></span> <span data-ttu-id="2cac4-108">Vous devez placer le [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md) figurant entre crochets («`<`« et »`>`»).</span><span class="sxs-lookup"><span data-stu-id="2cac4-108">You must enclose the [attribute list](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
     <span data-ttu-id="2cac4-109">Le <xref:System.FlagsAttribute> attribut indique que la valeur d’une instance de l’énumération peut inclure plusieurs membres de l’énumération, et que chaque membre représente un champ de bits dans la valeur d’énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-109">The <xref:System.FlagsAttribute> attribute indicates that the value of an instance of the enumeration can include multiple enumeration members, and that each member represents a bit field in the enumeration value.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="2cac4-110">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="2cac4-110">Optional.</span></span> <span data-ttu-id="2cac4-111">Spécifie le code pouvant accéder à cette énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-111">Specifies what code can access this enumeration.</span></span> <span data-ttu-id="2cac4-112">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="2cac4-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="2cac4-113">Public</span><span class="sxs-lookup"><span data-stu-id="2cac4-113">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="2cac4-114">Protected</span><span class="sxs-lookup"><span data-stu-id="2cac4-114">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="2cac4-115">Friend</span><span class="sxs-lookup"><span data-stu-id="2cac4-115">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="2cac4-116">Private</span><span class="sxs-lookup"><span data-stu-id="2cac4-116">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
     <span data-ttu-id="2cac4-117">Vous pouvez spécifier `Protected``Friend` pour autoriser l’accès à partir du code au sein classe de l’énumération, une classe dérivée ou le même assembly.</span><span class="sxs-lookup"><span data-stu-id="2cac4-117">You can specify `Protected``Friend` to allow access from code within the enumeration's class, a derived class, or the same assembly.</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="2cac4-118">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="2cac4-118">Optional.</span></span> <span data-ttu-id="2cac4-119">Spécifie que cette énumération redéclare et masque un élément de programmation portant le même nom ou un ensemble d’éléments surchargés, dans une classe de base.</span><span class="sxs-lookup"><span data-stu-id="2cac4-119">Specifies that this enumeration redeclares and hides an identically named programming element, or set of overloaded elements, in a base class.</span></span> <span data-ttu-id="2cac4-120">Vous pouvez spécifier [ombres](../../../visual-basic/language-reference/modifiers/shadows.md) uniquement sur l’énumération elle-même, et non sur un de ses membres.</span><span class="sxs-lookup"><span data-stu-id="2cac4-120">You can specify [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md) only on the enumeration itself, not on any of its members.</span></span>  
  
-   `enumerationname`  
  
     <span data-ttu-id="2cac4-121">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2cac4-121">Required.</span></span> <span data-ttu-id="2cac4-122">Nom de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-122">Name of the enumeration.</span></span> <span data-ttu-id="2cac4-123">Pour plus d’informations sur les noms valides, consultez [noms d’élément déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="2cac4-123">For information on valid names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `datatype`  
  
     <span data-ttu-id="2cac4-124">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="2cac4-124">Optional.</span></span> <span data-ttu-id="2cac4-125">Type de données de l’énumération et tous ses membres.</span><span class="sxs-lookup"><span data-stu-id="2cac4-125">Data type of the enumeration and all its members.</span></span>  
  
-   `memberlist`  
  
     <span data-ttu-id="2cac4-126">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2cac4-126">Required.</span></span> <span data-ttu-id="2cac4-127">Liste des constantes membres déclarées dans cette instruction.</span><span class="sxs-lookup"><span data-stu-id="2cac4-127">List of member constants being declared in this statement.</span></span> <span data-ttu-id="2cac4-128">Plusieurs membres apparaissent sur les lignes de code source individuel.</span><span class="sxs-lookup"><span data-stu-id="2cac4-128">Multiple members appear on individual source code lines.</span></span>  
  
     <span data-ttu-id="2cac4-129">Chaque `member` possède la syntaxe et les éléments suivants :`[<attribute list>] member name [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="2cac4-129">Each `member` has the following syntax and parts: `[<attribute list>] member name [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="2cac4-130">Élément</span><span class="sxs-lookup"><span data-stu-id="2cac4-130">Part</span></span>|<span data-ttu-id="2cac4-131">Description</span><span class="sxs-lookup"><span data-stu-id="2cac4-131">Description</span></span>|  
    |---|---|  
    |`membername`|<span data-ttu-id="2cac4-132">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="2cac4-132">Required.</span></span> <span data-ttu-id="2cac4-133">Nom de ce membre.</span><span class="sxs-lookup"><span data-stu-id="2cac4-133">Name of this member.</span></span>|  
    |`initializer`|<span data-ttu-id="2cac4-134">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="2cac4-134">Optional.</span></span> <span data-ttu-id="2cac4-135">Expression qui est évaluée au moment de la compilation et assignée à ce membre.</span><span class="sxs-lookup"><span data-stu-id="2cac4-135">Expression that is evaluated at compile time and assigned to this member.</span></span>|  
  
-   <span data-ttu-id="2cac4-136">`End` `Enum`</span><span class="sxs-lookup"><span data-stu-id="2cac4-136">`End` `Enum`</span></span>  
  
     <span data-ttu-id="2cac4-137">Met fin au bloc `Enum`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-137">Terminates the `Enum` block.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cac4-138">Remarques</span><span class="sxs-lookup"><span data-stu-id="2cac4-138">Remarks</span></span>  
 <span data-ttu-id="2cac4-139">Si vous avez un ensemble de valeurs qui ne changent pas logiquement liées entre elles, vous pouvez les définir ensemble dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-139">If you have a set of unchanging values that are logically related to each other, you can define them together in an enumeration.</span></span> <span data-ttu-id="2cac4-140">Cela fournit des noms explicites pour l’énumération et ses membres, qui sont plus faciles à mémoriser que leurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="2cac4-140">This provides meaningful names for the enumeration and its members, which are easier to remember than their values.</span></span> <span data-ttu-id="2cac4-141">Vous pouvez ensuite utiliser les membres d’énumération dans de nombreux endroits dans votre code.</span><span class="sxs-lookup"><span data-stu-id="2cac4-141">You can then use the enumeration members in many places in your code.</span></span>  
  
 <span data-ttu-id="2cac4-142">Les avantages de l’utilisation des énumérations sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="2cac4-142">The benefits of using enumerations include the following:</span></span>  
  
-   <span data-ttu-id="2cac4-143">Réduit les erreurs provoquées par transposer ou numéros d’erreur de frappe.</span><span class="sxs-lookup"><span data-stu-id="2cac4-143">Reduces errors caused by transposing or mistyping numbers.</span></span>  
  
-   <span data-ttu-id="2cac4-144">Rend faciles à modifier les valeurs dans le futur.</span><span class="sxs-lookup"><span data-stu-id="2cac4-144">Makes it easy to change values in the future.</span></span>  
  
-   <span data-ttu-id="2cac4-145">Rend le code plus facile à lire, ce qui signifie qu’il est peu probable que les erreurs seront introduites.</span><span class="sxs-lookup"><span data-stu-id="2cac4-145">Makes code easier to read, which means it is less likely that errors will be introduced.</span></span>  
  
-   <span data-ttu-id="2cac4-146">Garantit la compatibilité ascendante.</span><span class="sxs-lookup"><span data-stu-id="2cac4-146">Ensures forward compatibility.</span></span> <span data-ttu-id="2cac4-147">Si vous utilisez des énumérations, votre code est moins susceptible d’échouer si à l’avenir une personne modifie les valeurs correspondant aux noms de membre.</span><span class="sxs-lookup"><span data-stu-id="2cac4-147">If you use enumerations, your code is less likely to fail if in the future someone changes the values corresponding to the member names.</span></span>  
  
 <span data-ttu-id="2cac4-148">Une énumération a un nom, un type de données sous-jacent et un jeu de membres.</span><span class="sxs-lookup"><span data-stu-id="2cac4-148">An enumeration has a name, an underlying data type, and a set of members.</span></span> <span data-ttu-id="2cac4-149">Chaque membre représente une constante.</span><span class="sxs-lookup"><span data-stu-id="2cac4-149">Each member represents a constant.</span></span>  
  
 <span data-ttu-id="2cac4-150">Une énumération déclarée au niveau de la classe, structure, un module ou niveau de l’interface, en dehors de toute procédure, est une *énumération membre*.</span><span class="sxs-lookup"><span data-stu-id="2cac4-150">An enumeration declared at class, structure, module, or interface level, outside any procedure, is a *member enumeration*.</span></span> <span data-ttu-id="2cac4-151">Il est membre de la classe, une structure, un module ou une interface qui le déclare.</span><span class="sxs-lookup"><span data-stu-id="2cac4-151">It is a member of the class, structure, module, or interface that declares it.</span></span>  
  
 <span data-ttu-id="2cac4-152">Les énumérations de membres sont accessibles à partir de n’importe où au sein de leur classe, une structure, un module ou une interface.</span><span class="sxs-lookup"><span data-stu-id="2cac4-152">Member enumerations can be accessed from anywhere within their class, structure, module, or interface.</span></span> <span data-ttu-id="2cac4-153">Code en dehors d’une classe, structure ou module doit qualifier le nom d’une énumération de membre avec le nom de cette classe, une structure ou un module.</span><span class="sxs-lookup"><span data-stu-id="2cac4-153">Code outside a class, structure, or module must qualify a member enumeration's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="2cac4-154">Vous pouvez éviter la nécessité d’utiliser des noms qualifiés complets en ajoutant un [importations](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) instruction dans le fichier source.</span><span class="sxs-lookup"><span data-stu-id="2cac4-154">You can avoid the need to use fully qualified names by adding an [Imports](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) statement to the source file.</span></span>  
  
 <span data-ttu-id="2cac4-155">Une énumération déclarée au niveau de l’espace de noms, en dehors de toute classe, une structure, un module ou une interface, est un membre de l’espace de noms dans lequel elle apparaît.</span><span class="sxs-lookup"><span data-stu-id="2cac4-155">An enumeration declared at namespace level, outside any class, structure, module, or interface, is a member of the namespace in which it appears.</span></span>  
  
 <span data-ttu-id="2cac4-156">Le *contexte de déclaration* pour une énumération doit être un fichier source, espace de noms, classe, structure, module ou interface et qu’il ne peut pas être une procédure.</span><span class="sxs-lookup"><span data-stu-id="2cac4-156">The *declaration context* for an enumeration must be a source file, namespace, class, structure, module, or interface, and cannot be a procedure.</span></span> <span data-ttu-id="2cac4-157">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2cac4-157">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="2cac4-158">Vous pouvez appliquer des attributs à une énumération dans son ensemble, mais pas à ses membres individuellement.</span><span class="sxs-lookup"><span data-stu-id="2cac4-158">You can apply attributes to an enumeration as a whole, but not to its members individually.</span></span> <span data-ttu-id="2cac4-159">Un attribut fournit des informations aux métadonnées de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="2cac4-159">An attribute contributes information to the assembly's metadata.</span></span>  
  
## <a name="data-type"></a><span data-ttu-id="2cac4-160">Type de données</span><span class="sxs-lookup"><span data-stu-id="2cac4-160">Data Type</span></span>  
 <span data-ttu-id="2cac4-161">La `Enum` instruction peut déclarer le type de données d’une énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-161">The `Enum` statement can declare the data type of an enumeration.</span></span> <span data-ttu-id="2cac4-162">Chaque membre prend le type de données de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-162">Each member takes the enumeration's data type.</span></span> <span data-ttu-id="2cac4-163">Vous pouvez spécifier `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, ou `UShort`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-163">You can specify `Byte`, `Integer`, `Long`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort`.</span></span>  
  
 <span data-ttu-id="2cac4-164">Si vous ne spécifiez pas `datatype` pour l’énumération, chaque membre prend le type de données de son `initializer`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-164">If you do not specify `datatype` for the enumeration, each member takes the data type of its `initializer`.</span></span> <span data-ttu-id="2cac4-165">Si vous spécifiez à la fois `datatype` et `initializer`, type de données de `initializer` doit être convertible en `datatype`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-165">If you specify both `datatype` and `initializer`, the data type of `initializer` must be convertible to `datatype`.</span></span> <span data-ttu-id="2cac4-166">Si ni `datatype` ni `initializer` est présent, le type de données par défaut, `Integer`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-166">If neither `datatype` nor `initializer` is present, the data type defaults to `Integer`.</span></span>  
  
## <a name="initializing-members"></a><span data-ttu-id="2cac4-167">L’initialisation des membres</span><span class="sxs-lookup"><span data-stu-id="2cac4-167">Initializing Members</span></span>  
 <span data-ttu-id="2cac4-168">Le `Enum` instruction peut initialiser le contenu de membres sélectionnés dans `memberlist`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-168">The `Enum` statement can initialize the contents of selected members in `memberlist`.</span></span> <span data-ttu-id="2cac4-169">Vous utilisez `initializer` pour fournir une expression à affecter au membre.</span><span class="sxs-lookup"><span data-stu-id="2cac4-169">You use `initializer` to supply an expression to be assigned to the member.</span></span>  
  
 <span data-ttu-id="2cac4-170">Si vous ne spécifiez pas `initializer` pour un membre, Visual Basic l’initialise soit à zéro (s’il s’agit de la première `member` dans `memberlist`), ou une valeur supérieure d’une unité à celle de qui précède immédiatement `member`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-170">If you do not specify `initializer` for a member, Visual Basic initializes it either to zero (if it is the first `member` in `memberlist`), or to a value greater by one than that of the immediately preceding `member`.</span></span>  
  
 <span data-ttu-id="2cac4-171">L’expression fournie dans chaque `initializer` peut être n’importe quelle combinaison de littéraux, d’autres constantes qui sont déjà définies et de membres de l’énumération qui sont déjà définis, y compris un membre précédent de cette énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-171">The expression supplied in each `initializer` can be any combination of literals, other constants that are already defined, and enumeration members that are already defined, including a previous member of this enumeration.</span></span> <span data-ttu-id="2cac4-172">Vous pouvez utiliser des opérateurs arithmétiques et logiques pour combiner ces éléments.</span><span class="sxs-lookup"><span data-stu-id="2cac4-172">You can use arithmetic and logical operators to combine such elements.</span></span>  
  
 <span data-ttu-id="2cac4-173">Vous ne pouvez pas utiliser des variables ou des fonctions dans `initializer`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-173">You cannot use variables or functions in `initializer`.</span></span> <span data-ttu-id="2cac4-174">Toutefois, vous pouvez utiliser des mots clés de conversion tels que `CByte` et `CShort`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-174">However, you can use conversion keywords such as `CByte` and `CShort`.</span></span> <span data-ttu-id="2cac4-175">Vous pouvez également utiliser `AscW` si vous l’appelez avec une constante `String` ou `Char` argument, étant donné que qui peut être évaluée au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="2cac4-175">You can also use `AscW` if you call it with a constant `String` or `Char` argument, since that can be evaluated at compile time.</span></span>  
  
 <span data-ttu-id="2cac4-176">Les énumérations ne peut pas avoir de valeurs à virgule flottante.</span><span class="sxs-lookup"><span data-stu-id="2cac4-176">Enumerations cannot have floating-point values.</span></span> <span data-ttu-id="2cac4-177">Si un membre est assigné une valeur à virgule flottante et `Option Strict` a la valeur on, une erreur de compilation se produit.</span><span class="sxs-lookup"><span data-stu-id="2cac4-177">If a member is assigned a floating-point value and `Option Strict` is set to on, a compiler error occurs.</span></span> <span data-ttu-id="2cac4-178">Si `Option Strict` est désactivée, la valeur est automatiquement convertie en la `Enum` type.</span><span class="sxs-lookup"><span data-stu-id="2cac4-178">If `Option Strict` is off, the value is automatically converted to the `Enum` type.</span></span>  
  
 <span data-ttu-id="2cac4-179">Si la valeur d’un membre dépasse la plage autorisée pour le type de données sous-jacente, ou si vous initialisez un membre à la valeur maximale autorisée par le type de données sous-jacent, le compilateur signale une erreur.</span><span class="sxs-lookup"><span data-stu-id="2cac4-179">If the value of a member exceeds the allowable range for the underlying data type, or if you initialize any member to the maximum value allowed by the underlying data type, the compiler reports an error.</span></span>  
  
## <a name="modifiers"></a><span data-ttu-id="2cac4-180">Modificateurs</span><span class="sxs-lookup"><span data-stu-id="2cac4-180">Modifiers</span></span>  
 <span data-ttu-id="2cac4-181">Classe, structure, module et interface membres énumérations par défaut d’un accès public.</span><span class="sxs-lookup"><span data-stu-id="2cac4-181">Class, structure, module, and interface member enumerations default to public access.</span></span> <span data-ttu-id="2cac4-182">Vous pouvez ajuster leurs niveaux d’accès avec les modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="2cac4-182">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="2cac4-183">Namespace membre énumérations par défaut d’un accès ami.</span><span class="sxs-lookup"><span data-stu-id="2cac4-183">Namespace member enumerations default to friend access.</span></span> <span data-ttu-id="2cac4-184">Vous pouvez ajuster leurs niveaux d’accès public, mais pas pour privé ou protégé.</span><span class="sxs-lookup"><span data-stu-id="2cac4-184">You can adjust their access levels to public, but not to private or protected.</span></span> <span data-ttu-id="2cac4-185">Pour plus d’informations, consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2cac4-185">For more information, see [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="2cac4-186">Tous les membres d’énumération ont un accès public, et vous ne pouvez pas utiliser les modificateurs d’accès sur ces derniers.</span><span class="sxs-lookup"><span data-stu-id="2cac4-186">All enumeration members have public access, and you cannot use any access modifiers on them.</span></span> <span data-ttu-id="2cac4-187">Toutefois, si l’énumération elle-même a un niveau d’accès plus restreint, le niveau d’accès de l’énumération spécifiée est prioritaire.</span><span class="sxs-lookup"><span data-stu-id="2cac4-187">However, if the enumeration itself has a more restricted access level, the specified enumeration access level takes precedence.</span></span>  
  
 <span data-ttu-id="2cac4-188">Par défaut, toutes les énumérations sont des types et leurs champs sont des constantes.</span><span class="sxs-lookup"><span data-stu-id="2cac4-188">By default, all enumerations are types and their fields are constants.</span></span> <span data-ttu-id="2cac4-189">Par conséquent la `Shared`, `Static`, et `ReadOnly` mots clés ne peut pas être utilisés pour déclarer une énumération ou ses membres.</span><span class="sxs-lookup"><span data-stu-id="2cac4-189">Therefore the `Shared`, `Static`, and `ReadOnly` keywords cannot be used when declaring an enumeration or its members.</span></span>  
  
## <a name="assigning-multiple-values"></a><span data-ttu-id="2cac4-190">Affectation de valeurs multiples</span><span class="sxs-lookup"><span data-stu-id="2cac4-190">Assigning Multiple Values</span></span>  
 <span data-ttu-id="2cac4-191">Énumérations représentent généralement les valeurs s’excluent mutuellement.</span><span class="sxs-lookup"><span data-stu-id="2cac4-191">Enumerations typically represent mutually exclusive values.</span></span> <span data-ttu-id="2cac4-192">En incluant la <xref:System.FlagsAttribute> d’attribut dans le `Enum` déclaration, vous pouvez affecter à la place plusieurs valeurs à une instance de l’énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-192">By including the <xref:System.FlagsAttribute> attribute in the `Enum` declaration, you can instead assign multiple values to an instance of the enumeration.</span></span> <span data-ttu-id="2cac4-193">Le <xref:System.FlagsAttribute> attribut spécifie que l’énumération être traitée comme un champ de bits, c'est-à-dire un ensemble d’indicateurs.</span><span class="sxs-lookup"><span data-stu-id="2cac4-193">The <xref:System.FlagsAttribute> attribute specifies that the enumeration be treated as a bit field, that is, a set of flags.</span></span> <span data-ttu-id="2cac4-194">Ils sont appelés *au niveau du bit* énumérations.</span><span class="sxs-lookup"><span data-stu-id="2cac4-194">These are called *bitwise* enumerations.</span></span>  
  
 <span data-ttu-id="2cac4-195">Lorsque vous déclarez une énumération à l’aide de la <xref:System.FlagsAttribute> attribut, nous vous recommandons d’utiliser puissances de 2, qui est, 1, 2, 4, 8, 16 et ainsi de suite, pour les valeurs.</span><span class="sxs-lookup"><span data-stu-id="2cac4-195">When you declare an enumeration by using the <xref:System.FlagsAttribute> attribute, we recommend that you use powers of 2, that is, 1, 2, 4, 8, 16, and so on, for the values.</span></span> <span data-ttu-id="2cac4-196">Nous vous recommandons également de « None » soit le nom d’un membre dont la valeur est 0.</span><span class="sxs-lookup"><span data-stu-id="2cac4-196">We also recommend that "None" be the name of a member whose value is 0.</span></span> <span data-ttu-id="2cac4-197">Pour des instructions supplémentaires, consultez <xref:System.FlagsAttribute> et <xref:System.Enum>.</span><span class="sxs-lookup"><span data-stu-id="2cac4-197">For additional guidelines, see <xref:System.FlagsAttribute> and <xref:System.Enum>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cac4-198">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cac4-198">Example</span></span>  
 <span data-ttu-id="2cac4-199">L’exemple suivant montre comment utiliser la `Enum` instruction.</span><span class="sxs-lookup"><span data-stu-id="2cac4-199">The following example shows how to use the `Enum` statement.</span></span> <span data-ttu-id="2cac4-200">Notez que le membre est appelé `EggSizeEnum.Medium`et non comme `Medium`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-200">Note that the member is referred to as `EggSizeEnum.Medium`, and not as `Medium`.</span></span>  
  
 [!code-vb[VbEnumsTask#41](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="2cac4-201">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cac4-201">Example</span></span>  
 <span data-ttu-id="2cac4-202">La méthode dans l’exemple suivant est en dehors de la `Egg` classe.</span><span class="sxs-lookup"><span data-stu-id="2cac4-202">The method in the following example is outside the `Egg` class.</span></span> <span data-ttu-id="2cac4-203">Par conséquent, `EggSizeEnum` est qualifié en tant que `Egg.EggSizeEnum`.</span><span class="sxs-lookup"><span data-stu-id="2cac4-203">Therefore, `EggSizeEnum` is fully qualified as `Egg.EggSizeEnum`.</span></span>  
  
 [!code-vb[VbEnumsTask#42](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_2.vb)]  
  
## <a name="example"></a><span data-ttu-id="2cac4-204">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cac4-204">Example</span></span>  
 <span data-ttu-id="2cac4-205">L’exemple suivant utilise la `Enum` instruction afin de définir un ensemble des valeurs des constantes nommées.</span><span class="sxs-lookup"><span data-stu-id="2cac4-205">The following example uses the `Enum` statement to define a related set of named constant values.</span></span> <span data-ttu-id="2cac4-206">Dans ce cas, les valeurs sont des couleurs, que vous pouvez choisir de concevoir les formulaires de saisie de données pour une base de données.</span><span class="sxs-lookup"><span data-stu-id="2cac4-206">In this case, the values are colors you might choose to design data entry forms for a database.</span></span>  
  
 [!code-vb[VbEnumsTask#30](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="2cac4-207">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cac4-207">Example</span></span>  
 <span data-ttu-id="2cac4-208">L’exemple suivant montre les valeurs qui comportent des nombres positifs et négatifs.</span><span class="sxs-lookup"><span data-stu-id="2cac4-208">The following example shows values that include both positive and negative numbers.</span></span>  
  
 [!code-vb[VbEnumsTask#31](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="2cac4-209">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cac4-209">Example</span></span>  
 <span data-ttu-id="2cac4-210">Dans l’exemple suivant, un `As` clause est utilisée pour spécifier le `datatype` d’une énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-210">In the following example, an `As` clause is used to specify the `datatype` of an enumeration.</span></span>  
  
 [!code-vb[VbEnumsTask#6](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_5.vb)]  
  
## <a name="example"></a><span data-ttu-id="2cac4-211">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cac4-211">Example</span></span>  
 <span data-ttu-id="2cac4-212">L’exemple suivant montre comment utiliser une énumération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="2cac4-212">The following example shows how to use a bitwise enumeration.</span></span> <span data-ttu-id="2cac4-213">Plusieurs valeurs peuvent être attribués à une instance d’une énumération au niveau du bit.</span><span class="sxs-lookup"><span data-stu-id="2cac4-213">Multiple values can be assigned to an instance of a bitwise enumeration.</span></span> <span data-ttu-id="2cac4-214">Le `Enum` déclaration inclut le <xref:System.FlagsAttribute> attribut, ce qui indique que l’énumération peut être traitée comme un ensemble d’indicateurs.</span><span class="sxs-lookup"><span data-stu-id="2cac4-214">The `Enum` declaration includes the <xref:System.FlagsAttribute> attribute, which indicates that the enumeration can be treated as a set of flags.</span></span>  
  
 [!code-vb[VbEnumsTask#61](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_6.vb)]  
  
## <a name="example"></a><span data-ttu-id="2cac4-215">Exemple</span><span class="sxs-lookup"><span data-stu-id="2cac4-215">Example</span></span>  
 <span data-ttu-id="2cac4-216">L’exemple suivant effectue une itération dans une énumération.</span><span class="sxs-lookup"><span data-stu-id="2cac4-216">The following example iterates through an enumeration.</span></span> <span data-ttu-id="2cac4-217">Elle utilise le <xref:System.Enum.GetNames%2A> méthode pour récupérer un tableau des noms de membres de l’énumération, et <xref:System.Enum.GetValues%2A> pour récupérer un tableau de valeurs de membre.</span><span class="sxs-lookup"><span data-stu-id="2cac4-217">It uses the <xref:System.Enum.GetNames%2A> method to retrieve an array of member names from the enumeration, and <xref:System.Enum.GetValues%2A> to retrieve an array of member values.</span></span>  
  
 [!code-vb[VbEnumsTask#51](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enum-statement_7.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2cac4-218">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2cac4-218">See Also</span></span>  
 <xref:System.Enum>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 [<span data-ttu-id="2cac4-219">Const (instruction)</span><span class="sxs-lookup"><span data-stu-id="2cac4-219">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
 [<span data-ttu-id="2cac4-220">Dim (instruction)</span><span class="sxs-lookup"><span data-stu-id="2cac4-220">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [<span data-ttu-id="2cac4-221">Conversions implicites et explicites</span><span class="sxs-lookup"><span data-stu-id="2cac4-221">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="2cac4-222">Fonctions de conversion de types</span><span class="sxs-lookup"><span data-stu-id="2cac4-222">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="2cac4-223">Constantes et énumérations</span><span class="sxs-lookup"><span data-stu-id="2cac4-223">Constants and Enumerations</span></span>](../../../visual-basic/language-reference/constants-and-enumerations.md)
