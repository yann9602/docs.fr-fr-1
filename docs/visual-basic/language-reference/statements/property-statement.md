---
title: "Déclaration de propriété | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.PropertySet
- vb.Property
- vb.PropertyGet
dev_langs:
- VB
helpviewer_keywords:
- Property statement
- default modifier
- property procedures, Property statements
- Property keyword
ms.assetid: 3155edaf-8ebd-45c6-9cef-11d5d2dc8d38
caps.latest.revision: 41
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: dbd779b4b6a1dd167e8581066b0fbe034cd2d8f2
ms.contentlocale: fr-fr
ms.lasthandoff: 05/23/2017

---
# <a name="property-statement"></a><span data-ttu-id="ab2dc-102">Property Statement</span><span class="sxs-lookup"><span data-stu-id="ab2dc-102">Property Statement</span></span>
<span data-ttu-id="ab2dc-103">Déclare le nom d'une propriété, ainsi que les procédures de propriété utilisées pour stocker et récupérer la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-103">Declares the name of a property, and the property procedures used to store and retrieve the value of the property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab2dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab2dc-104">Syntax</span></span>  
  
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
  
## <a name="parts"></a><span data-ttu-id="ab2dc-105">Composants</span><span class="sxs-lookup"><span data-stu-id="ab2dc-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="ab2dc-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-106">Optional.</span></span> <span data-ttu-id="ab2dc-107">Liste des attributs qui s’appliquent à cette propriété ou `Get` ou `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-107">List of attributes that apply to this property or `Get` or `Set` procedure.</span></span> <span data-ttu-id="ab2dc-108">Consultez la page [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-108">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `Default`  
  
     <span data-ttu-id="ab2dc-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-109">Optional.</span></span> <span data-ttu-id="ab2dc-110">Spécifie que cette propriété est la propriété par défaut pour la classe ou la structure sur laquelle elle est définie.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-110">Specifies that this property is the default property for the class or structure on which it is defined.</span></span> <span data-ttu-id="ab2dc-111">Propriétés par défaut doivent accepter des paramètres et peuvent être définies et récupérées sans spécifier le nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-111">Default properties must accept parameters and can be set and retrieved without specifying the property name.</span></span> <span data-ttu-id="ab2dc-112">Si vous déclarez la propriété comme `Default`, vous ne pouvez pas utiliser `Private` sur la propriété ou sur une de ses procédures de propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-112">If you declare the property as `Default`, you cannot use `Private` on the property or on either of its property procedures.</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="ab2dc-113">Facultatif sur le `Property` instruction et sur l’une de la `Get` et `Set` instructions.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-113">Optional on the `Property` statement and on at most one of the `Get` and `Set` statements.</span></span> <span data-ttu-id="ab2dc-114">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab2dc-114">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="ab2dc-115">Public</span><span class="sxs-lookup"><span data-stu-id="ab2dc-115">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="ab2dc-116">Protected</span><span class="sxs-lookup"><span data-stu-id="ab2dc-116">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="ab2dc-117">Friend</span><span class="sxs-lookup"><span data-stu-id="ab2dc-117">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="ab2dc-118">Private</span><span class="sxs-lookup"><span data-stu-id="ab2dc-118">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="ab2dc-119">Consultez la page [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-119">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `propertymodifiers`  
  
     <span data-ttu-id="ab2dc-120">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-120">Optional.</span></span> <span data-ttu-id="ab2dc-121">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ab2dc-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="ab2dc-122">Surcharges</span><span class="sxs-lookup"><span data-stu-id="ab2dc-122">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="ab2dc-123">Overrides</span><span class="sxs-lookup"><span data-stu-id="ab2dc-123">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="ab2dc-124">Overridable</span><span class="sxs-lookup"><span data-stu-id="ab2dc-124">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="ab2dc-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="ab2dc-125">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="ab2dc-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="ab2dc-126">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="ab2dc-127">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-127">Optional.</span></span> <span data-ttu-id="ab2dc-128">Consultez la page [partagé](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-128">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="ab2dc-129">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-129">Optional.</span></span> <span data-ttu-id="ab2dc-130">Consultez la page [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-130">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="ab2dc-131">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-131">Optional.</span></span> <span data-ttu-id="ab2dc-132">Consultez la page [en lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-132">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WriteOnly`  
  
     <span data-ttu-id="ab2dc-133">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-133">Optional.</span></span> <span data-ttu-id="ab2dc-134">Consultez la page [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-134">See [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="ab2dc-135">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-135">Optional.</span></span> <span data-ttu-id="ab2dc-136">Consultez la page [itérateur](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-136">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="ab2dc-137">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-137">Required.</span></span> <span data-ttu-id="ab2dc-138">Nom de la propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-138">Name of the property.</span></span> <span data-ttu-id="ab2dc-139">Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-139">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="ab2dc-140">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-140">Optional.</span></span> <span data-ttu-id="ab2dc-141">Liste des noms de variables locales représentant les paramètres de cette propriété et les éventuels paramètres supplémentaires de la `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-141">List of local variable names representing the parameters of this property, and possible additional parameters of the `Set` procedure.</span></span> <span data-ttu-id="ab2dc-142">Consultez la page [liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-142">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="ab2dc-143">Requis si `Option``Strict` est `On`.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-143">Required if `Option``Strict` is `On`.</span></span> <span data-ttu-id="ab2dc-144">Type de données de la valeur retournée par cette propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-144">Data type of the value returned by this property.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="ab2dc-145">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-145">Optional.</span></span> <span data-ttu-id="ab2dc-146">Indique que cette propriété implémente une ou plusieurs propriétés, chacune étant définie dans une interface implémentée par la classe ou la structure conteneur de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-146">Indicates that this property implements one or more properties, each one defined in an interface implemented by this property's containing class or structure.</span></span> <span data-ttu-id="ab2dc-147">Consultez la page [implémente l’instruction](../../../visual-basic/language-reference/statements/implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-147">See [Implements Statement](../../../visual-basic/language-reference/statements/implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="ab2dc-148">Obligatoire si `Implements` est utilisé.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-148">Required if `Implements` is supplied.</span></span> <span data-ttu-id="ab2dc-149">Liste des propriétés implémentées.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-149">List of properties being implemented.</span></span>  
  
     `implementedproperty [ , implementedproperty ... ]`  
  
     <span data-ttu-id="ab2dc-150">Chaque `implementedproperty` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="ab2dc-150">Each `implementedproperty` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="ab2dc-151">Élément</span><span class="sxs-lookup"><span data-stu-id="ab2dc-151">Part</span></span>|<span data-ttu-id="ab2dc-152">Description</span><span class="sxs-lookup"><span data-stu-id="ab2dc-152">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="ab2dc-153">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-153">Required.</span></span> <span data-ttu-id="ab2dc-154">Nom d’une interface implémentée par cette propriété de la classe ou la structure conteneur.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-154">Name of an interface implemented by this property's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="ab2dc-155">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-155">Required.</span></span> <span data-ttu-id="ab2dc-156">Nom par lequel la propriété est définie dans `interface`.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-156">Name by which the property is defined in `interface`.</span></span>|  
  
-   `Get`  
  
     <span data-ttu-id="ab2dc-157">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-157">Optional.</span></span> <span data-ttu-id="ab2dc-158">Obligatoire si la propriété est marquée `WriteOnly`.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-158">Required if the property is marked `WriteOnly`.</span></span> <span data-ttu-id="ab2dc-159">Démarre un `Get` procédure de propriété qui est utilisée pour retourner la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-159">Starts a `Get` property procedure that is used to return the value of the property.</span></span>  
  
-   `statements`  
  
     <span data-ttu-id="ab2dc-160">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-160">Optional.</span></span> <span data-ttu-id="ab2dc-161">Bloc d’instructions à exécuter dans le `Get` ou `Set` procédure.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-161">Block of statements to run within the `Get` or `Set` procedure.</span></span>  
  
-   `End Get`  
  
     <span data-ttu-id="ab2dc-162">Met fin à la `Get` procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-162">Terminates the `Get` property procedure.</span></span>  
  
-   `Set`  
  
     <span data-ttu-id="ab2dc-163">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-163">Optional.</span></span> <span data-ttu-id="ab2dc-164">Obligatoire si la propriété est marquée `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-164">Required if the property is marked `ReadOnly`.</span></span> <span data-ttu-id="ab2dc-165">Démarre un `Set` procédure de propriété qui est utilisé pour stocker la valeur de la propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-165">Starts a `Set` property procedure that is used to store the value of the property.</span></span>  
  
-   `End Set`  
  
     <span data-ttu-id="ab2dc-166">Met fin à la `Set` procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-166">Terminates the `Set` property procedure.</span></span>  
  
-   `End Property`  
  
     <span data-ttu-id="ab2dc-167">Met fin à la définition de cette propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-167">Terminates the definition of this property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab2dc-168">Remarques</span><span class="sxs-lookup"><span data-stu-id="ab2dc-168">Remarks</span></span>  
 <span data-ttu-id="ab2dc-169">La `Property` instruction introduit la déclaration d’une propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-169">The `Property` statement introduces the declaration of a property.</span></span> <span data-ttu-id="ab2dc-170">Une propriété peut avoir un `Get` procédure (lecture seule), un `Set` procédure (écriture seule), ou les deux (lecture-écriture).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-170">A property can have a `Get` procedure (read only), a `Set` procedure (write only), or both (read-write).</span></span> <span data-ttu-id="ab2dc-171">Vous pouvez omettre le `Get` et `Set` procédure lors de l’utilisation d’une propriété implémentée automatiquement.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-171">You can omit the `Get` and `Set` procedure when using an auto-implemented property.</span></span> <span data-ttu-id="ab2dc-172">Pour plus d’informations, consultez [auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-172">For more information, see [Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md).</span></span>  
  
 <span data-ttu-id="ab2dc-173">Vous pouvez utiliser `Property` uniquement au niveau de classe.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-173">You can use `Property` only at class level.</span></span> <span data-ttu-id="ab2dc-174">Cela signifie que la *contexte de déclaration* pour une propriété doit être une classe, une structure, un module ou une interface et ne peut pas être un fichier source, un espace de noms, une procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-174">This means the *declaration context* for a property must be a class, structure, module, or interface, and cannot be a source file, namespace, procedure, or block.</span></span> <span data-ttu-id="ab2dc-175">Pour plus d’informations, consultez [contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-175">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="ab2dc-176">Par défaut, les propriétés utilisent un accès public.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-176">By default, properties use public access.</span></span> <span data-ttu-id="ab2dc-177">Vous pouvez ajuster le niveau d’accès d’une propriété avec un modificateur d’accès sur la `Property` instruction et vous pouvez éventuellement appliquer une de ses procédures de propriété à un niveau d’accès plus restrictif.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-177">You can adjust a property's access level with an access modifier on the `Property` statement, and you can optionally adjust one of its property procedures to a more restrictive access level.</span></span>  
  
 <span data-ttu-id="ab2dc-178">Visual Basic passe un paramètre à la `Set` procédure pendant les assignations de propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-178">Visual Basic passes a parameter to the `Set` procedure during property assignments.</span></span> <span data-ttu-id="ab2dc-179">Si vous ne fournissez pas de paramètre pour `Set`, l’environnement de développement intégré (IDE) utilise un paramètre implicite nommé `value`.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-179">If you do not supply a parameter for `Set`, the integrated development environment (IDE) uses an implicit parameter named `value`.</span></span> <span data-ttu-id="ab2dc-180">Ce paramètre conserve la valeur à affecter à la propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-180">This parameter holds the value to be assigned to the property.</span></span> <span data-ttu-id="ab2dc-181">Vous en général de stocker cette valeur dans une variable locale privée et retourner chaque fois que le `Get` procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-181">You typically store this value in a private local variable and return it whenever the `Get` procedure is called.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="ab2dc-182">Règles</span><span class="sxs-lookup"><span data-stu-id="ab2dc-182">Rules</span></span>  
  
-   <span data-ttu-id="ab2dc-183">**Niveaux d’accès mixtes.**</span><span class="sxs-lookup"><span data-stu-id="ab2dc-183">**Mixed Access Levels.**</span></span> <span data-ttu-id="ab2dc-184">Si vous définissez une propriété en lecture-écriture, vous pouvez éventuellement spécifier un niveau d’accès différent pour un le `Get` ou `Set` procédure, mais pas les deux.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-184">If you are defining a read-write property, you can optionally specify a different access level for either the `Get` or the `Set` procedure, but not both.</span></span> <span data-ttu-id="ab2dc-185">Si vous procédez ainsi, le niveau d’accès de la procédure doit être plus restrictif que le niveau d’accès de la propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-185">If you do this, the procedure access level must be more restrictive than the property's access level.</span></span> <span data-ttu-id="ab2dc-186">Par exemple, si la propriété est déclarée `Friend`, vous pouvez déclarer le `Set` procédure `Private`, mais pas `Public`.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-186">For example, if the property is declared `Friend`, you can declare the `Set` procedure `Private`, but not `Public`.</span></span>  
  
     <span data-ttu-id="ab2dc-187">Si vous définissez un `ReadOnly` ou `WriteOnly` propriété, la procédure de propriété unique (`Get` ou `Set`, respectivement) représente la propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-187">If you are defining a `ReadOnly` or `WriteOnly` property, the single property procedure (`Get` or `Set`, respectively) represents all of the property.</span></span> <span data-ttu-id="ab2dc-188">Vous ne pouvez pas déclarer un niveau d’accès différent pour cette procédure, parce que seront définis à deux niveaux d’accès pour la propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-188">You cannot declare a different access level for such a procedure, because that would set two access levels for the property.</span></span>  
  
-   <span data-ttu-id="ab2dc-189">**Type de retour.**</span><span class="sxs-lookup"><span data-stu-id="ab2dc-189">**Return Type.**</span></span> <span data-ttu-id="ab2dc-190">La `Property` instruction peut déclarer le type de données de la valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-190">The `Property` statement can declare the data type of the value it returns.</span></span> <span data-ttu-id="ab2dc-191">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, une structure, une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-191">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
     <span data-ttu-id="ab2dc-192">Si vous ne spécifiez pas `returntype`, la propriété renvoie `Object`.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-192">If you do not specify `returntype`, the property returns `Object`.</span></span>  
  
-   <span data-ttu-id="ab2dc-193">**Mise en œuvre.**</span><span class="sxs-lookup"><span data-stu-id="ab2dc-193">**Implementation.**</span></span> <span data-ttu-id="ab2dc-194">Si cette propriété utilise le `Implements` (mot clé), la classe ou la structure conteneur doit avoir un `Implements` suit immédiatement sa `Class` ou `Structure` instruction.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-194">If this property uses the `Implements` keyword, the containing class or structure must have an `Implements` statement immediately following its `Class` or `Structure` statement.</span></span> <span data-ttu-id="ab2dc-195">Le `Implements` doit inclure chaque interface spécifiée dans `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-195">The `Implements` statement must include each interface specified in `implementslist`.</span></span> <span data-ttu-id="ab2dc-196">Toutefois, le nom par lequel une interface définit les `Property` (dans `definedname`) ne devra pas être le même que le nom de cette propriété (dans `name`).</span><span class="sxs-lookup"><span data-stu-id="ab2dc-196">However, the name by which an interface defines the `Property` (in `definedname`) does not have to be the same as the name of this property (in `name`).</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="ab2dc-197">Comportement</span><span class="sxs-lookup"><span data-stu-id="ab2dc-197">Behavior</span></span>  
  
-   <span data-ttu-id="ab2dc-198">**Retour d’une procédure de propriété.**</span><span class="sxs-lookup"><span data-stu-id="ab2dc-198">**Returning from a Property Procedure.**</span></span> <span data-ttu-id="ab2dc-199">Lors de la `Get` ou `Set` procédure retourne au code appelant, l’exécution se poursuit avec l’instruction qui suit l’instruction qui l’a appelée.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-199">When the `Get` or `Set` procedure returns to the calling code, execution continues with the statement following the statement that invoked it.</span></span>  
  
     <span data-ttu-id="ab2dc-200">Le `Exit Property` et `Return` instructions provoquent la sortie immédiate d’une procédure de propriété.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-200">The `Exit Property` and `Return` statements cause an immediate exit from a property procedure.</span></span> <span data-ttu-id="ab2dc-201">Un nombre quelconque de `Exit Property` et `Return` instructions peuvent apparaître n’importe où dans la procédure, et vous pouvez mélanger `Exit Property` et `Return` instructions.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-201">Any number of `Exit Property` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Property` and `Return` statements.</span></span>  
  
-   <span data-ttu-id="ab2dc-202">**Valeur de retour.**</span><span class="sxs-lookup"><span data-stu-id="ab2dc-202">**Return Value.**</span></span> <span data-ttu-id="ab2dc-203">Pour retourner une valeur depuis une `Get` procédure, vous pouvez affecter la valeur au nom de propriété ou l’inclure dans un `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-203">To return a value from a `Get` procedure, you can either assign the value to the property name or include it in a `Return` statement.</span></span> <span data-ttu-id="ab2dc-204">L’exemple suivant affecte la valeur de retour au nom de propriété `quoteForTheDay` , puis utilise la `Exit Property` instruction à retourner.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-204">The following example assigns the return value to the property name `quoteForTheDay` and then uses the `Exit Property` statement to return.</span></span>  
  
     <span data-ttu-id="ab2dc-205">[!code-vb[27 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab2dc-205">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="ab2dc-206">[!code-vb[VbVbalrStatements&#28;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab2dc-206">[!code-vb[VbVbalrStatements#28](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_2.vb)]</span></span>  
  
     <span data-ttu-id="ab2dc-207">Si vous utilisez `Exit Property` sans assigner une valeur à `name`, le `Get` procédure retourne la valeur par défaut pour le type de données.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-207">If you use `Exit Property` without assigning a value to `name`, the `Get` procedure returns the default value for the property's data type.</span></span>  
  
     <span data-ttu-id="ab2dc-208">Le `Return` instruction en même temps affecte le `Get` procédure retourner de valeur et termine la procédure.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-208">The `Return` statement at the same time assigns the `Get` procedure return value and exits the procedure.</span></span> <span data-ttu-id="ab2dc-209">L’exemple suivant illustre ce point.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-209">The following example shows this.</span></span>  
  
     <span data-ttu-id="ab2dc-210">[!code-vb[27 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab2dc-210">[!code-vb[VbVbalrStatements#27](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_1.vb)]</span></span>  
  
     <span data-ttu-id="ab2dc-211">[!code-vb[VbVbalrStatements&#29;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab2dc-211">[!code-vb[VbVbalrStatements#29](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab2dc-212">Exemple</span><span class="sxs-lookup"><span data-stu-id="ab2dc-212">Example</span></span>  
 <span data-ttu-id="ab2dc-213">L’exemple suivant déclare une propriété dans une classe.</span><span class="sxs-lookup"><span data-stu-id="ab2dc-213">The following example declares a property in a class.</span></span>  
  
 <span data-ttu-id="ab2dc-214">[!code-vb[VbVbalrStatements&#51;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab2dc-214">[!code-vb[VbVbalrStatements#51](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/property-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab2dc-215">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab2dc-215">See Also</span></span>  
 <span data-ttu-id="ab2dc-216">[Propriétés implémentées automatiquement](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span><span class="sxs-lookup"><span data-stu-id="ab2dc-216">[Auto-Implemented Properties](../../../visual-basic/programming-guide/language-features/procedures/auto-implemented-properties.md) </span></span>  
<span data-ttu-id="ab2dc-217"> [Objets et Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab2dc-217"> [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) </span></span>  
<span data-ttu-id="ab2dc-218"> [Get (instruction)](../../../visual-basic/language-reference/statements/get-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ab2dc-218"> [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md) </span></span>  
<span data-ttu-id="ab2dc-219"> [Set, instruction](../../../visual-basic/language-reference/statements/set-statement.md) </span><span class="sxs-lookup"><span data-stu-id="ab2dc-219"> [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md) </span></span>  
<span data-ttu-id="ab2dc-220"> [Liste de paramètres](../../../visual-basic/language-reference/statements/parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="ab2dc-220"> [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md) </span></span>  
<span data-ttu-id="ab2dc-221"> [Default](../../../visual-basic/language-reference/modifiers/default.md)</span><span class="sxs-lookup"><span data-stu-id="ab2dc-221"> [Default](../../../visual-basic/language-reference/modifiers/default.md)</span></span>

