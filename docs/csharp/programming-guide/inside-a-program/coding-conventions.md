---
title: Conventions de codage C# (Guide de programmation C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- coding conventions, C#
- Visual C#, coding conventions
- C# language, coding conventions
ms.assetid: f4f60de9-d49b-4fb6-bab1-20e19ea24710
caps.latest.revision: "32"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84ddc2b3cebb6bad95f5076889de11f12624b4de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="c-coding-conventions-c-programming-guide"></a><span data-ttu-id="cbee8-102">Conventions de codage C# (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="cbee8-102">C# Coding Conventions (C# Programming Guide)</span></span>
<span data-ttu-id="cbee8-103">La [spécification du langage C#](http://go.microsoft.com/fwlink/?LinkId=199552) ne définit pas une norme de codage.</span><span class="sxs-lookup"><span data-stu-id="cbee8-103">The [C# Language Specification](http://go.microsoft.com/fwlink/?LinkId=199552) does not define a coding standard.</span></span> <span data-ttu-id="cbee8-104">Toutefois, les instructions de cette rubrique sont utilisées par Microsoft pour développer les exemples et la documentation.</span><span class="sxs-lookup"><span data-stu-id="cbee8-104">However, the guidelines in this topic are used by Microsoft to develop samples and documentation.</span></span>  
  
 <span data-ttu-id="cbee8-105">Les conventions de codage répondent aux objectifs suivants :</span><span class="sxs-lookup"><span data-stu-id="cbee8-105">Coding conventions serve the following purposes:</span></span>  
  
-   <span data-ttu-id="cbee8-106">Elles confèrent une apparence cohérente au code, afin que les lecteurs puissent se concentrer sur le contenu, pas sur la disposition.</span><span class="sxs-lookup"><span data-stu-id="cbee8-106">They create a consistent look to the code, so that readers can focus on content, not layout.</span></span>  
  
-   <span data-ttu-id="cbee8-107">Elles permettent aux lecteurs de comprendre le code plus rapidement en formulant des hypothèses selon leur expérience antérieure.</span><span class="sxs-lookup"><span data-stu-id="cbee8-107">They enable readers to understand the code more quickly by making assumptions based on previous experience.</span></span>  
  
-   <span data-ttu-id="cbee8-108">Elles facilitent la copie, la modification et la gestion du code.</span><span class="sxs-lookup"><span data-stu-id="cbee8-108">They facilitate copying, changing, and maintaining the code.</span></span>  
  
-   <span data-ttu-id="cbee8-109">Elles illustrent les bonnes pratiques en C#.</span><span class="sxs-lookup"><span data-stu-id="cbee8-109">They demonstrate C# best practices.</span></span>  
  
## <a name="naming-conventions"></a><span data-ttu-id="cbee8-110">Conventions d'affectation de noms</span><span class="sxs-lookup"><span data-stu-id="cbee8-110">Naming Conventions</span></span>  
  
-   <span data-ttu-id="cbee8-111">Dans les exemples courts qui ne comprennent pas de [directives](../../../csharp/language-reference/keywords/using-directive.md), utilisez les qualifications d’espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cbee8-111">In short examples that do not include [using directives](../../../csharp/language-reference/keywords/using-directive.md), use namespace qualifications.</span></span> <span data-ttu-id="cbee8-112">Si vous savez qu'un espace de noms est importé par défaut dans un projet, vous n'êtes pas obligé de qualifier entièrement les noms à partir de cet espace de noms.</span><span class="sxs-lookup"><span data-stu-id="cbee8-112">If you know that a namespace is imported by default in a project, you do not have to fully qualify the names from that namespace.</span></span> <span data-ttu-id="cbee8-113">Les noms qualifiés peuvent être interrompus après un point (.) s'ils sont trop longs pour contenir sur une ligne unique, comme indiqué dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cbee8-113">Qualified names can be broken after a dot (.) if they are too long for a single line, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#1](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#1)]  
  
-   <span data-ttu-id="cbee8-114">Vous n'avez pas à modifier les noms des objets qui ont été créés à l'aide des outils du concepteur Visual Studio pour les rendre conformes aux autres directives.</span><span class="sxs-lookup"><span data-stu-id="cbee8-114">You do not have to change the names of objects that were created by using the Visual Studio designer tools to make them fit other guidelines.</span></span>  
  
## <a name="layout-conventions"></a><span data-ttu-id="cbee8-115">Conventions de disposition</span><span class="sxs-lookup"><span data-stu-id="cbee8-115">Layout Conventions</span></span>  
 <span data-ttu-id="cbee8-116">Une bonne disposition utilise la mise en forme pour souligner la structure de votre code et en faciliter la lecture.</span><span class="sxs-lookup"><span data-stu-id="cbee8-116">Good layout uses formatting to emphasize the structure of your code and to make the code easier to read.</span></span> <span data-ttu-id="cbee8-117">Les exemples Microsoft et autres se conforment aux conventions suivantes :</span><span class="sxs-lookup"><span data-stu-id="cbee8-117">Microsoft examples and samples conform to the following conventions:</span></span>  
  
-   <span data-ttu-id="cbee8-118">Utilisez les paramètres par défaut de l'éditeur de code (retrait intelligent, retrait de quatre caractères, tabulations enregistrées en tant qu'espaces).</span><span class="sxs-lookup"><span data-stu-id="cbee8-118">Use the default Code Editor settings (smart indenting, four-character indents, tabs saved as spaces).</span></span> <span data-ttu-id="cbee8-119">Pour plus d’informations, consultez [Options, Éditeur de texte, C#, Mise en forme](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span><span class="sxs-lookup"><span data-stu-id="cbee8-119">For more information, see [Options, Text Editor, C#, Formatting](/visualstudio/ide/reference/options-text-editor-csharp-formatting).</span></span>  
  
-   <span data-ttu-id="cbee8-120">Écrivez une seule instruction par ligne.</span><span class="sxs-lookup"><span data-stu-id="cbee8-120">Write only one statement per line.</span></span>  
  
-   <span data-ttu-id="cbee8-121">Écrivez une seule déclaration par ligne.</span><span class="sxs-lookup"><span data-stu-id="cbee8-121">Write only one declaration per line.</span></span>  
  
-   <span data-ttu-id="cbee8-122">Si les lignes de continuation ne sont pas mises en retrait automatiquement, indentez-les à l'aide d'un taquet de tabulation (quatre espaces).</span><span class="sxs-lookup"><span data-stu-id="cbee8-122">If continuation lines are not indented automatically, indent them one tab stop (four spaces).</span></span>  
  
-   <span data-ttu-id="cbee8-123">Ajoutez au moins une ligne blanche entre les définitions des méthodes et les définitions des propriétés.</span><span class="sxs-lookup"><span data-stu-id="cbee8-123">Add at least one blank line between method definitions and property definitions.</span></span>  
  
-   <span data-ttu-id="cbee8-124">Utilisez des parenthèses pour rendre apparentes les clauses d'une expression, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="cbee8-124">Use parentheses to make clauses in an expression apparent, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#2](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#2)]  
  
## <a name="commenting-conventions"></a><span data-ttu-id="cbee8-125">Conventions de commentaires</span><span class="sxs-lookup"><span data-stu-id="cbee8-125">Commenting Conventions</span></span>  
  
-   <span data-ttu-id="cbee8-126">Placez le commentaire sur une ligne séparée, pas à la fin d'une ligne de code.</span><span class="sxs-lookup"><span data-stu-id="cbee8-126">Place the comment on a separate line, not at the end of a line of code.</span></span>  
  
-   <span data-ttu-id="cbee8-127">Commencez le commentaire par une lettre majuscule.</span><span class="sxs-lookup"><span data-stu-id="cbee8-127">Begin comment text with an uppercase letter.</span></span>  
  
-   <span data-ttu-id="cbee8-128">Terminez le texte de commentaire par un point.</span><span class="sxs-lookup"><span data-stu-id="cbee8-128">End comment text with a period.</span></span>  
  
-   <span data-ttu-id="cbee8-129">Insérez un espace entre le délimiteur de commentaire (//) et le texte du commentaire, comme illustré dans l'exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cbee8-129">Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#3](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#3)]  
  
-   <span data-ttu-id="cbee8-130">Ne créez pas de blocs d'astérisques mis en forme autour des commentaires.</span><span class="sxs-lookup"><span data-stu-id="cbee8-130">Do not create formatted blocks of asterisks around comments.</span></span>  
  
## <a name="language-guidelines"></a><span data-ttu-id="cbee8-131">Directives du langage</span><span class="sxs-lookup"><span data-stu-id="cbee8-131">Language Guidelines</span></span>  
 <span data-ttu-id="cbee8-132">Les sections suivantes décrivent les pratiques que l'équipe C# suit pour préparer les exemples de code et autres.</span><span class="sxs-lookup"><span data-stu-id="cbee8-132">The following sections describe practices that the C# team follows to prepare code examples and samples.</span></span>  
  
### <a name="string-data-type"></a><span data-ttu-id="cbee8-133">String, type de données</span><span class="sxs-lookup"><span data-stu-id="cbee8-133">String Data Type</span></span>  
  
-   <span data-ttu-id="cbee8-134">Utilisez l'opérateur `+` pour concaténer les chaînes courtes, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="cbee8-134">Use the `+` operator to concatenate short strings, as shown in the following code.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#6](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#6)]  
  
-   <span data-ttu-id="cbee8-135">Pour ajouter des chaînes dans des boucles, en particulier lorsque vous travaillez avec une quantité de texte importante, utilisez un objet <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="cbee8-135">To append strings in loops, especially when you are working with large amounts of text, use a <xref:System.Text.StringBuilder> object.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#7](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#7)]  
  
### <a name="implicitly-typed-local-variables"></a><span data-ttu-id="cbee8-136">Variables locales implicitement typées</span><span class="sxs-lookup"><span data-stu-id="cbee8-136">Implicitly Typed Local Variables</span></span>  
  
-   <span data-ttu-id="cbee8-137">Utilisez le [typage implicite](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) pour les variables locales quand le type de la variable est évident à droite de l’assignation ou quand le type précis n’importe pas.</span><span class="sxs-lookup"><span data-stu-id="cbee8-137">Use [implicit typing](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#8](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#8)]  
  
-   <span data-ttu-id="cbee8-138">N’utilisez pas [var](../../../csharp/language-reference/keywords/var.md) quand le type n’est pas apparent à droite de l’assignation.</span><span class="sxs-lookup"><span data-stu-id="cbee8-138">Do not use [var](../../../csharp/language-reference/keywords/var.md) when the type is not apparent from the right side of the assignment.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#9](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#9)]  
  
-   <span data-ttu-id="cbee8-139">Ne vous basez pas sur le nom de la variable pour spécifier son type.</span><span class="sxs-lookup"><span data-stu-id="cbee8-139">Do not rely on the variable name to specify the type of the variable.</span></span> <span data-ttu-id="cbee8-140">Il peut ne pas être correct.</span><span class="sxs-lookup"><span data-stu-id="cbee8-140">It might not be correct.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#10](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#10)]  
  
-   <span data-ttu-id="cbee8-141">Évitez d’utiliser `var` à la place de [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span><span class="sxs-lookup"><span data-stu-id="cbee8-141">Avoid the use of `var` in place of [dynamic](../../../csharp/language-reference/keywords/dynamic.md).</span></span>  
  
-   <span data-ttu-id="cbee8-142">Utilisez le typage implicite pour déterminer le type de la variable de boucle dans les boucles [for](../../../csharp/language-reference/keywords/for.md) et [foreach](../../../csharp/language-reference/keywords/foreach-in.md).</span><span class="sxs-lookup"><span data-stu-id="cbee8-142">Use implicit typing to determine the type of the loop variable in [for](../../../csharp/language-reference/keywords/for.md) and [foreach](../../../csharp/language-reference/keywords/foreach-in.md) loops.</span></span>  
  
     <span data-ttu-id="cbee8-143">L'exemple suivant utilise un typage implicite dans une instruction `for`.</span><span class="sxs-lookup"><span data-stu-id="cbee8-143">The following example uses implicit typing in a `for` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#11](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#11)]  
  
     <span data-ttu-id="cbee8-144">L'exemple suivant utilise un typage implicite dans une instruction `foreach`.</span><span class="sxs-lookup"><span data-stu-id="cbee8-144">The following example uses implicit typing in a `foreach` statement.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#12](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#12)]  
  
### <a name="unsigned-data-type"></a><span data-ttu-id="cbee8-145">Type de données non signé</span><span class="sxs-lookup"><span data-stu-id="cbee8-145">Unsigned Data Type</span></span>  
  
-   <span data-ttu-id="cbee8-146">En règle générale, utilisez `int` plutôt que les types non signés.</span><span class="sxs-lookup"><span data-stu-id="cbee8-146">In general, use `int` rather than unsigned types.</span></span> <span data-ttu-id="cbee8-147">L'utilisation de `int` est commun en C# et il est plus facile d'interagir avec d'autres bibliothèques lorsque vous utilisez `int`.</span><span class="sxs-lookup"><span data-stu-id="cbee8-147">The use of `int` is common throughout C#, and it is easier to interact with other libraries when you use `int`.</span></span>  
  
### <a name="arrays"></a><span data-ttu-id="cbee8-148">Tableaux</span><span class="sxs-lookup"><span data-stu-id="cbee8-148">Arrays</span></span>  
  
-   <span data-ttu-id="cbee8-149">Utilisez la syntaxe concise lorsque vous initialisez des tableaux sur la ligne de déclaration.</span><span class="sxs-lookup"><span data-stu-id="cbee8-149">Use the concise syntax when you initialize arrays on the declaration line.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#13](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#13)]  
  
### <a name="delegates"></a><span data-ttu-id="cbee8-150">Délégués</span><span class="sxs-lookup"><span data-stu-id="cbee8-150">Delegates</span></span>  
  
-   <span data-ttu-id="cbee8-151">Utilisez la syntaxe concise pour créer des instances d'un type délégué.</span><span class="sxs-lookup"><span data-stu-id="cbee8-151">Use the concise syntax to create instances of a delegate type.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#14](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#14)]  
  
     [!code-csharp[csProgGuideCodingConventions#15](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#15)]  
  
### <a name="try-catch-and-using-statements-in-exception-handling"></a><span data-ttu-id="cbee8-152">Instructions try-catch et using dans la gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="cbee8-152">try-catch and using Statements in Exception Handling</span></span>  
  
-   <span data-ttu-id="cbee8-153">Utilisez une instruction [try-catch](../../../csharp/language-reference/keywords/try-catch.md) pour la plus grande part de la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="cbee8-153">Use a [try-catch](../../../csharp/language-reference/keywords/try-catch.md) statement for most exception handling.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#16](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#16)]  
  
-   <span data-ttu-id="cbee8-154">Simplifiez votre code à l’aide de l’instruction [using](../../../csharp/language-reference/keywords/using-statement.md) C#.</span><span class="sxs-lookup"><span data-stu-id="cbee8-154">Simplify your code by using the C# [using statement](../../../csharp/language-reference/keywords/using-statement.md).</span></span> <span data-ttu-id="cbee8-155">Si vous avez une instruction [try-finally](../../../csharp/language-reference/keywords/try-finally.md) dans laquelle le seul code du bloc `finally` est un appel à la méthode <xref:System.IDisposable.Dispose%2A>, utilisez à la place une instruction `using`.</span><span class="sxs-lookup"><span data-stu-id="cbee8-155">If you have a [try-finally](../../../csharp/language-reference/keywords/try-finally.md) statement in which the only code in the `finally` block is a call to the <xref:System.IDisposable.Dispose%2A> method, use a `using` statement instead.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#17](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#17)]  
  
### <a name="-and-124124-operators"></a><span data-ttu-id="cbee8-156">Opérateurs && et &#124;&#124;</span><span class="sxs-lookup"><span data-stu-id="cbee8-156">&& and &#124;&#124; Operators</span></span>  
  
-   <span data-ttu-id="cbee8-157">Pour éviter les exceptions et accroître les performances en ignorant les comparaisons superflues, utilisez [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) au lieu de [&](../../../csharp/language-reference/operators/and-operator.md) et [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) au lieu de [&#124;](../../../csharp/language-reference/operators/or-operator.md) quand vous effectuez des comparaisons, comme indiqué dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="cbee8-157">To avoid exceptions and increase performance by skipping unnecessary comparisons, use [&&](../../../csharp/language-reference/operators/conditional-and-operator.md) instead of [&](../../../csharp/language-reference/operators/and-operator.md) and [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md) instead of [&#124;](../../../csharp/language-reference/operators/or-operator.md) when you perform comparisons, as shown in the following example.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#18](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#18)]  
  
### <a name="new-operator"></a><span data-ttu-id="cbee8-158">New, opérateur</span><span class="sxs-lookup"><span data-stu-id="cbee8-158">New Operator</span></span>  
  
-   <span data-ttu-id="cbee8-159">Utilisez la forme concise de l'instanciation d'objets, avec typage implicite, comme indiqué dans la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="cbee8-159">Use the concise form of object instantiation, with implicit typing, as shown in the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#19](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#19)]  
  
     <span data-ttu-id="cbee8-160">La ligne précédente est équivalente à la déclaration suivante.</span><span class="sxs-lookup"><span data-stu-id="cbee8-160">The previous line is equivalent to the following declaration.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#20](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#20)]  
  
-   <span data-ttu-id="cbee8-161">Utilisez les initialiseurs d'objets pour simplifier la création d'objet.</span><span class="sxs-lookup"><span data-stu-id="cbee8-161">Use object initializers to simplify object creation.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#21](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#21)]  
  
### <a name="event-handling"></a><span data-ttu-id="cbee8-162">Gestion des événements</span><span class="sxs-lookup"><span data-stu-id="cbee8-162">Event Handling</span></span>  
  
-   <span data-ttu-id="cbee8-163">Si vous définissez un gestionnaire d'événements que vous n'avez pas besoin de supprimer ultérieurement, utilisez une expression lambda.</span><span class="sxs-lookup"><span data-stu-id="cbee8-163">If you are defining an event handler that you do not need to remove later, use a lambda expression.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#22](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#22)]  
  
     [!code-csharp[csProgGuideCodingConventions#23](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#23)]  
  
### <a name="static-members"></a><span data-ttu-id="cbee8-164">Membres static</span><span class="sxs-lookup"><span data-stu-id="cbee8-164">Static Members</span></span>  
  
-   <span data-ttu-id="cbee8-165">Appelez les membres [static](../../../csharp/language-reference/keywords/static.md) en utilisant le nom de la classe : *Nom_classe.Membre_statique*.</span><span class="sxs-lookup"><span data-stu-id="cbee8-165">Call [static](../../../csharp/language-reference/keywords/static.md) members by using the class name: *ClassName.StaticMember*.</span></span> <span data-ttu-id="cbee8-166">Cette pratique rend le code plus lisible en clarifiant l'accès aux membres static.</span><span class="sxs-lookup"><span data-stu-id="cbee8-166">This practice makes code more readable by making static access clear.</span></span>  <span data-ttu-id="cbee8-167">Ne qualifiez pas un membre static défini dans une classe de base avec le nom d'une classe dérivée.</span><span class="sxs-lookup"><span data-stu-id="cbee8-167">Do not qualify a static member defined in a base class with the name of a derived class.</span></span>  <span data-ttu-id="cbee8-168">Lorsque ce code est compilé, la lisibilité du code est trompeuse et le code peut s'interrompre à l'avenir si vous ajoutez à la classe dérivée un membre static de même nom.</span><span class="sxs-lookup"><span data-stu-id="cbee8-168">While that code compiles, the code readability is misleading, and the code may break in the future if you add a static member with the same name to the derived class.</span></span>  
  
### <a name="linq-queries"></a><span data-ttu-id="cbee8-169">Requêtes LINQ</span><span class="sxs-lookup"><span data-stu-id="cbee8-169">LINQ Queries</span></span>  
  
-   <span data-ttu-id="cbee8-170">Utilisez des noms explicites pour les variables de requête.</span><span class="sxs-lookup"><span data-stu-id="cbee8-170">Use meaningful names for query variables.</span></span> <span data-ttu-id="cbee8-171">L'exemple suivant utilise `seattleCustomers` pour les clients qui se trouvent à Seattle.</span><span class="sxs-lookup"><span data-stu-id="cbee8-171">The following example uses `seattleCustomers` for customers who are located in Seattle.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="cbee8-172">Utilisez des alias pour vous assurer que les noms de propriétés des types anonymes sont correctement écrits en majuscules à l'aide de la casse Pascal.</span><span class="sxs-lookup"><span data-stu-id="cbee8-172">Use aliases to make sure that property names of anonymous types are correctly capitalized, using Pascal casing.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#26](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#26)]  
  
-   <span data-ttu-id="cbee8-173">Renommez les propriétés lorsque les noms de propriétés dans le résultat sont ambigus.</span><span class="sxs-lookup"><span data-stu-id="cbee8-173">Rename properties when the property names in the result would be ambiguous.</span></span> <span data-ttu-id="cbee8-174">Par exemple, si votre requête retourne un nom de client et un ID de distributeur, au lieu de les laisser sous la forme `Name` et `ID` dans le résultat, renommez-les pour montrer clairement que `Name` est le nom d'un client et `ID` l'ID d'un distributeur.</span><span class="sxs-lookup"><span data-stu-id="cbee8-174">For example, if your query returns a customer name and a distributor ID, instead of leaving them as `Name` and `ID` in the result, rename them to clarify that `Name` is the name of a customer, and `ID` is the ID of a distributor.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#27](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#27)]  
  
-   <span data-ttu-id="cbee8-175">Utilisez le typage implicite dans la déclaration des variables de requête et des variables de portée.</span><span class="sxs-lookup"><span data-stu-id="cbee8-175">Use implicit typing in the declaration of query variables and range variables.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#25](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#25)]  
  
-   <span data-ttu-id="cbee8-176">Alignez les clauses de requête sous la clause [from](../../../csharp/language-reference/keywords/from-clause.md), comme illustré dans les exemples précédents.</span><span class="sxs-lookup"><span data-stu-id="cbee8-176">Align query clauses under the [from](../../../csharp/language-reference/keywords/from-clause.md) clause, as shown in the previous examples.</span></span>  
  
-   <span data-ttu-id="cbee8-177">Utilisez les clauses [where](../../../csharp/language-reference/keywords/where-clause.md) avant les autres clauses de requête pour garantir que les clauses de requête ultérieures opèrent sur l’ensemble de données réduit et filtré.</span><span class="sxs-lookup"><span data-stu-id="cbee8-177">Use [where](../../../csharp/language-reference/keywords/where-clause.md) clauses before other query clauses to ensure that later query clauses operate on the reduced, filtered set of data.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#29](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#29)]  
  
-   <span data-ttu-id="cbee8-178">Utilisez plusieurs clauses `from` au lieu d’une clause [join](../../../csharp/language-reference/keywords/join-clause.md) pour accéder aux collections internes.</span><span class="sxs-lookup"><span data-stu-id="cbee8-178">Use multiple `from` clauses instead of a [join](../../../csharp/language-reference/keywords/join-clause.md) clause to access inner collections.</span></span> <span data-ttu-id="cbee8-179">Par exemple, une collection d'objets `Student` peut contenir chacune une collection de scores de test.</span><span class="sxs-lookup"><span data-stu-id="cbee8-179">For example, a collection of `Student` objects might each contain a collection of test scores.</span></span> <span data-ttu-id="cbee8-180">Lorsque la requête suivante est exécutée, elle retourne chaque score supérieur à 90, avec le nom de l'étudiant correspondant.</span><span class="sxs-lookup"><span data-stu-id="cbee8-180">When the following query is executed, it returns each score that is over 90, along with the last name of the student who received the score.</span></span>  
  
     [!code-csharp[csProgGuideCodingConventions#30](../../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csprogguidecodingconventions/cs/program.cs#30)]  
  
## <a name="security"></a><span data-ttu-id="cbee8-181">Sécurité</span><span class="sxs-lookup"><span data-stu-id="cbee8-181">Security</span></span>  
 <span data-ttu-id="cbee8-182">Suivez les instructions indiquées dans [Instructions de codage sécurisé](../../../standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="cbee8-182">Follow the guidelines in [Secure Coding Guidelines](../../../standard/security/secure-coding-guidelines.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbee8-183">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cbee8-183">See Also</span></span>  
 [<span data-ttu-id="cbee8-184">Conventions de codage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cbee8-184">Visual Basic Coding Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/coding-conventions.md)  
 [<span data-ttu-id="cbee8-185">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="cbee8-185">Secure Coding Guidelines</span></span>](../../../standard/security/secure-coding-guidelines.md)
