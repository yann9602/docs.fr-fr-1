---
title: "Déclaration de variable en Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic], declaring
- member variables, declarations
- Dim statement, variable declaration
- declaring variables
- variables [Visual Basic], scope
- variables [Visual Basic], data types
- data types [Visual Basic], variable declarations
- lifetime, variables
- variables [Visual Basic], lifetime
- access levels, variables
- scope, declaration statements
- variables [Visual Basic], access level
- local variables, declarations
- scope, variables
ms.assetid: d8f10226-92b1-480f-9f53-df377b2d7e15
caps.latest.revision: 31
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: dac536b99eb4515c75381dc4e28720a92e1001f0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="variable-declaration-in-visual-basic"></a><span data-ttu-id="ab9db-102">Déclaration de variable en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab9db-102">Variable Declaration in Visual Basic</span></span>
<span data-ttu-id="ab9db-103">Vous déclarez une variable pour spécifier son nom et sa configuration.</span><span class="sxs-lookup"><span data-stu-id="ab9db-103">You declare a variable to specify its name and characteristics.</span></span> <span data-ttu-id="ab9db-104">L’instruction de déclaration de variables est la [une instruction Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab9db-104">The declaration statement for variables is the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md).</span></span> <span data-ttu-id="ab9db-105">Son emplacement et son contenu déterminent les caractéristiques de la variable.</span><span class="sxs-lookup"><span data-stu-id="ab9db-105">Its location and contents determine the variable's characteristics.</span></span>  
  
 <span data-ttu-id="ab9db-106">Pour les règles d’affectation de noms de variable et les considérations, consultez [noms d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="ab9db-106">For variable naming rules and considerations, see [Declared Element Names](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="declaration-levels"></a><span data-ttu-id="ab9db-107">Niveaux de déclaration</span><span class="sxs-lookup"><span data-stu-id="ab9db-107">Declaration Levels</span></span>  
  
### <a name="local-and-member-variables"></a><span data-ttu-id="ab9db-108">Local et les Variables de membre</span><span class="sxs-lookup"><span data-stu-id="ab9db-108">Local and Member Variables</span></span>  
 <span data-ttu-id="ab9db-109">A *variable locale* est celle qui est déclarée dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="ab9db-109">A *local variable* is one that is declared within a procedure.</span></span> <span data-ttu-id="ab9db-110">A *variable membre* est un membre d’un [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] type ; elle est déclarée au niveau du module, à l’intérieur d’une classe, une structure ou un module, mais pas dans une procédure interne à cette classe, une structure ou un module.</span><span class="sxs-lookup"><span data-stu-id="ab9db-110">A *member variable* is a member of a [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] type; it is declared at module level, inside a class, structure, or module, but not within any procedure internal to that class, structure, or module.</span></span>  
  
### <a name="shared-and-instance-variables"></a><span data-ttu-id="ab9db-111">Instance et Variables partagées</span><span class="sxs-lookup"><span data-stu-id="ab9db-111">Shared and Instance Variables</span></span>  
 <span data-ttu-id="ab9db-112">Dans une classe ou structure, la catégorie d’une variable membre dépend d’elle est partagée ou non.</span><span class="sxs-lookup"><span data-stu-id="ab9db-112">In a class or structure, the category of a member variable depends on whether or not it is shared.</span></span> <span data-ttu-id="ab9db-113">Si elle est déclarée avec le [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) (mot clé), il est un *variable partagée*, et il existe une seule copie partagée entre toutes les instances de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="ab9db-113">If it is declared with the [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) keyword, it is a *shared variable*, and it exists in a single copy shared among all instances of the class or structure.</span></span>  
  
 <span data-ttu-id="ab9db-114">Sinon, il est un *variable d’instance*, et une copie séparée est créée pour chaque instance de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="ab9db-114">Otherwise it is an *instance variable*, and a separate copy of it is created for each instance of the class or structure.</span></span> <span data-ttu-id="ab9db-115">Une copie d’une variable d’instance donnée est disponible uniquement à l’instance de la classe ou la structure dans laquelle elle a été créée.</span><span class="sxs-lookup"><span data-stu-id="ab9db-115">A given copy of an instance variable is available only to the instance of the class or structure in which it was created.</span></span> <span data-ttu-id="ab9db-116">Elle est indépendante d’une copie de la variable d’instance dans une autre instance de la classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="ab9db-116">It is independent of a copy of the instance variable in any other instance of the class or structure.</span></span>  
  
## <a name="declaring-data-type"></a><span data-ttu-id="ab9db-117">Déclaration de Type de données</span><span class="sxs-lookup"><span data-stu-id="ab9db-117">Declaring Data Type</span></span>  
 <span data-ttu-id="ab9db-118">Le [comme](../../../../visual-basic/language-reference/statements/as-clause.md) clause dans l’instruction de déclaration vous permet de définir le type de données ou le type d’objet de la variable que vous déclarez.</span><span class="sxs-lookup"><span data-stu-id="ab9db-118">The [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause in the declaration statement allows you to define the data type or object type of the variable you are declaring.</span></span> <span data-ttu-id="ab9db-119">Vous pouvez spécifier les types suivants d’une variable :</span><span class="sxs-lookup"><span data-stu-id="ab9db-119">You can specify any of the following types for a variable:</span></span>  
  
-   <span data-ttu-id="ab9db-120">Type de données élémentaire, tel que `Boolean`, `Long`, ou`Decimal`</span><span class="sxs-lookup"><span data-stu-id="ab9db-120">An elementary data type, such as `Boolean`, `Long`, or `Decimal`</span></span>  
  
-   <span data-ttu-id="ab9db-121">Type de données composite, tel qu’un tableau ou une structure</span><span class="sxs-lookup"><span data-stu-id="ab9db-121">A composite data type, such as an array or structure</span></span>  
  
-   <span data-ttu-id="ab9db-122">Type d’objet, ou classe, défini dans votre application ou dans une autre application</span><span class="sxs-lookup"><span data-stu-id="ab9db-122">An object type, or class, defined either in your application or in another application</span></span>  
  
-   <span data-ttu-id="ab9db-123">A [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] classe, telle que <xref:System.Windows.Forms.Label>ou <xref:System.Windows.Forms.TextBox></xref:System.Windows.Forms.TextBox> </xref:System.Windows.Forms.Label></span><span class="sxs-lookup"><span data-stu-id="ab9db-123">A [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] class, such as <xref:System.Windows.Forms.Label> or <xref:System.Windows.Forms.TextBox></span></span>  
  
-   <span data-ttu-id="ab9db-124">Type d’interface, tel que <xref:System.IComparable>ou <xref:System.IDisposable></xref:System.IDisposable> </xref:System.IComparable></span><span class="sxs-lookup"><span data-stu-id="ab9db-124">An interface type, such as <xref:System.IComparable> or <xref:System.IDisposable></span></span>  
  
 <span data-ttu-id="ab9db-125">Vous pouvez déclarer plusieurs variables dans une instruction sans devoir répéter le type de données.</span><span class="sxs-lookup"><span data-stu-id="ab9db-125">You can declare several variables in one statement without having to repeat the data type.</span></span> <span data-ttu-id="ab9db-126">Dans les instructions suivantes, les variables `i`, `j`, et `k` sont déclarées en tant que type `Integer`, `l` et `m` en tant que `Long`, et `x` et `y` comme `Single`:</span><span class="sxs-lookup"><span data-stu-id="ab9db-126">In the following statements, the variables `i`, `j`, and `k` are declared as type `Integer`, `l` and `m` as `Long`, and `x` and `y` as `Single`:</span></span>  
  
```  
Dim i, j, k As Integer  
' All three variables in the preceding statement are declared as Integer.  
Dim l, m As Long, x, y As Single  
' In the preceding statement, l and m are Long, x and y are Single.  
```  
  
 <span data-ttu-id="ab9db-127">Pour plus d’informations sur les types de données, consultez la page [des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="ab9db-127">For more information on data types, see [Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md).</span></span> <span data-ttu-id="ab9db-128">Pour plus d’informations sur les objets, consultez [objets et Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) et [programmation avec des composants](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span><span class="sxs-lookup"><span data-stu-id="ab9db-128">For more information on objects, see [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) and [Programming with Components](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3).</span></span>  
  
## <a name="local-type-inference"></a><span data-ttu-id="ab9db-129">Inférence de type local</span><span class="sxs-lookup"><span data-stu-id="ab9db-129">Local Type Inference</span></span>  
 <span data-ttu-id="ab9db-130">*L’inférence de type* est utilisé pour déterminer les types de données des variables locales déclarées sans un `As` clause.</span><span class="sxs-lookup"><span data-stu-id="ab9db-130">*Type inference* is used to determine the data types of local variables declared without an `As` clause.</span></span> <span data-ttu-id="ab9db-131">Le compilateur déduit le type de la variable du type de l’expression d’initialisation.</span><span class="sxs-lookup"><span data-stu-id="ab9db-131">The compiler infers the type of the variable from the type of the initialization expression.</span></span> <span data-ttu-id="ab9db-132">Cela vous permet de déclarer des variables sans déclarer explicitement un type.</span><span class="sxs-lookup"><span data-stu-id="ab9db-132">This enables you to declare variables without explicitly stating a type.</span></span> <span data-ttu-id="ab9db-133">Dans l’exemple suivant, les deux `num1` et `num2` sont fortement typés comme entiers.</span><span class="sxs-lookup"><span data-stu-id="ab9db-133">In the following example, both `num1` and `num2` are strongly typed as integers.</span></span>  
  
 <span data-ttu-id="ab9db-134">[!code-vb[VbVbalrTypeInference n °&1;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ab9db-134">[!code-vb[VbVbalrTypeInference#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/variable-declaration_1.vb)]</span></span>  
  
 <span data-ttu-id="ab9db-135">Si vous souhaitez utiliser l’inférence de type local, `Option Infer` doit avoir la valeur `On`.</span><span class="sxs-lookup"><span data-stu-id="ab9db-135">If you want to use local type inference, `Option Infer` must be set to `On`.</span></span> <span data-ttu-id="ab9db-136">Pour plus d’informations, consultez [l’inférence de Type Local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) et [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ab9db-136">For more information, see [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) and [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md).</span></span>  
  
## <a name="characteristics-of-declared-variables"></a><span data-ttu-id="ab9db-137">Caractéristiques des Variables déclarées</span><span class="sxs-lookup"><span data-stu-id="ab9db-137">Characteristics of Declared Variables</span></span>  
 <span data-ttu-id="ab9db-138">Le *durée de vie* d’une variable est la période pendant laquelle il est disponible pour utilisation.</span><span class="sxs-lookup"><span data-stu-id="ab9db-138">The *lifetime* of a variable is the period of time during which it is available for use.</span></span> <span data-ttu-id="ab9db-139">En règle générale, une variable existe tant que l’élément qui le déclare (par exemple, une procédure ou une classe) continue d’exister.</span><span class="sxs-lookup"><span data-stu-id="ab9db-139">In general, a variable exists as long as the element that declares it (such as a procedure or class) continues to exist.</span></span> <span data-ttu-id="ab9db-140">Si la variable n’a pas besoin excède la durée de vie de son élément conteneur, il est inutile d’opération spécifique dans la déclaration.</span><span class="sxs-lookup"><span data-stu-id="ab9db-140">If the variable does not need to continue existing beyond the lifetime of its containing element, you do not need to do anything special in the declaration.</span></span> <span data-ttu-id="ab9db-141">Si la variable doit continuer d’exister plus longtemps que son élément conteneur, vous pouvez inclure le `Static` ou `Shared` mot clé dans son `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="ab9db-141">If the variable needs to continue to exist longer than its containing element, you can include the `Static` or `Shared` keyword in its `Dim` statement.</span></span> <span data-ttu-id="ab9db-142">Pour plus d’informations, consultez [durée de vie dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span><span class="sxs-lookup"><span data-stu-id="ab9db-142">For more information, see [Lifetime in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md).</span></span>  
  
 <span data-ttu-id="ab9db-143">Le *étendue* d’une variable est l’ensemble du code que vous pouvez vous y référer sans qualifier son nom.</span><span class="sxs-lookup"><span data-stu-id="ab9db-143">The *scope* of a variable is the set of all code that can refer to it without qualifying its name.</span></span> <span data-ttu-id="ab9db-144">La portée d’une variable est déterminée par l’endroit où elle est déclarée.</span><span class="sxs-lookup"><span data-stu-id="ab9db-144">A variable's scope is determined by where it is declared.</span></span> <span data-ttu-id="ab9db-145">Le code situé dans une région donnée peut utiliser les variables définies dans cette zone sans devoir qualifier leurs noms.</span><span class="sxs-lookup"><span data-stu-id="ab9db-145">Code located in a given region can use the variables defined in that region without having to qualify their names.</span></span> <span data-ttu-id="ab9db-146">Pour plus d’informations, consultez [portée dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span><span class="sxs-lookup"><span data-stu-id="ab9db-146">For more information, see [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).</span></span>  
  
 <span data-ttu-id="ab9db-147">D’une variable *niveau d’accès* est l’étendue de code qui a l’autorisation d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="ab9db-147">A variable's *access level* is the extent of code that has permission to access it.</span></span> <span data-ttu-id="ab9db-148">Cela est déterminé par le modificateur d’accès (tel que [Public](../../../../visual-basic/language-reference/modifiers/public.md) ou [privé](../../../../visual-basic/language-reference/modifiers/private.md)) que vous utilisez dans la `Dim` instruction.</span><span class="sxs-lookup"><span data-stu-id="ab9db-148">This is determined by the access modifier (such as [Public](../../../../visual-basic/language-reference/modifiers/public.md) or [Private](../../../../visual-basic/language-reference/modifiers/private.md)) that you use in the `Dim` statement.</span></span> <span data-ttu-id="ab9db-149">Pour plus d’informations, consultez [niveaux d’accès dans Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ab9db-149">For more information, see [Access Levels in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9db-150">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab9db-150">See Also</span></span>  
 <span data-ttu-id="ab9db-151">[Comment : créer une Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md) </span><span class="sxs-lookup"><span data-stu-id="ab9db-151">[How to: Create a New Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md) </span></span>  
<span data-ttu-id="ab9db-152"> [Comment : déplacer des données dans et hors d’une Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span><span class="sxs-lookup"><span data-stu-id="ab9db-152"> [How to: Move Data Into and Out of a Variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md) </span></span>  
<span data-ttu-id="ab9db-153"> [Types de données](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span><span class="sxs-lookup"><span data-stu-id="ab9db-153"> [Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md) </span></span>  
<span data-ttu-id="ab9db-154"> [Protégé par](../../../../visual-basic/language-reference/modifiers/protected.md) </span><span class="sxs-lookup"><span data-stu-id="ab9db-154"> [Protected](../../../../visual-basic/language-reference/modifiers/protected.md) </span></span>  
<span data-ttu-id="ab9db-155"> [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) </span><span class="sxs-lookup"><span data-stu-id="ab9db-155"> [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) </span></span>  
<span data-ttu-id="ab9db-156"> [Statique](../../../../visual-basic/language-reference/modifiers/static.md) </span><span class="sxs-lookup"><span data-stu-id="ab9db-156"> [Static](../../../../visual-basic/language-reference/modifiers/static.md) </span></span>  
<span data-ttu-id="ab9db-157"> [Caractéristiques d’éléments déclarés](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span><span class="sxs-lookup"><span data-stu-id="ab9db-157"> [Declared Element Characteristics](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md) </span></span>  
<span data-ttu-id="ab9db-158"> [Inférence de Type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span><span class="sxs-lookup"><span data-stu-id="ab9db-158"> [Local Type Inference](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) </span></span>  
<span data-ttu-id="ab9db-159"> [Option Infer (instruction)](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span><span class="sxs-lookup"><span data-stu-id="ab9db-159"> [Option Infer Statement](../../../../visual-basic/language-reference/statements/option-infer-statement.md)</span></span>
