---
title: Structures et Classes (Visual Basic) | Documents Microsoft
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
- classes [Visual Basic], vs. structures
- structures
- classes [Visual Basic]
- structures, compared to classes
- structures, structure variables
- structure variables
ms.assetid: a221e74a-ffcf-4bdc-a0f6-a088a9bf26cc
caps.latest.revision: 21
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
ms.openlocfilehash: c6874192a09db9ff5f247274247630d0bfa05ea3
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="structures-and-classes-visual-basic"></a><span data-ttu-id="5f614-102">Structures et classes (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f614-102">Structures and Classes (Visual Basic)</span></span>
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]<span data-ttu-id="5f614-103">unifie la syntaxe des structures et des classes, avec pour conséquence que les deux entités prennent en charge les mêmes fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="5f614-103"> unifies the syntax for structures and classes, with the result that both entities support most of the same features.</span></span> <span data-ttu-id="5f614-104">Toutefois, il existe également des différences importantes entre les classes et structures.</span><span class="sxs-lookup"><span data-stu-id="5f614-104">However, there are also important differences between structures and classes.</span></span>  
  
 <span data-ttu-id="5f614-105">Classes ont l’avantage d’être des types référence, en passant une référence est plus efficace de passer une variable de structure avec toutes ses données.</span><span class="sxs-lookup"><span data-stu-id="5f614-105">Classes have the advantage of being reference types — passing a reference is more efficient than passing a structure variable with all its data.</span></span> <span data-ttu-id="5f614-106">En revanche, les structures ne nécessitent pas l’allocation de mémoire sur le tas global.</span><span class="sxs-lookup"><span data-stu-id="5f614-106">On the other hand, structures do not require allocation of memory on the global heap.</span></span>  
  
 <span data-ttu-id="5f614-107">Car il ne peut pas hériter d’une structure, structures doivent être utilisées uniquement pour les objets qui ne doivent pas être étendu.</span><span class="sxs-lookup"><span data-stu-id="5f614-107">Because you cannot inherit from a structure, structures should be used only for objects that do not need to be extended.</span></span> <span data-ttu-id="5f614-108">Utilisez les structures lorsque l’objet que vous souhaitez créer a une taille d’instance réduite et prendre en compte les caractéristiques de performances des classes et structures.</span><span class="sxs-lookup"><span data-stu-id="5f614-108">Use structures when the object you wish to create has a small instance size, and take into account the performance characteristics of classes versus structures.</span></span>  
  
## <a name="similarities"></a><span data-ttu-id="5f614-109">Points communs</span><span class="sxs-lookup"><span data-stu-id="5f614-109">Similarities</span></span>  
 <span data-ttu-id="5f614-110">Les classes et les structures sont similaires aux points suivants :</span><span class="sxs-lookup"><span data-stu-id="5f614-110">Structures and classes are similar in the following respects:</span></span>  
  
-   <span data-ttu-id="5f614-111">Les deux sont *conteneur* types, ce qui signifie qu’ils contiennent d’autres types en tant que membres.</span><span class="sxs-lookup"><span data-stu-id="5f614-111">Both are *container* types, meaning that they contain other types as members.</span></span>  
  
-   <span data-ttu-id="5f614-112">Elles ont des membres comprenant des constructeurs, méthodes, propriétés, champs, des constantes, énumérations, événements et gestionnaires d’événements.</span><span class="sxs-lookup"><span data-stu-id="5f614-112">Both have members, which can include constructors, methods, properties, fields, constants, enumerations, events, and event handlers.</span></span> <span data-ttu-id="5f614-113">Toutefois, ne confondez pas ces membres avec les déclaré *éléments* d’une structure.</span><span class="sxs-lookup"><span data-stu-id="5f614-113">However, do not confuse these members with the declared *elements* of a structure.</span></span>  
  
-   <span data-ttu-id="5f614-114">Leurs membres peuvent avoir individualisée des niveaux d’accès.</span><span class="sxs-lookup"><span data-stu-id="5f614-114">Members of both can have individualized access levels.</span></span> <span data-ttu-id="5f614-115">Par exemple, un membre peut être déclaré `Public` et un autre `Private`.</span><span class="sxs-lookup"><span data-stu-id="5f614-115">For example, one member can be declared `Public` and another `Private`.</span></span>  
  
-   <span data-ttu-id="5f614-116">Les deux peuvent implémenter des interfaces.</span><span class="sxs-lookup"><span data-stu-id="5f614-116">Both can implement interfaces.</span></span>  
  
-   <span data-ttu-id="5f614-117">Les deux peuvent avoir des constructeurs partagés, avec ou sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="5f614-117">Both can have shared constructors, with or without parameters.</span></span>  
  
-   <span data-ttu-id="5f614-118">Elles peuvent exposer une *propriété par défaut*, sous réserve que la propriété prenne au moins un paramètre.</span><span class="sxs-lookup"><span data-stu-id="5f614-118">Both can expose a *default property*, provided that property takes at least one parameter.</span></span>  
  
-   <span data-ttu-id="5f614-119">Elles peuvent déclarer et déclencher des événements, et déclarer des délégués.</span><span class="sxs-lookup"><span data-stu-id="5f614-119">Both can declare and raise events, and both can declare delegates.</span></span>  
  
## <a name="differences"></a><span data-ttu-id="5f614-120">Différences</span><span class="sxs-lookup"><span data-stu-id="5f614-120">Differences</span></span>  
 <span data-ttu-id="5f614-121">Structures et classes diffèrent dans les indications suivantes :</span><span class="sxs-lookup"><span data-stu-id="5f614-121">Structures and classes differ in the following particulars:</span></span>  
  
-   <span data-ttu-id="5f614-122">Les structures sont *des types valeur*; les classes sont *types référence*.</span><span class="sxs-lookup"><span data-stu-id="5f614-122">Structures are *value types*; classes are *reference types*.</span></span> <span data-ttu-id="5f614-123">Une variable d’un type structure contient les données de la structure, plutôt que contenant une référence aux données comme un type de classe.</span><span class="sxs-lookup"><span data-stu-id="5f614-123">A variable of a structure type contains the structure's data, rather than containing a reference to the data as a class type does.</span></span>  
  
-   <span data-ttu-id="5f614-124">Les structures utilisent l’allocation de pile ; les classes utilisent l’allocation de tas.</span><span class="sxs-lookup"><span data-stu-id="5f614-124">Structures use stack allocation; classes use heap allocation.</span></span>  
  
-   <span data-ttu-id="5f614-125">Tous les éléments de structure sont `Public` par défaut ; classe variables et constantes sont `Private` par défaut, tandis que d’autres membres de classe sont `Public` par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f614-125">All structure elements are `Public` by default; class variables and constants are `Private` by default, while other class members are `Public` by default.</span></span> <span data-ttu-id="5f614-126">Ce comportement pour les membres de classe assure la compatibilité avec le système de Visual Basic 6.0 de valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f614-126">This behavior for class members provides compatibility with the Visual Basic 6.0 system of defaults.</span></span>  
  
-   <span data-ttu-id="5f614-127">Une structure doit contenir au moins un non partagé, ou variable non partagée élément d’événement ; une classe peut être entièrement vide.</span><span class="sxs-lookup"><span data-stu-id="5f614-127">A structure must have at least one nonshared variable or nonshared, noncustom event element; a class can be completely empty.</span></span>  
  
-   <span data-ttu-id="5f614-128">Éléments de structure ne peuvent pas être déclarés en tant que `Protected`; peuvent des membres de classe.</span><span class="sxs-lookup"><span data-stu-id="5f614-128">Structure elements cannot be declared as `Protected`; class members can.</span></span>  
  
-   <span data-ttu-id="5f614-129">Une procédure de structure peut gérer des événements uniquement s’il est un [partagé](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub` procédure et uniquement au moyen de la [AddHandler, instruction](../../../../visual-basic/language-reference/statements/addhandler-statement.md); toute procédure de classe peut gérer des événements à l’aide la [gère](../../../../visual-basic/language-reference/statements/handles-clause.md) (mot clé) ou le `AddHandler` instruction.</span><span class="sxs-lookup"><span data-stu-id="5f614-129">A structure procedure can handle events only if it is a [Shared](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub` procedure, and only by means of the [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md); any class procedure can handle events, using either the [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) keyword or the `AddHandler` statement.</span></span> <span data-ttu-id="5f614-130">Pour plus d’informations, consultez [événements](../../../../visual-basic/programming-guide/language-features/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="5f614-130">For more information, see [Events](../../../../visual-basic/programming-guide/language-features/events/index.md).</span></span>  
  
-   <span data-ttu-id="5f614-131">Les déclarations de variable de structure ne peut pas spécifier initialiseurs ni les tailles initiales des tableaux ; les déclarations de variable de classe peuvent.</span><span class="sxs-lookup"><span data-stu-id="5f614-131">Structure variable declarations cannot specify initializers or initial sizes for arrays; class variable declarations can.</span></span>  
  
-   <span data-ttu-id="5f614-132">Les structures héritent implicitement de la <xref:System.ValueType?displayProperty=fullName>classe et ne peut pas hériter d’un autre type ; classes peuvent hériter d’une classe ou d’une classe autre que <xref:System.ValueType?displayProperty=fullName>.</xref:System.ValueType?displayProperty=fullName> </xref:System.ValueType?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5f614-132">Structures implicitly inherit from the <xref:System.ValueType?displayProperty=fullName> class and cannot inherit from any other type; classes can inherit from any class or classes other than <xref:System.ValueType?displayProperty=fullName>.</span></span>  
  
-   <span data-ttu-id="5f614-133">Structures ne sont pas héritées ; les classes sont.</span><span class="sxs-lookup"><span data-stu-id="5f614-133">Structures are not inheritable; classes are.</span></span>  
  
-   <span data-ttu-id="5f614-134">Les structures n’étant jamais arrêtées, le common language runtime (CLR) n’appelle jamais la <xref:System.Object.Finalize%2A>méthode sur une structure ; les classes sont arrêtées par le garbage collector (GC), qui appelle <xref:System.Object.Finalize%2A>sur une classe lorsqu’il ne détecte aucune référence active restante.</xref:System.Object.Finalize%2A> </xref:System.Object.Finalize%2A></span><span class="sxs-lookup"><span data-stu-id="5f614-134">Structures are never terminated, so the common language runtime (CLR) never calls the <xref:System.Object.Finalize%2A> method on any structure; classes are terminated by the garbage collector (GC), which calls <xref:System.Object.Finalize%2A> on a class when it detects there are no active references remaining.</span></span>  
  
-   <span data-ttu-id="5f614-135">Une structure ne nécessite pas un constructeur ; une classe fait.</span><span class="sxs-lookup"><span data-stu-id="5f614-135">A structure does not require a constructor; a class does.</span></span>  
  
-   <span data-ttu-id="5f614-136">Les structures peuvent avoir des constructeurs non partagés uniquement lorsqu’ils acceptent des paramètres. classes peuvent avoir leur avec ou sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="5f614-136">Structures can have nonshared constructors only if they take parameters; classes can have them with or without parameters.</span></span>  
  
 <span data-ttu-id="5f614-137">Chaque structure possède un constructeur public implicite sans paramètres.</span><span class="sxs-lookup"><span data-stu-id="5f614-137">Every structure has an implicit public constructor without parameters.</span></span> <span data-ttu-id="5f614-138">Ce constructeur initialise les éléments de données de toute la structure à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="5f614-138">This constructor initializes all the structure's data elements to their default values.</span></span> <span data-ttu-id="5f614-139">Vous ne pouvez pas modifier ce comportement.</span><span class="sxs-lookup"><span data-stu-id="5f614-139">You cannot redefine this behavior.</span></span>  
  
## <a name="instances-and-variables"></a><span data-ttu-id="5f614-140">Instances et Variables</span><span class="sxs-lookup"><span data-stu-id="5f614-140">Instances and Variables</span></span>  
 <span data-ttu-id="5f614-141">Étant donné que les structures sont des types valeur, chaque variable de structure est définitivement liée à une instance de structure individuelle.</span><span class="sxs-lookup"><span data-stu-id="5f614-141">Because structures are value types, each structure variable is permanently bound to an individual structure instance.</span></span> <span data-ttu-id="5f614-142">Mais les classes sont des types référence, et une variable objet peut faire référence à plusieurs instances de classe à des moments différents.</span><span class="sxs-lookup"><span data-stu-id="5f614-142">But classes are reference types, and an object variable can refer to various class instances at different times.</span></span> <span data-ttu-id="5f614-143">Cette distinction affecte votre utilisation de structures et les classes de plusieurs façons :</span><span class="sxs-lookup"><span data-stu-id="5f614-143">This distinction affects your usage of structures and classes in the following ways:</span></span>  
  
-   <span data-ttu-id="5f614-144">**Initialisation.**</span><span class="sxs-lookup"><span data-stu-id="5f614-144">**Initialization.**</span></span> <span data-ttu-id="5f614-145">Une variable de structure comprend implicitement une initialisation des éléments à l’aide du constructeur sans paramètre de la structure.</span><span class="sxs-lookup"><span data-stu-id="5f614-145">A structure variable implicitly includes an initialization of the elements using the structure's parameterless constructor.</span></span> <span data-ttu-id="5f614-146">Par conséquent, `Dim s As struct1` équivaut à `Dim s As struct1 = New struct1()`.</span><span class="sxs-lookup"><span data-stu-id="5f614-146">Therefore, `Dim s As struct1` is equivalent to `Dim s As struct1 = New struct1()`.</span></span>  
  
-   <span data-ttu-id="5f614-147">**Assignation de Variables.**</span><span class="sxs-lookup"><span data-stu-id="5f614-147">**Assigning Variables.**</span></span> <span data-ttu-id="5f614-148">Lorsque vous assignez une variable de structure à une autre, ou passez une instance de structure à un argument de procédure, les valeurs actuelles de tous les éléments de variable sont copiés à la nouvelle structure.</span><span class="sxs-lookup"><span data-stu-id="5f614-148">When you assign one structure variable to another, or pass a structure instance to a procedure argument, the current values of all the variable elements are copied to the new structure.</span></span> <span data-ttu-id="5f614-149">Lorsque vous assignez une variable d’objet à un autre, ou passez une variable objet à une procédure, seul le pointeur de la référence est copié.</span><span class="sxs-lookup"><span data-stu-id="5f614-149">When you assign one object variable to another, or pass an object variable to a procedure, only the reference pointer is copied.</span></span>  
  
-   <span data-ttu-id="5f614-150">**Assignation de Nothing.**</span><span class="sxs-lookup"><span data-stu-id="5f614-150">**Assigning Nothing.**</span></span> <span data-ttu-id="5f614-151">Vous pouvez affecter la valeur [rien](../../../../visual-basic/language-reference/nothing.md) à une structure variable, mais l’instance continue à associer à la variable.</span><span class="sxs-lookup"><span data-stu-id="5f614-151">You can assign the value [Nothing](../../../../visual-basic/language-reference/nothing.md) to a structure variable, but the instance continues to be associated with the variable.</span></span> <span data-ttu-id="5f614-152">Vous pouvez toujours appeler ses méthodes et accéder à ses éléments de données, bien que les éléments de variable sont réinitialisés par l’assignation.</span><span class="sxs-lookup"><span data-stu-id="5f614-152">You can still call its methods and access its data elements, although variable elements are reinitialized by the assignment.</span></span>  
  
     <span data-ttu-id="5f614-153">En revanche, si vous définissez une variable objet à `Nothing`, vous lui assigniez à partir de n’importe quelle instance de classe et vous ne pouvez pas accéder aux membres via la variable jusqu'à ce que vous lui affectez une autre instance.</span><span class="sxs-lookup"><span data-stu-id="5f614-153">In contrast, if you set an object variable to `Nothing`, you dissociate it from any class instance, and you cannot access any members through the variable until you assign another instance to it.</span></span>  
  
-   <span data-ttu-id="5f614-154">**Plusieurs Instances.**</span><span class="sxs-lookup"><span data-stu-id="5f614-154">**Multiple Instances.**</span></span> <span data-ttu-id="5f614-155">Une variable objet peut avoir diverses instances de classe attribués à des moments différents, et plusieurs variables d’objet peuvent faire référence à la même instance de classe en même temps.</span><span class="sxs-lookup"><span data-stu-id="5f614-155">An object variable can have different class instances assigned to it at different times, and several object variables can refer to the same class instance at the same time.</span></span> <span data-ttu-id="5f614-156">Modifications apportées aux valeurs des membres de classe affectent ces membres lorsque pour accéder à une autre variable pointant vers la même instance.</span><span class="sxs-lookup"><span data-stu-id="5f614-156">Changes you make to the values of class members affect those members when accessed through another variable pointing to the same instance.</span></span>  
  
     <span data-ttu-id="5f614-157">Toutefois, les éléments de structure, sont isolés dans leur propre instance.</span><span class="sxs-lookup"><span data-stu-id="5f614-157">Structure elements, however, are isolated within their own instance.</span></span> <span data-ttu-id="5f614-158">Modifications apportées à leurs valeurs ne sont pas répercutées dans d’autres variables de structure, même dans les autres instances du même `Structure` déclaration.</span><span class="sxs-lookup"><span data-stu-id="5f614-158">Changes to their values are not reflected in any other structure variables, even in other instances of the same `Structure` declaration.</span></span>  
  
-   <span data-ttu-id="5f614-159">**Égalité.**</span><span class="sxs-lookup"><span data-stu-id="5f614-159">**Equality.**</span></span> <span data-ttu-id="5f614-160">Tester l’égalité de deux structures doit être effectué sur un élément par élément.</span><span class="sxs-lookup"><span data-stu-id="5f614-160">Equality testing of two structures must be performed with an element-by-element test.</span></span> <span data-ttu-id="5f614-161">Deux variables d’objet peuvent être comparées à l’aide de la <xref:System.Object.Equals%2A>méthode.</xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="5f614-161">Two object variables can be compared using the <xref:System.Object.Equals%2A> method.</span></span> <span data-ttu-id="5f614-162"><xref:System.Object.Equals%2A>Indique si les deux variables pointent vers la même instance.</xref:System.Object.Equals%2A></span><span class="sxs-lookup"><span data-stu-id="5f614-162"><xref:System.Object.Equals%2A> indicates whether the two variables point to the same instance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f614-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5f614-163">See Also</span></span>  
 <span data-ttu-id="5f614-164">[Types de données](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span><span class="sxs-lookup"><span data-stu-id="5f614-164">[Data Types](../../../../visual-basic/programming-guide/language-features/data-types/index.md) </span></span>  
<span data-ttu-id="5f614-165"> [Types de données composites](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="5f614-165"> [Composite Data Types](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) </span></span>  
<span data-ttu-id="5f614-166"> [Types valeur et Types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span><span class="sxs-lookup"><span data-stu-id="5f614-166"> [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md) </span></span>  
<span data-ttu-id="5f614-167"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span><span class="sxs-lookup"><span data-stu-id="5f614-167"> [Structures](../../../../visual-basic/programming-guide/language-features/data-types/structures.md) </span></span>  
<span data-ttu-id="5f614-168"> [Dépannage des Types de données](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span><span class="sxs-lookup"><span data-stu-id="5f614-168"> [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md) </span></span>  
<span data-ttu-id="5f614-169"> [Structures et autres éléments de programmation](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span><span class="sxs-lookup"><span data-stu-id="5f614-169"> [Structures and Other Programming Elements](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md) </span></span>  
<span data-ttu-id="5f614-170"> [Objets et classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span><span class="sxs-lookup"><span data-stu-id="5f614-170"> [Objects and Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)</span></span>
