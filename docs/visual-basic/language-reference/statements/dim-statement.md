---
title: Dim, instruction (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Dim
- Dim
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, in Dim statement
- Dim statement
- fixed-length strings, declaring
- variables [Visual Basic], declaring
- WithEvents keyword, Dim statement
- dynamic arrays, Dim statement
- variables [Visual Basic], initializing
- '{} braces'
- fields, as member variables
- declarations, dynamic arrays
- member variables
- default values
- data types [Visual Basic], assigning
- braces {}
- As keyword, in Dim statement
- arrays [Visual Basic], declaring
- New keyword, Dim statement
- To keyword, in Dim statement
- storage, allocating
- local variables
- declaration statements
- Dim statement, syntax
- variables [Visual Basic], member and local
ms.assetid: fae3eca1-f0b2-4400-994b-7aa58a848448
caps.latest.revision: 72
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
ms.openlocfilehash: 049ab1e82bac6c9f94bc411cd3e7c859e334d739
ms.contentlocale: fr-fr
ms.lasthandoff: 05/15/2017

---
# <a name="dim-statement-visual-basic"></a><span data-ttu-id="7e13f-102">Dim, instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7e13f-102">Dim Statement (Visual Basic)</span></span>
<span data-ttu-id="7e13f-103">Déclare et alloue de l’espace de stockage pour une ou plusieurs variables.</span><span class="sxs-lookup"><span data-stu-id="7e13f-103">Declares and allocates storage space for one or more variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e13f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e13f-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [[ Shared ] [ Shadows ] | [ Static ]] [ ReadOnly ]   
Dim [ WithEvents ] variablelist  
```  
  
## <a name="parts"></a><span data-ttu-id="7e13f-105">Composants</span><span class="sxs-lookup"><span data-stu-id="7e13f-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="7e13f-106">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-106">Optional.</span></span> <span data-ttu-id="7e13f-107">Consultez la page [liste d’attributs](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="7e13f-108">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-108">Optional.</span></span> <span data-ttu-id="7e13f-109">Il peut s'agir d'une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="7e13f-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="7e13f-110">Public</span><span class="sxs-lookup"><span data-stu-id="7e13f-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="7e13f-111">Protected</span><span class="sxs-lookup"><span data-stu-id="7e13f-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="7e13f-112">Friend</span><span class="sxs-lookup"><span data-stu-id="7e13f-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="7e13f-113">Private</span><span class="sxs-lookup"><span data-stu-id="7e13f-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="7e13f-114">Consultez la page [niveaux en Visual Basic d’accès](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-114">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `Shared`  
  
     <span data-ttu-id="7e13f-115">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-115">Optional.</span></span> <span data-ttu-id="7e13f-116">Consultez la page [partagé](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-116">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="7e13f-117">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-117">Optional.</span></span> <span data-ttu-id="7e13f-118">Consultez la page [ombres](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-118">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Static`  
  
     <span data-ttu-id="7e13f-119">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-119">Optional.</span></span> <span data-ttu-id="7e13f-120">Consultez la page [statique](../../../visual-basic/language-reference/modifiers/static.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-120">See [Static](../../../visual-basic/language-reference/modifiers/static.md).</span></span>  
  
-   `ReadOnly`  
  
     <span data-ttu-id="7e13f-121">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-121">Optional.</span></span> <span data-ttu-id="7e13f-122">Consultez la page [en lecture seule](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-122">See [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
-   `WithEvents`  
  
     <span data-ttu-id="7e13f-123">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-123">Optional.</span></span> <span data-ttu-id="7e13f-124">Spécifie qu’il s’agit de variables objets qui font référence aux instances d’une classe qui peut déclencher des événements.</span><span class="sxs-lookup"><span data-stu-id="7e13f-124">Specifies that these are object variables that refer to instances of a class that can raise events.</span></span> <span data-ttu-id="7e13f-125">Consultez la page [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-125">See [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md).</span></span>  
  
-   `variablelist`  
  
     <span data-ttu-id="7e13f-126">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7e13f-126">Required.</span></span> <span data-ttu-id="7e13f-127">Liste de variables déclarées dans cette instruction.</span><span class="sxs-lookup"><span data-stu-id="7e13f-127">List of variables being declared in this statement.</span></span>  
  
     `variable [ , variable ... ]`  
  
     <span data-ttu-id="7e13f-128">Chaque `variable` emploie la syntaxe et les éléments suivants :</span><span class="sxs-lookup"><span data-stu-id="7e13f-128">Each `variable` has the following syntax and parts:</span></span>  
  
     <span data-ttu-id="7e13f-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span><span class="sxs-lookup"><span data-stu-id="7e13f-129">`variablename [ ( [ boundslist ] ) ] [ As [ New ] datatype [ With`{`[ .propertyname = propinitializer [ , ... ] ] } ] ] [ = initializer ]`</span></span>  
  
    |<span data-ttu-id="7e13f-130">Élément</span><span class="sxs-lookup"><span data-stu-id="7e13f-130">Part</span></span>|<span data-ttu-id="7e13f-131">Description</span><span class="sxs-lookup"><span data-stu-id="7e13f-131">Description</span></span>|  
    |---|---|  
    |`variablename`|<span data-ttu-id="7e13f-132">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="7e13f-132">Required.</span></span> <span data-ttu-id="7e13f-133">Nom de la variable.</span><span class="sxs-lookup"><span data-stu-id="7e13f-133">Name of the variable.</span></span> <span data-ttu-id="7e13f-134">Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
    |`boundslist`|<span data-ttu-id="7e13f-135">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-135">Optional.</span></span> <span data-ttu-id="7e13f-136">Liste des limites de chaque dimension d’une variable tableau.</span><span class="sxs-lookup"><span data-stu-id="7e13f-136">List of bounds of each dimension of an array variable.</span></span>|  
    |`New`|<span data-ttu-id="7e13f-137">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-137">Optional.</span></span> <span data-ttu-id="7e13f-138">Crée une nouvelle instance de la classe lors de la `Dim` instruction s’exécute.</span><span class="sxs-lookup"><span data-stu-id="7e13f-138">Creates a new instance of the class when the `Dim` statement runs.</span></span>|  
    |`datatype`|<span data-ttu-id="7e13f-139">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-139">Optional.</span></span> <span data-ttu-id="7e13f-140">Type de données de la variable.</span><span class="sxs-lookup"><span data-stu-id="7e13f-140">Data type of the variable.</span></span>|  
    |`With`|<span data-ttu-id="7e13f-141">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-141">Optional.</span></span> <span data-ttu-id="7e13f-142">Présente la liste d’initialiseurs objet.</span><span class="sxs-lookup"><span data-stu-id="7e13f-142">Introduces the object initializer list.</span></span>|  
    |`propertyname`|<span data-ttu-id="7e13f-143">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="7e13f-143">Optional.</span></span> <span data-ttu-id="7e13f-144">Le nom d’une propriété dans la classe que vous tentez une instance de.</span><span class="sxs-lookup"><span data-stu-id="7e13f-144">The name of a property in the class you are making an instance of.</span></span>|  
    |`propinitializer`|<span data-ttu-id="7e13f-145">Requis après `propertyname` =.</span><span class="sxs-lookup"><span data-stu-id="7e13f-145">Required after `propertyname` =.</span></span> <span data-ttu-id="7e13f-146">L’expression qui est évaluée et assignée au nom de propriété.</span><span class="sxs-lookup"><span data-stu-id="7e13f-146">The expression that is evaluated and assigned to the property name.</span></span>|  
    |`initializer`|<span data-ttu-id="7e13f-147">Facultatif si `New` n’est pas spécifié.</span><span class="sxs-lookup"><span data-stu-id="7e13f-147">Optional if `New` is not specified.</span></span> <span data-ttu-id="7e13f-148">Expression qui est évaluée et assignée à la variable lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="7e13f-148">Expression that is evaluated and assigned to the variable when it is created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e13f-149">Remarques</span><span class="sxs-lookup"><span data-stu-id="7e13f-149">Remarks</span></span>  
 <span data-ttu-id="7e13f-150">Le compilateur Visual Basic utilise le `Dim` pour déterminer le type de données de la variable et d’autres informations, telles que le code peut accéder à la variable.</span><span class="sxs-lookup"><span data-stu-id="7e13f-150">The Visual Basic compiler uses the `Dim` statement to determine the variable's data type and other information, such as what code can access the variable.</span></span> <span data-ttu-id="7e13f-151">L’exemple suivant déclare une variable pour contenir un `Integer` valeur.</span><span class="sxs-lookup"><span data-stu-id="7e13f-151">The following example declares a variable to hold an `Integer` value.</span></span>  
  
```vb  
Dim numberOfStudents As Integer  
```  
  
 <span data-ttu-id="7e13f-152">Vous pouvez spécifier n’importe quel type de données ou le nom d’une énumération, une structure, une classe ou une interface.</span><span class="sxs-lookup"><span data-stu-id="7e13f-152">You can specify any data type or the name of an enumeration, structure, class, or interface.</span></span>  
  
```vb  
Dim finished As Boolean  
Dim monitorBox As System.Windows.Forms.Form  
```  
  
 <span data-ttu-id="7e13f-153">Pour un type référence, vous utilisez la `New` mot clé pour créer une nouvelle instance de la classe ou une structure qui est spécifié par le type de données.</span><span class="sxs-lookup"><span data-stu-id="7e13f-153">For a reference type, you use the `New` keyword to create a new instance of the class or structure that is specified by the data type.</span></span> <span data-ttu-id="7e13f-154">Si vous utilisez `New`, vous n’utilisez pas une expression d’initialiseur.</span><span class="sxs-lookup"><span data-stu-id="7e13f-154">If you use `New`, you do not use an initializer expression.</span></span> <span data-ttu-id="7e13f-155">Au lieu de cela, vous fournissez des arguments, s’ils sont requis, au constructeur de la classe à partir de laquelle vous créez la variable.</span><span class="sxs-lookup"><span data-stu-id="7e13f-155">Instead, you supply arguments, if they are required, to the constructor of the class from which you are creating the variable.</span></span>  
  
```vb  
Dim bottomLabel As New System.Windows.Forms.Label  
```  
  
 <span data-ttu-id="7e13f-156">Vous pouvez déclarer une variable dans une procédure, un bloc, une classe, une structure ou un module.</span><span class="sxs-lookup"><span data-stu-id="7e13f-156">You can declare a variable in a procedure, block, class, structure, or module.</span></span> <span data-ttu-id="7e13f-157">Vous ne pouvez pas déclarer une variable dans un fichier source, un espace de noms ou une interface.</span><span class="sxs-lookup"><span data-stu-id="7e13f-157">You cannot declare a variable in a source file, namespace, or interface.</span></span> <span data-ttu-id="7e13f-158">Pour plus d’informations, consultez [contextes de déclaration et niveaux d’accès par défaut](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-158">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="7e13f-159">Une variable déclarée au niveau du module, en dehors de toute procédure, est une *variable membre* ou *champ*.</span><span class="sxs-lookup"><span data-stu-id="7e13f-159">A variable that is declared at module level, outside any procedure, is a *member variable* or *field*.</span></span> <span data-ttu-id="7e13f-160">Les variables membres sont dans la portée de leur classe, structure ou module.</span><span class="sxs-lookup"><span data-stu-id="7e13f-160">Member variables are in scope throughout their class, structure, or module.</span></span> <span data-ttu-id="7e13f-161">Une variable déclarée au niveau de la procédure est un *variable locale*.</span><span class="sxs-lookup"><span data-stu-id="7e13f-161">A variable that is declared at procedure level is a *local variable*.</span></span> <span data-ttu-id="7e13f-162">Les variables locales sont dans la portée uniquement au sein de leur procédure ou bloc.</span><span class="sxs-lookup"><span data-stu-id="7e13f-162">Local variables are in scope only within their procedure or block.</span></span>  
  
 <span data-ttu-id="7e13f-163">Modificateurs d’accès suivants sont utilisés pour déclarer des variables en dehors d’une procédure : `Public`, `Protected`, `Friend`, `Protected Friend`, et `Private`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-163">The following access modifiers are used to declare variables outside a procedure: `Public`, `Protected`, `Friend`, `Protected Friend`, and `Private`.</span></span> <span data-ttu-id="7e13f-164">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-164">For more information, see [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
 <span data-ttu-id="7e13f-165">Le `Dim` mot clé est facultatif et généralement omis si vous spécifiez un des modificateurs suivants : `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, ou `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-165">The `Dim` keyword is optional and usually omitted if you specify any of the following modifiers: `Public`, `Protected`, `Friend`, `Protected Friend`, `Private`, `Shared`, `Shadows`, `Static`, `ReadOnly`, or `WithEvents`.</span></span>  
  
```vb  
Public maximumAllowed As Double  
Protected Friend currentUserName As String  
Private salary As Decimal  
Static runningTotal As Integer  
```  
  
 <span data-ttu-id="7e13f-166">Si `Option Explicit` est activée (par défaut), le compilateur requiert une déclaration pour chaque variable que vous utilisez.</span><span class="sxs-lookup"><span data-stu-id="7e13f-166">If `Option Explicit` is on (the default), the compiler requires a declaration for every variable you use.</span></span> <span data-ttu-id="7e13f-167">Pour plus d’informations, consultez [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-167">For more information, see [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md).</span></span>  
  
## <a name="specifying-an-initial-value"></a><span data-ttu-id="7e13f-168">Spécifier une valeur initiale</span><span class="sxs-lookup"><span data-stu-id="7e13f-168">Specifying an Initial Value</span></span>  
 <span data-ttu-id="7e13f-169">Vous pouvez affecter une valeur à une variable lors de sa création.</span><span class="sxs-lookup"><span data-stu-id="7e13f-169">You can assign a value to a variable when it is created.</span></span> <span data-ttu-id="7e13f-170">Pour un type valeur, vous utilisez un *initialiseur* pour fournir une expression à assigner à la variable.</span><span class="sxs-lookup"><span data-stu-id="7e13f-170">For a value type, you use an *initializer* to supply an expression to be assigned to the variable.</span></span> <span data-ttu-id="7e13f-171">L’expression doit correspondre à une constante qui peut être calculée au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7e13f-171">The expression must evaluate to a constant that can be calculated at compile time.</span></span>  
  
```vb  
Dim quantity As Integer = 10  
Dim message As String = "Just started"  
```  
  
 <span data-ttu-id="7e13f-172">Si un initialiseur est spécifié et un type de données n’est pas spécifié dans un `As` clause, *l’inférence de type* est utilisée pour déduire le type de données à partir de l’initialiseur.</span><span class="sxs-lookup"><span data-stu-id="7e13f-172">If an initializer is specified and a data type is not specified in an `As` clause, *type inference* is used to infer the data type from the initializer.</span></span> <span data-ttu-id="7e13f-173">Dans l’exemple suivant, les deux `num1` et `num2` sont fortement typés comme entiers.</span><span class="sxs-lookup"><span data-stu-id="7e13f-173">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span> <span data-ttu-id="7e13f-174">Dans la seconde déclaration, l’inférence de type déduit le type de la valeur 3.</span><span class="sxs-lookup"><span data-stu-id="7e13f-174">In the second declaration, type inference infers the type from the value 3.</span></span>  
  
```vb  
' Use explicit typing.  
Dim num1 As Integer = 3  
  
' Use local type inference.  
Dim num2 = 3  
```  
  
 <span data-ttu-id="7e13f-175">L’inférence de type s’applique au niveau de la procédure.</span><span class="sxs-lookup"><span data-stu-id="7e13f-175">Type inference applies at the procedure level.</span></span> <span data-ttu-id="7e13f-176">Il ne s’applique pas à l’extérieur d’une procédure dans une classe, une structure, un module ou une interface.</span><span class="sxs-lookup"><span data-stu-id="7e13f-176">It does not apply outside a procedure in a class, structure, module, or interface.</span></span> <span data-ttu-id="7e13f-177">Pour plus d’informations sur l’inférence de type, consultez la page [Option Infer, instruction](../../../visual-basic/language-reference/statements/option-infer-statement.md) et [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-177">For more information about type inference, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
 <span data-ttu-id="7e13f-178">Pour plus d’informations sur ce qui se passe lorsqu’un type de données ou un initialiseur n’est pas spécifié, consultez [par défaut des Types de données et les valeurs](../../../visual-basic/language-reference/statements/dim-statement.md#default) plus loin dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="7e13f-178">For information about what happens when a data type or initializer is not specified, see [Default Data Types and Values](../../../visual-basic/language-reference/statements/dim-statement.md#default) later in this topic.</span></span>  
  
 <span data-ttu-id="7e13f-179">Vous pouvez utiliser un *initialiseur d’objet* pour déclarer des instances de types nommés et anonymes.</span><span class="sxs-lookup"><span data-stu-id="7e13f-179">You can use an *object initializer* to declare instances of named and anonymous types.</span></span> <span data-ttu-id="7e13f-180">Le code suivant crée une instance d’un `Student` de classe et utilise un initialiseur d’objet pour initialiser les propriétés.</span><span class="sxs-lookup"><span data-stu-id="7e13f-180">The following code creates an instance of a `Student` class and uses an object initializer to initialize properties.</span></span>  
  
```vb  
Dim student1 As New Student With {.First = "Michael",   
                                  .Last = "Tucker"}  
```  
  
 <span data-ttu-id="7e13f-181">Pour plus d’informations sur les initialiseurs d’objets, consultez [Comment : déclarer un objet à l’aide d’un initialiseur d’objet](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [initialiseurs d’objets : Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), et [les Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-181">For more information about object initializers, see [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md), [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md), and [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).</span></span>  
  
## <a name="declaring-multiple-variables"></a><span data-ttu-id="7e13f-182">Déclaration de Variables multiples</span><span class="sxs-lookup"><span data-stu-id="7e13f-182">Declaring Multiple Variables</span></span>  
 <span data-ttu-id="7e13f-183">Vous pouvez déclarer plusieurs variables dans la même instruction de déclaration, en spécifiant le nom de variable pour chacun d’eux et suivre chaque nom de tableau de parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7e13f-183">You can declare several variables in one declaration statement, specifying the variable name for each one, and following each array name with parentheses.</span></span> <span data-ttu-id="7e13f-184">Les variables multiples sont séparées par des virgules.</span><span class="sxs-lookup"><span data-stu-id="7e13f-184">Multiple variables are separated by commas.</span></span>  
  
```vb  
Dim lastTime, nextTime, allTimes() As Date  
```  
  
 <span data-ttu-id="7e13f-185">Si vous déclarez plusieurs variables avec une `As` clause, vous ne pouvez pas spécifier un initialiseur pour ce groupe de variables.</span><span class="sxs-lookup"><span data-stu-id="7e13f-185">If you declare more than one variable with one `As` clause, you cannot supply an initializer for that group of variables.</span></span>  
  
 <span data-ttu-id="7e13f-186">Vous pouvez spécifier différents types de données pour différentes variables à l’aide de distinct `As` pour chaque variable que vous déclarez.</span><span class="sxs-lookup"><span data-stu-id="7e13f-186">You can specify different data types for different variables by using a separate `As` clause for each variable you declare.</span></span> <span data-ttu-id="7e13f-187">Chaque variable prend le type de données spécifié dans la première `As` clause rencontrée après son `variablename` partie.</span><span class="sxs-lookup"><span data-stu-id="7e13f-187">Each variable takes the data type specified in the first `As` clause encountered after its `variablename` part.</span></span>  
  
```vb  
Dim a, b, c As Single, x, y As Double, i As Integer  
' a, b, and c are all Single; x and y are both Double  
```  
  
## <a name="arrays"></a><span data-ttu-id="7e13f-188">Tableaux</span><span class="sxs-lookup"><span data-stu-id="7e13f-188">Arrays</span></span>  
 <span data-ttu-id="7e13f-189">Vous pouvez déclarer une variable pour contenir un *tableau*, qui peut contenir plusieurs valeurs.</span><span class="sxs-lookup"><span data-stu-id="7e13f-189">You can declare a variable to hold an *array*, which can hold multiple values.</span></span> <span data-ttu-id="7e13f-190">Pour spécifier qu’une variable contient un tableau, suivez sa `variablename` immédiatement avec des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7e13f-190">To specify that a variable holds an array, follow its `variablename` immediately with parentheses.</span></span> <span data-ttu-id="7e13f-191">Pour plus d’informations sur les tableaux, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-191">For more information about arrays, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="7e13f-192">Vous pouvez spécifier la limite inférieure et supérieure de chaque dimension du tableau.</span><span class="sxs-lookup"><span data-stu-id="7e13f-192">You can specify the lower and upper bound of each dimension of an array.</span></span> <span data-ttu-id="7e13f-193">Pour ce faire, vous devez inclure un `boundslist` à l’intérieur des parenthèses.</span><span class="sxs-lookup"><span data-stu-id="7e13f-193">To do this, include a `boundslist` inside the parentheses.</span></span> <span data-ttu-id="7e13f-194">Pour chaque dimension, le `boundslist` spécifie la limite supérieure et éventuellement la limite inférieure.</span><span class="sxs-lookup"><span data-stu-id="7e13f-194">For each dimension, the `boundslist` specifies the upper bound and optionally the lower bound.</span></span> <span data-ttu-id="7e13f-195">La limite inférieure est toujours égale à zéro, que vous spécifiiez ou non.</span><span class="sxs-lookup"><span data-stu-id="7e13f-195">The lower bound is always zero, whether you specify it or not.</span></span> <span data-ttu-id="7e13f-196">Chaque index peut varier de zéro à sa valeur de limite supérieure.</span><span class="sxs-lookup"><span data-stu-id="7e13f-196">Each index can vary from zero through its upper bound value.</span></span>  
  
 <span data-ttu-id="7e13f-197">Les deux instructions suivantes sont équivalentes.</span><span class="sxs-lookup"><span data-stu-id="7e13f-197">The following two statements are equivalent.</span></span> <span data-ttu-id="7e13f-198">Chaque instruction déclare un tableau de 21 `Integer` éléments.</span><span class="sxs-lookup"><span data-stu-id="7e13f-198">Each statement declares an array of 21 `Integer` elements.</span></span> <span data-ttu-id="7e13f-199">Lorsque vous accédez au tableau, l’index peut varier de 0 à 20.</span><span class="sxs-lookup"><span data-stu-id="7e13f-199">When you access the array, the index can vary from 0 through 20.</span></span>  
  
```vb  
Dim totals(20) As Integer  
Dim totals(0 To 20) As Integer  
```  
  
 <span data-ttu-id="7e13f-200">L’instruction suivante déclare un tableau à deux dimensions de type `Double`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-200">The following statement declares a two-dimensional array of type `Double`.</span></span> <span data-ttu-id="7e13f-201">Le tableau a 4 lignes (3 + 1) de 6 colonnes (5 + 1).</span><span class="sxs-lookup"><span data-stu-id="7e13f-201">The array has 4 rows (3 + 1) of 6 columns (5 + 1) each.</span></span> <span data-ttu-id="7e13f-202">Notez qu’une limite supérieure représente la valeur la plus élevée possible pour l’index, et non la longueur de la dimension.</span><span class="sxs-lookup"><span data-stu-id="7e13f-202">Note that an upper bound represents the highest possible value for the index, not the length of the dimension.</span></span> <span data-ttu-id="7e13f-203">La longueur de la dimension est la limite supérieure plus un.</span><span class="sxs-lookup"><span data-stu-id="7e13f-203">The length of the dimension is the upper bound plus one.</span></span>  
  
```vb  
Dim matrix2(3, 5) As Double  
```  
  
 <span data-ttu-id="7e13f-204">Un tableau peut avoir de 1 à 32 dimensions.</span><span class="sxs-lookup"><span data-stu-id="7e13f-204">An array can have from 1 to 32 dimensions.</span></span>  
  
 <span data-ttu-id="7e13f-205">Vous pouvez laisser toutes les limites vides dans une déclaration de tableau.</span><span class="sxs-lookup"><span data-stu-id="7e13f-205">You can leave all the bounds blank in an array declaration.</span></span> <span data-ttu-id="7e13f-206">Si vous le faites, le tableau a le nombre de dimensions que vous spécifiez, mais il n’est pas initialisé.</span><span class="sxs-lookup"><span data-stu-id="7e13f-206">If you do this, the array has the number of dimensions you specify, but it is uninitialized.</span></span> <span data-ttu-id="7e13f-207">Il a la valeur `Nothing` jusqu'à ce que vous initialisez au moins certains de ses éléments.</span><span class="sxs-lookup"><span data-stu-id="7e13f-207">It has a value of `Nothing` until you initialize at least some of its elements.</span></span> <span data-ttu-id="7e13f-208">La `Dim` instruction doit spécifier des limites pour toutes les dimensions ou pour aucune d'entre elles.</span><span class="sxs-lookup"><span data-stu-id="7e13f-208">The `Dim` statement must specify bounds either for all dimensions or for no dimensions.</span></span>  
  
```vb  
' Declare an array with blank array bounds.  
Dim messages() As String  
' Initialize the array.  
ReDim messages(4)  
```  
  
 <span data-ttu-id="7e13f-209">Si le tableau a plusieurs dimensions, vous devez inclure des virgules entre parenthèses pour indiquer le nombre de dimensions.</span><span class="sxs-lookup"><span data-stu-id="7e13f-209">If the array has more than one dimension, you must include commas between the parentheses to indicate the number of dimensions.</span></span>  
  
```vb  
Dim oneDimension(), twoDimensions(,), threeDimensions(,,) As Byte  
```  
  
 <span data-ttu-id="7e13f-210">Vous pouvez déclarer un *tableau de longueur zéro* en déclarant une des dimensions du tableau-1.</span><span class="sxs-lookup"><span data-stu-id="7e13f-210">You can declare a *zero-length array* by declaring one of the array's dimensions to be -1.</span></span> <span data-ttu-id="7e13f-211">Une variable contenant un tableau de longueur zéro n’a pas la valeur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-211">A variable that holds a zero-length array does not have the value `Nothing`.</span></span> <span data-ttu-id="7e13f-212">Tableaux de longueur zéro sont requis par certaines fonctions du common language runtime.</span><span class="sxs-lookup"><span data-stu-id="7e13f-212">Zero-length arrays are required by certain common language runtime functions.</span></span> <span data-ttu-id="7e13f-213">Si vous essayez d’accéder à un tel tableau, une exception runtime se produit.</span><span class="sxs-lookup"><span data-stu-id="7e13f-213">If you try to access such an array, a runtime exception occurs.</span></span> <span data-ttu-id="7e13f-214">Pour plus d’informations, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-214">For more information, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
 <span data-ttu-id="7e13f-215">Vous pouvez initialiser les valeurs d’un tableau à l’aide d’un littéral de tableau.</span><span class="sxs-lookup"><span data-stu-id="7e13f-215">You can initialize the values of an array by using an array literal.</span></span> <span data-ttu-id="7e13f-216">Pour ce faire, ajoutez les valeurs d’initialisation entre accolades (`{}`).</span><span class="sxs-lookup"><span data-stu-id="7e13f-216">To do this, surround the initialization values with braces (`{}`).</span></span>  
  
```vb  
Dim longArray() As Long = {0, 1, 2, 3}  
```  
  
 <span data-ttu-id="7e13f-217">Pour les tableaux multidimensionnels, l’initialisation de chaque dimension séparée est entourée d’accolades dans la dimension externe.</span><span class="sxs-lookup"><span data-stu-id="7e13f-217">For multidimensional arrays, the initialization for each separate dimension is enclosed in braces in the outer dimension.</span></span> <span data-ttu-id="7e13f-218">Les éléments sont spécifiés dans l’ordre ligne-champ.</span><span class="sxs-lookup"><span data-stu-id="7e13f-218">The elements are specified in row-major order.</span></span>  
  
```vb  
Dim twoDimensions(,) As Integer = {{0, 1, 2}, {10, 11, 12}}  
```  
  
 <span data-ttu-id="7e13f-219">Pour plus d’informations sur les littéraux de tableaux, consultez [tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-219">For more information about array literals, see [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md).</span></span>  
  
##  <span data-ttu-id="7e13f-220"><a name="default"></a>Valeurs et Types de données par défaut</span><span class="sxs-lookup"><span data-stu-id="7e13f-220"><a name="default"></a> Default Data Types and Values</span></span>  
 <span data-ttu-id="7e13f-221">Le tableau suivant décrit les résultats des diverses combinaisons de spécification du type de données et d'un initialiseur dans une instruction `Dim`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-221">The following table describes the results of various combinations of specifying the data type and initializer in a `Dim` statement.</span></span>  
  
|<span data-ttu-id="7e13f-222">Type de données spécifié ?</span><span class="sxs-lookup"><span data-stu-id="7e13f-222">Data type specified?</span></span>|<span data-ttu-id="7e13f-223">Initialiseur spécifié ?</span><span class="sxs-lookup"><span data-stu-id="7e13f-223">Initializer specified?</span></span>|<span data-ttu-id="7e13f-224">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e13f-224">Example</span></span>|<span data-ttu-id="7e13f-225">Résultat</span><span class="sxs-lookup"><span data-stu-id="7e13f-225">Result</span></span>|  
|---|---|---|---|  
|<span data-ttu-id="7e13f-226">Non</span><span class="sxs-lookup"><span data-stu-id="7e13f-226">No</span></span>|<span data-ttu-id="7e13f-227">Non</span><span class="sxs-lookup"><span data-stu-id="7e13f-227">No</span></span>|`Dim qty`|<span data-ttu-id="7e13f-228">Si [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) est désactivé (par défaut), la variable est définie sur `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-228">If [Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md) is off (the default), the variable is set to `Nothing`.</span></span><br /><br /> <span data-ttu-id="7e13f-229">Si `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7e13f-229">If `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="7e13f-230">Non</span><span class="sxs-lookup"><span data-stu-id="7e13f-230">No</span></span>|<span data-ttu-id="7e13f-231">Oui</span><span class="sxs-lookup"><span data-stu-id="7e13f-231">Yes</span></span>|`Dim qty = 5`|<span data-ttu-id="7e13f-232">Si [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) est activée (par défaut), la variable prend les type de données de l’initialiseur.</span><span class="sxs-lookup"><span data-stu-id="7e13f-232">If [Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) is on (the default), the variable takes the data type of the initializer.</span></span> <span data-ttu-id="7e13f-233">Consultez la page [l’inférence de Type Local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-233">See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span><br /><br /> <span data-ttu-id="7e13f-234">Si `Option Infer` est désactivé et que `Option Strict` est désactivé, la variable prend le type de données de `Object`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-234">If `Option Infer` is off and `Option Strict` is off, the variable takes the data type of `Object`.</span></span><br /><br /> <span data-ttu-id="7e13f-235">Si `Option Infer` est désactivé et que `Option Strict` est activé, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7e13f-235">If `Option Infer` is off and `Option Strict` is on, a compile-time error occurs.</span></span>|  
|<span data-ttu-id="7e13f-236">Oui</span><span class="sxs-lookup"><span data-stu-id="7e13f-236">Yes</span></span>|<span data-ttu-id="7e13f-237">Non</span><span class="sxs-lookup"><span data-stu-id="7e13f-237">No</span></span>|`Dim qty As Integer`|<span data-ttu-id="7e13f-238">La variable est initialisée avec la valeur par défaut du type de données.</span><span class="sxs-lookup"><span data-stu-id="7e13f-238">The variable is initialized to the default value for the data type.</span></span> <span data-ttu-id="7e13f-239">Consultez le tableau plus loin dans cette section.</span><span class="sxs-lookup"><span data-stu-id="7e13f-239">See the table later in this section.</span></span>|  
|<span data-ttu-id="7e13f-240">Oui</span><span class="sxs-lookup"><span data-stu-id="7e13f-240">Yes</span></span>|<span data-ttu-id="7e13f-241">Oui</span><span class="sxs-lookup"><span data-stu-id="7e13f-241">Yes</span></span>|`Dim qty  As Integer = 5`|<span data-ttu-id="7e13f-242">Si le type de données de l’initialiseur ne peut pas être converti dans le type de données spécifié, une erreur se produit au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="7e13f-242">If the data type of the initializer is not convertible to the specified data type, a compile-time error occurs.</span></span>|  
  
 <span data-ttu-id="7e13f-243">Si vous spécifiez un type de données mais que vous ne spécifiez pas un initialiseur, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] initialise la variable à la valeur par défaut pour son type de données.</span><span class="sxs-lookup"><span data-stu-id="7e13f-243">If you specify a data type but do not specify an initializer, [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] initializes the variable to the default value for its data type.</span></span> <span data-ttu-id="7e13f-244">Le tableau suivant présente des valeurs d’initialisation par défaut.</span><span class="sxs-lookup"><span data-stu-id="7e13f-244">The following table shows the default initialization values.</span></span>  
  
|<span data-ttu-id="7e13f-245">Type de données</span><span class="sxs-lookup"><span data-stu-id="7e13f-245">Data type</span></span>|<span data-ttu-id="7e13f-246">Valeur par défaut</span><span class="sxs-lookup"><span data-stu-id="7e13f-246">Default value</span></span>|  
|---|---|  
|<span data-ttu-id="7e13f-247">Tous les types numériques (y compris `Byte` et `SByte`)</span><span class="sxs-lookup"><span data-stu-id="7e13f-247">All numeric types (including `Byte` and `SByte`)</span></span>|<span data-ttu-id="7e13f-248">0</span><span class="sxs-lookup"><span data-stu-id="7e13f-248">0</span></span>|  
|`Char`|<span data-ttu-id="7e13f-249">0 (binaire)</span><span class="sxs-lookup"><span data-stu-id="7e13f-249">Binary 0</span></span>|  
|<span data-ttu-id="7e13f-250">Tous les types référence (y compris `Object`, `String`et tous les tableaux)</span><span class="sxs-lookup"><span data-stu-id="7e13f-250">All reference types (including `Object`, `String`, and all arrays)</span></span>|`Nothing`|  
|`Boolean`|`False`|  
|`Date`|<span data-ttu-id="7e13f-251">12 h 00 le 1er janvier de l’année 1 (01/01/0001 12:00:00 AM)</span><span class="sxs-lookup"><span data-stu-id="7e13f-251">12:00 AM of January 1 of the year 1 (01/01/0001 12:00:00 AM)</span></span>|  
  
 <span data-ttu-id="7e13f-252">Chaque élément d’une structure est initialisé comme s’il s’agissait d’une variable distincte.</span><span class="sxs-lookup"><span data-stu-id="7e13f-252">Each element of a structure is initialized as if it were a separate variable.</span></span> <span data-ttu-id="7e13f-253">Si vous déclarez la longueur d’un tableau, mais ne pas initialisez ses éléments, chaque élément est initialisé comme s’il s’agissait d’une variable distincte.</span><span class="sxs-lookup"><span data-stu-id="7e13f-253">If you declare the length of an array but do not initialize its elements, each element is initialized as if it were a separate variable.</span></span>  
  
## <a name="static-local-variable-lifetime"></a><span data-ttu-id="7e13f-254">Durée de vie Variable locale statique</span><span class="sxs-lookup"><span data-stu-id="7e13f-254">Static Local Variable Lifetime</span></span>  
 <span data-ttu-id="7e13f-255">A `Static` variable locale a une durée de vie plus longue que celle de la procédure dans laquelle elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="7e13f-255">A `Static` local variable has a longer lifetime than that of the procedure in which it is declared.</span></span> <span data-ttu-id="7e13f-256">Les limites de durée de vie de la variable dépendent dans lequel la procédure est déclarée et s’il est `Shared`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-256">The boundaries of the variable's lifetime depend on where the procedure is declared and whether it is `Shared`.</span></span>  
  
|<span data-ttu-id="7e13f-257">Déclaration de procédure</span><span class="sxs-lookup"><span data-stu-id="7e13f-257">Procedure declaration</span></span>|<span data-ttu-id="7e13f-258">Variable initialisée</span><span class="sxs-lookup"><span data-stu-id="7e13f-258">Variable initialized</span></span>|<span data-ttu-id="7e13f-259">Variable n’existe plus.</span><span class="sxs-lookup"><span data-stu-id="7e13f-259">Variable stops existing</span></span>|  
|---|---|---|  
|<span data-ttu-id="7e13f-260">Dans un module</span><span class="sxs-lookup"><span data-stu-id="7e13f-260">In a module</span></span>|<span data-ttu-id="7e13f-261">La première fois que la procédure est appelée.</span><span class="sxs-lookup"><span data-stu-id="7e13f-261">The first time the procedure is called</span></span>|<span data-ttu-id="7e13f-262">Lorsque votre programme s’arrête l’exécution</span><span class="sxs-lookup"><span data-stu-id="7e13f-262">When your program stops execution</span></span>|  
|<span data-ttu-id="7e13f-263">Dans une classe ou structure, la procédure est`Shared`</span><span class="sxs-lookup"><span data-stu-id="7e13f-263">In a class or structure, procedure is `Shared`</span></span>|<span data-ttu-id="7e13f-264">La première fois que la procédure est appelée sur une instance spécifique ou sur la classe ou la structure elle-même</span><span class="sxs-lookup"><span data-stu-id="7e13f-264">The first time the procedure is called either on a specific instance or on the class or structure itself</span></span>|<span data-ttu-id="7e13f-265">Lorsque votre programme s’arrête l’exécution</span><span class="sxs-lookup"><span data-stu-id="7e13f-265">When your program stops execution</span></span>|  
|<span data-ttu-id="7e13f-266">Dans une classe ou structure, la procédure n’est pas`Shared`</span><span class="sxs-lookup"><span data-stu-id="7e13f-266">In a class or structure, procedure isn't `Shared`</span></span>|<span data-ttu-id="7e13f-267">La première fois que la procédure est appelée sur une instance spécifique</span><span class="sxs-lookup"><span data-stu-id="7e13f-267">The first time the procedure is called on a specific instance</span></span>|<span data-ttu-id="7e13f-268">Lorsque l’instance est libérée pour le garbage collection (GC)</span><span class="sxs-lookup"><span data-stu-id="7e13f-268">When the instance is released for garbage collection (GC)</span></span>|  
  
## <a name="attributes-and-modifiers"></a><span data-ttu-id="7e13f-269">Attributs et les modificateurs</span><span class="sxs-lookup"><span data-stu-id="7e13f-269">Attributes and Modifiers</span></span>  
 <span data-ttu-id="7e13f-270">Vous pouvez appliquer des attributs qu’aux variables membres, et non aux variables locales.</span><span class="sxs-lookup"><span data-stu-id="7e13f-270">You can apply attributes only to member variables, not to local variables.</span></span> <span data-ttu-id="7e13f-271">Un attribut fournit des informations aux métadonnées de l’assembly, qui n’est pas significatif pour le stockage temporaire tel que les variables locales.</span><span class="sxs-lookup"><span data-stu-id="7e13f-271">An attribute contributes information to the assembly's metadata, which is not meaningful for temporary storage such as local variables.</span></span>  
  
 <span data-ttu-id="7e13f-272">Au niveau du module, vous ne pouvez pas utiliser le `Static` modificateur pour déclarer des variables de membre.</span><span class="sxs-lookup"><span data-stu-id="7e13f-272">At module level, you cannot use the `Static` modifier to declare member variables.</span></span> <span data-ttu-id="7e13f-273">Au niveau de la procédure, vous ne pouvez pas utiliser `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, ou un modificateur d’accès pour déclarer des variables locales.</span><span class="sxs-lookup"><span data-stu-id="7e13f-273">At procedure level, you cannot use `Shared`, `Shadows`, `ReadOnly`, `WithEvents`, or any access modifiers to declare local variables.</span></span>  
  
 <span data-ttu-id="7e13f-274">Vous pouvez spécifier le code peut accéder à une variable en fournissant un `accessmodifier`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-274">You can specify what code can access a variable by supplying an `accessmodifier`.</span></span> <span data-ttu-id="7e13f-275">Classe et le module membre variables (en dehors de toute procédure) par défaut d’un accès privé et structure membre variables par défaut d’un accès public.</span><span class="sxs-lookup"><span data-stu-id="7e13f-275">Class and module member variables (outside any procedure) default to private access, and structure member variables default to public access.</span></span> <span data-ttu-id="7e13f-276">Vous pouvez régler leurs niveaux d’accès avec les modificateurs d’accès.</span><span class="sxs-lookup"><span data-stu-id="7e13f-276">You can adjust their access levels with the access modifiers.</span></span> <span data-ttu-id="7e13f-277">Vous ne pouvez pas utiliser les modificateurs d’accès sur les variables locales (à l’intérieur d’une procédure).</span><span class="sxs-lookup"><span data-stu-id="7e13f-277">You cannot use access modifiers on local variables (inside a procedure).</span></span>  
  
 <span data-ttu-id="7e13f-278">Vous pouvez spécifier `WithEvents` uniquement sur les variables membres, et non sur les variables locales à l’intérieur d’une procédure.</span><span class="sxs-lookup"><span data-stu-id="7e13f-278">You can specify `WithEvents` only on member variables, not on local variables inside a procedure.</span></span> <span data-ttu-id="7e13f-279">Si vous spécifiez `WithEvents`, le type de données de la variable doit être un type de classe spécifique, pas `Object`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-279">If you specify `WithEvents`, the data type of the variable must be a specific class type, not `Object`.</span></span> <span data-ttu-id="7e13f-280">Vous ne pouvez pas déclarer un tableau avec `WithEvents`.</span><span class="sxs-lookup"><span data-stu-id="7e13f-280">You cannot declare an array with `WithEvents`.</span></span> <span data-ttu-id="7e13f-281">Pour plus d’informations sur les événements, consultez la page [événements](../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-281">For more information about events, see [Events](../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e13f-282">Code à l’extérieur d’une classe, structure ou module doit qualifier le nom d’une variable membre avec le nom de cette classe, une structure ou un module.</span><span class="sxs-lookup"><span data-stu-id="7e13f-282">Code outside a class, structure, or module must qualify a member variable's name with the name of that class, structure, or module.</span></span> <span data-ttu-id="7e13f-283">Code en dehors de qu'une procédure ou un bloc ne peut pas faire référence à des variables locales de cette procédure ou un bloc.</span><span class="sxs-lookup"><span data-stu-id="7e13f-283">Code outside a procedure or block cannot refer to any local variables within that procedure or block.</span></span>  
  
## <a name="releasing-managed-resources"></a><span data-ttu-id="7e13f-284">Libération des ressources managées</span><span class="sxs-lookup"><span data-stu-id="7e13f-284">Releasing Managed Resources</span></span>  
 <span data-ttu-id="7e13f-285">Le garbage collector .NET Framework libère les ressources managées sans codage supplémentaire de votre part.</span><span class="sxs-lookup"><span data-stu-id="7e13f-285">The .NET Framework garbage collector disposes of managed resources without any extra coding on your part.</span></span> <span data-ttu-id="7e13f-286">Toutefois, vous pouvez forcer la suppression d’une ressource managée au lieu d’attendre le garbage collector.</span><span class="sxs-lookup"><span data-stu-id="7e13f-286">However, you can force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="7e13f-287">Si une classe conserve une ressource particulièrement précieuses et rares (par exemple, un handle de connexion ou un fichier de base de données), il pourrez que vous ne souhaitez pas attendre que le garbage collection suivant pour nettoyer une instance de classe qui n’est plus en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="7e13f-287">If a class holds onto a particularly valuable and scarce resource (such as a database connection or file handle), you might not want to wait until the next garbage collection to clean up a class instance that's no longer in use.</span></span> <span data-ttu-id="7e13f-288">Une classe peut implémenter la <xref:System.IDisposable>interface afin de fournir un moyen pour libérer des ressources avant un garbage collection.</xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="7e13f-288">A class may implement the <xref:System.IDisposable> interface to provide a way to release resources before a garbage collection.</span></span> <span data-ttu-id="7e13f-289">Une classe qui implémente cette interface expose un `Dispose` méthode qui peut être appelé pour le forcer à libérer immédiatement des ressources intéressantes.</span><span class="sxs-lookup"><span data-stu-id="7e13f-289">A class that implements that interface exposes a `Dispose` method that can be called to force valuable resources to be released immediately.</span></span>  
  
 <span data-ttu-id="7e13f-290">La `Using` instruction automatise le processus d’acquérir une ressource, l’exécution d’un ensemble d’instructions, puis suppression de la ressource.</span><span class="sxs-lookup"><span data-stu-id="7e13f-290">The `Using` statement automates the process of acquiring a resource, executing a set of statements, and then disposing of the resource.</span></span> <span data-ttu-id="7e13f-291">Toutefois, la ressource doit implémenter le <xref:System.IDisposable>interface.</xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="7e13f-291">However, the resource must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="7e13f-292">Pour plus d’informations, consultez [instruction à l’aide de](../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7e13f-292">For more information, see [Using Statement](../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e13f-293">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e13f-293">Example</span></span>  
 <span data-ttu-id="7e13f-294">L’exemple suivant déclare les variables à l’aide de la `Dim` instruction avec différentes options.</span><span class="sxs-lookup"><span data-stu-id="7e13f-294">The following example declares variables by using the `Dim` statement with various options.</span></span>  
  
 <span data-ttu-id="7e13f-295">[!code-vb[VbVbalrStatements&#141;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="7e13f-295">[!code-vb[VbVbalrStatements#141](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e13f-296">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e13f-296">Example</span></span>  
 <span data-ttu-id="7e13f-297">L’exemple suivant répertorie les nombres premiers entre 1 et 30.</span><span class="sxs-lookup"><span data-stu-id="7e13f-297">The following example lists the prime numbers between 1 and 30.</span></span> <span data-ttu-id="7e13f-298">La portée des variables locales est décrite dans les commentaires de code.</span><span class="sxs-lookup"><span data-stu-id="7e13f-298">The scope of local variables is described in code comments.</span></span>  
  
 <span data-ttu-id="7e13f-299">[!code-vb[VbVbalrStatements&#142;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="7e13f-299">[!code-vb[VbVbalrStatements#142](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_2.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e13f-300">Exemple</span><span class="sxs-lookup"><span data-stu-id="7e13f-300">Example</span></span>  
 <span data-ttu-id="7e13f-301">Dans l’exemple suivant, le `speedValue` variable est déclarée au niveau de la classe.</span><span class="sxs-lookup"><span data-stu-id="7e13f-301">In the following example, the `speedValue` variable is declared at the class level.</span></span> <span data-ttu-id="7e13f-302">Le `Private` mot clé est utilisé pour déclarer la variable.</span><span class="sxs-lookup"><span data-stu-id="7e13f-302">The `Private` keyword is used to declare the variable.</span></span> <span data-ttu-id="7e13f-303">La variable est accessible par n’importe quelle procédure la `Car` classe.</span><span class="sxs-lookup"><span data-stu-id="7e13f-303">The variable can be accessed by any procedure in the `Car` class.</span></span>  
  
 <span data-ttu-id="7e13f-304">[!code-vb[VbVbalrStatements&#144;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="7e13f-304">[!code-vb[VbVbalrStatements#144](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_3.vb)]</span></span>  
  
 <span data-ttu-id="7e13f-305">[!code-vb[VbVbalrStatements&#145;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="7e13f-305">[!code-vb[VbVbalrStatements#145](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/dim-statement_4.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e13f-306">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7e13f-306">See Also</span></span>  
 <span data-ttu-id="7e13f-307">[Const (instruction)](../../../visual-basic/language-reference/statements/const-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-307">[Const Statement](../../../visual-basic/language-reference/statements/const-statement.md) </span></span>  
<span data-ttu-id="7e13f-308"> [ReDim (instruction)](../../../visual-basic/language-reference/statements/redim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-308"> [ReDim Statement](../../../visual-basic/language-reference/statements/redim-statement.md) </span></span>  
<span data-ttu-id="7e13f-309"> [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-309"> [Option Explicit Statement](../../../visual-basic/language-reference/statements/option-explicit-statement.md) </span></span>  
<span data-ttu-id="7e13f-310"> [Instruction Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-310"> [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) </span></span>  
<span data-ttu-id="7e13f-311"> [Option Strict, instruction](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-311"> [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md) </span></span>  
<span data-ttu-id="7e13f-312"> [Page Compiler, Concepteur de projet (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="7e13f-312"> [Compile Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/compile-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="7e13f-313"> [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-313"> [Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md) </span></span>  
<span data-ttu-id="7e13f-314"> [Tableaux](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-314"> [Arrays](../../../visual-basic/programming-guide/language-features/arrays/index.md) </span></span>  
<span data-ttu-id="7e13f-315"> [Initialiseurs d’objets : Les Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-315"> [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="7e13f-316"> [Types anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-316"> [Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) </span></span>  
<span data-ttu-id="7e13f-317"> [Initialiseurs d’objets : Les Types nommés et anonymes](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-317"> [Object Initializers: Named and Anonymous Types](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md) </span></span>  
<span data-ttu-id="7e13f-318"> [Comment : déclarer un objet à l’aide d’un initialiseur d’objet](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md) </span><span class="sxs-lookup"><span data-stu-id="7e13f-318"> [How to: Declare an Object by Using an Object Initializer](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md) </span></span>  
<span data-ttu-id="7e13f-319"> [Inférence de type local](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span><span class="sxs-lookup"><span data-stu-id="7e13f-319"> [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)</span></span>

