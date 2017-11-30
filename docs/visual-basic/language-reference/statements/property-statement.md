---
title: Property Statement
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
helpviewer_keywords:
- Property statement [Visual Basic]
- default modifier
- property procedures [Visual Basic], Property statements
- Property keyword [Visual Basic]
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af4666ecb059f141480be2295055644537819293
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="property-statement"></a><span data-ttu-id="b5872-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="b5872-102">Property Statement</span></span>
<span data-ttu-id="b5872-103">Déclare le nom d’une propriété et les procédures de propriété utilisées pour stocker et récupérer la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5872-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b5872-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ] [ Iterator ]  
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
    [ <attributelist> ] [ accessmodifier ] Get  
        [ statements ]  
    End Get  
    [ <attributelist> ] [ accessmodifier ] Set ( ByVal value As returntype [, parameterlist ] )  
        [ statements ]  
    End Set  
End Property  
- or -  
[ <attributelist> ] [ Default ] [ accessmodifier ]   
[ propertymodifiers ] [ Shared ] [ Shadows ] [ ReadOnly | WriteOnly ]   
Property name ( [ parameterlist ] ) [ As returntype ] [ Implements implementslist ]  
```  
  
## <a name="parts"></a><span data-ttu-id="b5872-105">Composants</span><span class="sxs-lookup"><span data-stu-id="b5872-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="b5872-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-106">Optional.</span></span> <span data-ttu-id="b5872-107">Liste des attributs qui s’appliquent à cette propriété ou `Get` ou `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="b5872-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="b5872-108">Consultez [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="b5872-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-109">Optional.</span></span> <span data-ttu-id="b5872-110">Spécifie que cette propriété est la propriété par défaut pour la classe ou structure sur lequel elle est définie.</span><span class="sxs-lookup"><span data-stu-id="b5872-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="b5872-111">Propriétés par défaut doivent accepter des paramètres et peuvent être définies et récupérées sans spécifier le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="b5872-112">Si vous déclarez la propriété comme `Default`, vous ne pouvez pas utiliser `Private` sur la propriété ou sur un de ses procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="b5872-113">Facultatif sur le `Property` instruction et sur l’une de le `Get` et `Set` instructions.</span><span class="sxs-lookup"><span data-stu-id="b5872-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="b5872-114">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5872-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="b5872-115">Public</span><span class="sxs-lookup"><span data-stu-id="b5872-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="b5872-116">Protected</span><span class="sxs-lookup"><span data-stu-id="b5872-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="b5872-117">Friend</span><span class="sxs-lookup"><span data-stu-id="b5872-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="b5872-118">Private</span><span class="sxs-lookup"><span data-stu-id="b5872-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="b5872-119">Consultez [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="b5872-120">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-120">Optional.</span></span> <span data-ttu-id="b5872-121">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="b5872-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="b5872-122">Overloads</span><span class="sxs-lookup"><span data-stu-id="b5872-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="b5872-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="b5872-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="b5872-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="b5872-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="b5872-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="b5872-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="b5872-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="b5872-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="b5872-127">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-127">Optional.</span></span> <span data-ttu-id="b5872-128">Consultez [partagé](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="b5872-129">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-129">Optional.</span></span> <span data-ttu-id="b5872-130">Consultez [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="b5872-131">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-131">Optional.</span></span> <span data-ttu-id="b5872-132">Consultez [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="b5872-133">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-133">Optional.</span></span> <span data-ttu-id="b5872-134">Consultez [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="b5872-135">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-135">Optional.</span></span> <span data-ttu-id="b5872-136">Consultez [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="b5872-137">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b5872-137">Required.</span></span> <span data-ttu-id="b5872-138">Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-138">Name of the property.</span></span> <span data-ttu-id="b5872-139">Consultez [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="b5872-140">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-140">Optional.</span></span> <span data-ttu-id="b5872-141">Liste des noms de variables locales représentant les paramètres de cette propriété et les éventuels paramètres supplémentaires de la `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="b5872-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="b5872-142">Consultez [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="b5872-143">Obligatoire si `Option``Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="b5872-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="b5872-144">Type de données de la valeur retournée par cette propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="b5872-145">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-145">Optional.</span></span> <span data-ttu-id="b5872-146">Indique que cette propriété implémente une ou plusieurs propriétés, chacune étant définie dans une interface implémentée par la classe ou la structure conteneur de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="b5872-147">Consultez [implémente l’instruction](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="b5872-148">Obligatoire si `Implements` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="b5872-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="b5872-149">Liste de propriétés en cours d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="b5872-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="b5872-150">Chaque `implementedproperty` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="b5872-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="b5872-151">Élément</span><span class="sxs-lookup"><span data-stu-id="b5872-151">Part</span></span>|<span data-ttu-id="b5872-152">Description</span><span class="sxs-lookup"><span data-stu-id="b5872-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="b5872-153">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b5872-153">Required.</span></span> <span data-ttu-id="b5872-154">Nom d’une interface implémentée par cette propriété de classe ou la structure conteneur.</span><span class="sxs-lookup"><span data-stu-id="b5872-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="b5872-155">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="b5872-155">Required.</span></span> <span data-ttu-id="b5872-156">Nom par lequel la propriété est définie dans `interface`.</span><span class="sxs-lookup"><span data-stu-id="b5872-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="b5872-157">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-157">Optional.</span></span> <span data-ttu-id="b5872-158">Obligatoire si la propriété est marquée `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="b5872-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="b5872-159">Démarre un `Get` procédure de propriété qui est utilisée pour retourner la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="b5872-160">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-160">Optional.</span></span> <span data-ttu-id="b5872-161">Bloc d’instructions à exécuter dans le `Get` ou `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="b5872-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="b5872-162">Met fin à la `Get` procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="b5872-163">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="b5872-163">Optional.</span></span> <span data-ttu-id="b5872-164">Obligatoire si la propriété est marquée `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="b5872-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="b5872-165">Démarre un `Set` procédure de propriété qui est utilisé pour stocker la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="b5872-166">Met fin à la `Set` procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="b5872-167">Termine la définition de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5872-168">Remarques</span><span class="sxs-lookup"><span data-stu-id="b5872-168">Remarks</span></span>  
 <span data-ttu-id="b5872-169">La `Property` instruction introduit la déclaration d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="b5872-170">Une propriété peut avoir un `Get` procédure (lecture seule), un `Set` procédure (écriture seule), ou les deux (lecture-écriture).</span><span class="sxs-lookup"><span data-stu-id="b5872-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="b5872-171">Vous pouvez omettre le `Get` et `Set` procédure lors de l’utilisation d’une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="b5872-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="b5872-172">Pour plus d’informations, consultez [Propriétés implémentées automatiquement](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="b5872-173">Vous pouvez utiliser `Property` uniquement au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="b5872-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="b5872-174">Cela signifie que la *contexte de déclaration* pour une propriété doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="b5872-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="b5872-175">Pour plus d’informations, consultez [Contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="b5872-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="b5872-176">Par défaut, les propriétés utilisent un accès public.</span><span class="sxs-lookup"><span data-stu-id="b5872-176">By default, properties use public access.</span></span> <span data-ttu-id="b5872-177">Vous pouvez ajuster le niveau d’accès d’une propriété avec un modificateur d’accès sur le `Property` instruction et que vous pouvez éventuellement ajuster une de ses procédures de propriété à un niveau d’accès plus restrictif.</span><span class="sxs-lookup"><span data-stu-id="b5872-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="b5872-178">Visual Basic passe un paramètre à la `Set` procédure pendant les assignations de propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="b5872-179">Si vous ne fournissez pas un paramètre pour `Set`, l’environnement de développement intégré (IDE) utilise un paramètre implicite nommé `value`.</span><span class="sxs-lookup"><span data-stu-id="b5872-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="b5872-180">Ce paramètre conserve la valeur à affecter à la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="b5872-181">En général, stockez la valeur dans une variable locale privée et de la retourner chaque fois que le `Get` procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="b5872-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="b5872-182">Règles</span><span class="sxs-lookup"><span data-stu-id="b5872-182">Rules</span></span>  
  
-   <span data-ttu-id="b5872-183">**Niveaux d’accès mixtes.**</span><span class="sxs-lookup"><span data-stu-id="b5872-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="b5872-184">Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour un le `Get` ou `Set` procédure, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="b5872-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="b5872-185">Si vous faites cela, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="b5872-186">Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer le `Set` procédure `Private`, mais pas `Public`.</span><span class="sxs-lookup"><span data-stu-id="b5872-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="b5872-187">Si vous définissez un `ReadOnly` ou `WriteOnly` propriété, la procédure de propriété unique (`Get` ou `Set`, respectivement) représente la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="b5872-188">Vous ne pouvez pas déclarer un niveau d’accès différent pour cette procédure, parce que seront définis à deux niveaux d’accès pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="b5872-189">**Type de retour.**</span><span class="sxs-lookup"><span data-stu-id="b5872-189">**Return Type.**</span></span> <span data-ttu-id="b5872-190">La `Property` instruction peut déclarer le type de données de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="b5872-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="b5872-191">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, structure, classe ou d’interface.</span><span class="sxs-lookup"><span data-stu-id="b5872-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="b5872-192">Si vous ne spécifiez pas `returntype`, la propriété renvoie `Object`.</span><span class="sxs-lookup"><span data-stu-id="b5872-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="b5872-193">**Mise en œuvre.**</span><span class="sxs-lookup"><span data-stu-id="b5872-193">**Implementation.**</span></span> <span data-ttu-id="b5872-194">Si cette propriété utilise la `Implements` (mot clé), la classe ou la structure conteneur doit avoir un `Implements` instruction qui suit immédiatement sa `Class` ou `Structure` instruction.</span><span class="sxs-lookup"><span data-stu-id="b5872-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="b5872-195">Le `Implements` doit inclure chaque interface spécifiée dans `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="b5872-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="b5872-196">Toutefois, le nom par lequel une interface définit les `Property` (dans `definedname`) pas nécessairement être le même que le nom de la propriété (dans `name`).</span><span class="sxs-lookup"><span data-stu-id="b5872-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="b5872-197">Comportement</span><span class="sxs-lookup"><span data-stu-id="b5872-197">Behavior</span></span>  
  
-   <span data-ttu-id="b5872-198">**Retour d’une procédure de propriété.**</span><span class="sxs-lookup"><span data-stu-id="b5872-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="b5872-199">Lorsque le `Get` ou `Set` procédure retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui l’a appelée.</span><span class="sxs-lookup"><span data-stu-id="b5872-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="b5872-200">Le `Exit Property` et `Return` instructions provoquent la sortie immédiate d’une procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="b5872-201">Un nombre quelconque de `Exit Property` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Property` et `Return` instructions.</span><span class="sxs-lookup"><span data-stu-id="b5872-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="b5872-202">**Valeur de retour.**</span><span class="sxs-lookup"><span data-stu-id="b5872-202">**Return Value.**</span></span> <span data-ttu-id="b5872-203">Pour retourner une valeur d’un `Get` procédure, vous pouvez affecter la valeur au nom de propriété ou l’inclure dans un `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="b5872-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="b5872-204">L’exemple suivant affecte la valeur de retour au nom de propriété `quoteForTheDay` , puis utilise la `Exit Property` instruction à retourner.</span><span class="sxs-lookup"><span data-stu-id="b5872-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]  
  
     <span data-ttu-id="b5872-205">Si vous utilisez `Exit Property` sans lui assigner une valeur à `name`, le `Get` procédure retourne la valeur par défaut pour le type de données de la propriété.</span><span class="sxs-lookup"><span data-stu-id="b5872-205">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="b5872-206">Le `Return` instruction en même temps affecte le `Get` procédure retourner de valeur et termine la procédure.</span><span class="sxs-lookup"><span data-stu-id="b5872-206">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="b5872-207">L’exemple suivant illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="b5872-207">The following example shows this.</span></span>  
  
     [!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]  
  
     [!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="b5872-208">Exemple</span><span class="sxs-lookup"><span data-stu-id="b5872-208">Example</span></span>  
 <span data-ttu-id="b5872-209">L’exemple suivant déclare une propriété dans une classe.</span><span class="sxs-lookup"><span data-stu-id="b5872-209">The following example declares a property in a class.</span></span>  
  
 [!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b5872-210">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5872-210">See Also</span></span>  
 [<span data-ttu-id="b5872-211">Propriétés implémentées automatiquement</span><span class="sxs-lookup"><span data-stu-id="b5872-211">Auto-Implemented Properties</span></span>](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md)  
 [<span data-ttu-id="b5872-212">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="b5872-212">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="b5872-213">Get (instruction)</span><span class="sxs-lookup"><span data-stu-id="b5872-213">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)  
 [<span data-ttu-id="b5872-214">Set (instruction)</span><span class="sxs-lookup"><span data-stu-id="b5872-214">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)  
 [<span data-ttu-id="b5872-215">Liste de paramètres</span><span class="sxs-lookup"><span data-stu-id="b5872-215">Parameter List</span></span>](../../../visual-basic/language-reference/statements/parameter-list.md)  
 [<span data-ttu-id="b5872-216">Default</span><span class="sxs-lookup"><span data-stu-id="b5872-216">Default</span></span>](../../../visual-basic/language-reference/modifiers/default.md)
