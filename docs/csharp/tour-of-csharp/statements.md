---
title: "Instructions C# - Visite guidée du langage C#"
description: "Vous créez les actions d’un programme C# à l’aide d’instructions"
keywords: .NET, csharp, instructions, syntaxe
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 5409c379-5622-4fae-88b5-1654276ea8d4
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 99ec2489daf89926da9b8c4e148965412826a8a6
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="statements"></a><span data-ttu-id="778e2-104">Instructions</span><span class="sxs-lookup"><span data-stu-id="778e2-104">Statements</span></span>

<span data-ttu-id="778e2-105">Les actions d’un programme sont exprimées à l’aide *d’instructions*.</span><span class="sxs-lookup"><span data-stu-id="778e2-105">The actions of a program are expressed using *statements*.</span></span> <span data-ttu-id="778e2-106">C# prend en charge plusieurs types d’instructions, dont plusieurs sont définies en termes d’instructions incorporées.</span><span class="sxs-lookup"><span data-stu-id="778e2-106">C# supports several different kinds of statements, a number of which are defined in terms of embedded statements.</span></span>

<span data-ttu-id="778e2-107">Un *bloc* autorise l’écriture de plusieurs instructions dans les contextes où une seule instruction est autorisée.</span><span class="sxs-lookup"><span data-stu-id="778e2-107">A *block* permits multiple statements to be written in contexts where a single statement is allowed.</span></span> <span data-ttu-id="778e2-108">Un bloc se compose d’une liste d’instructions écrites entre les délimiteurs `{` et `}`.</span><span class="sxs-lookup"><span data-stu-id="778e2-108">A block consists of a list of statements written between the delimiters `{` and `}`.</span></span>

<span data-ttu-id="778e2-109">Les *instructions de déclaration* sont utilisées pour déclarer des variables locales et des constantes.</span><span class="sxs-lookup"><span data-stu-id="778e2-109">*Declaration statements* are used to declare local variables and constants.</span></span>

<span data-ttu-id="778e2-110">Les *instructions d’expression* sont utilisées pour évaluer des expressions.</span><span class="sxs-lookup"><span data-stu-id="778e2-110">*Expression statements* are used to evaluate expressions.</span></span> <span data-ttu-id="778e2-111">Les expressions qui peuvent être utilisées en tant qu’instructions comprennent les appels de méthode, les allocations d’objet avec l’opérateur `new`, les affectations avec `=` et les opérateurs d’assignation composée, les opérations d’incrémentation et de décrémentation à l’aide des opérateurs `++` et `--` et les expressions `await`.</span><span class="sxs-lookup"><span data-stu-id="778e2-111">Expressions that can be used as statements include method invocations, object allocations using the `new` operator, assignments using `=` and the compound assignment operators, increment and decrement operations using the `++` and `--` operators and `await` expressions.</span></span>

<span data-ttu-id="778e2-112">Les *instructions de sélection* sont utilisées pour sélectionner un nombre d’instructions possibles pour l’exécution en fonction de la valeur d’une expression.</span><span class="sxs-lookup"><span data-stu-id="778e2-112">*Selection statements* are used to select one of a number of possible statements for execution based on the value of some expression.</span></span> <span data-ttu-id="778e2-113">Dans ce groupe, ce sont les instructions `if` et `switch`.</span><span class="sxs-lookup"><span data-stu-id="778e2-113">In this group are the `if` and `switch` statements.</span></span>

<span data-ttu-id="778e2-114">Les *instructions d’itération* servent à exécuter à plusieurs reprises une instruction incorporée.</span><span class="sxs-lookup"><span data-stu-id="778e2-114">*Iteration statements* are used to execute repeatedly an embedded statement.</span></span> <span data-ttu-id="778e2-115">Dans ce groupe, ce sont les instructions `while`, `do`, `for` et `foreach`.</span><span class="sxs-lookup"><span data-stu-id="778e2-115">In this group are the `while`, `do`, `for`, and `foreach` statements.</span></span>

<span data-ttu-id="778e2-116">Les *instructions de saut* sont utilisées pour transférer le contrôle.</span><span class="sxs-lookup"><span data-stu-id="778e2-116">*Jump statements* are used to transfer control.</span></span> <span data-ttu-id="778e2-117">Dans ce groupe, ce sont les instructions `break`, `continue`, `goto`, `throw`, `return` et `yield`.</span><span class="sxs-lookup"><span data-stu-id="778e2-117">In this group are the `break`, `continue`, `goto`, `throw`, `return`, and `yield` statements.</span></span>

<span data-ttu-id="778e2-118">L’instruction `try`...`catch` est utilisée pour intercepter les exceptions qui se produisent pendant l’exécution d’un bloc, et l’instruction `try`...`finally` permet de spécifier que le code de finalisation est toujours exécuté, qu’une exception se soit produite ou non.</span><span class="sxs-lookup"><span data-stu-id="778e2-118">The `try`...`catch` statement is used to catch exceptions that occur during execution of a block, and the `try`...`finally` statement is used to specify finalization code that is always executed, whether an exception occurred or not.</span></span>

<span data-ttu-id="778e2-119">Les instructions `checked` et `unchecked` permettent de contrôler le contexte de dépassement de capacité pour les conversions et les opérations arithmétiques de type intégral.</span><span class="sxs-lookup"><span data-stu-id="778e2-119">The `checked` and `unchecked` statements are used to control the overflow-checking context for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="778e2-120">L’instruction `lock` est utilisée pour obtenir le verrou d’exclusion mutuelle pour un objet donné, exécuter une instruction, puis libérer le verrou.</span><span class="sxs-lookup"><span data-stu-id="778e2-120">The `lock` statement is used to obtain the mutual-exclusion lock for a given object, execute a statement, and then release the lock.</span></span>

<span data-ttu-id="778e2-121">L’instruction `using` est utilisée pour obtenir une ressource, exécuter une instruction puis supprimer cette ressource.</span><span class="sxs-lookup"><span data-stu-id="778e2-121">The `using` statement is used to obtain a resource, execute a statement, and then dispose of that resource.</span></span>

<span data-ttu-id="778e2-122">La liste suivante décrit les types d’instructions qui peuvent être utilisés avec un exemple pour chacun.</span><span class="sxs-lookup"><span data-stu-id="778e2-122">The following lists the kinds of statements that can be used, and provides an example for each.</span></span>

* <span data-ttu-id="778e2-123">Déclaration de variable locale :</span><span class="sxs-lookup"><span data-stu-id="778e2-123">Local variable declaration:</span></span>

 <span data-ttu-id="778e2-124">[!code-csharp[Déclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]</span><span class="sxs-lookup"><span data-stu-id="778e2-124">[!code-csharp[Declarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L9-L15)]</span></span>

* <span data-ttu-id="778e2-125">Déclaration de constante locale :</span><span class="sxs-lookup"><span data-stu-id="778e2-125">Local constant declaration:</span></span>

 <span data-ttu-id="778e2-126">[!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]</span><span class="sxs-lookup"><span data-stu-id="778e2-126">[!code-csharp[ConstantDeclarations](../../../samples/snippets/csharp/tour/statements/Program.cs#L17-L22)]</span></span>

* <span data-ttu-id="778e2-127">Instruction d’expression :</span><span class="sxs-lookup"><span data-stu-id="778e2-127">Expression statement:</span></span>

 <span data-ttu-id="778e2-128">[!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]</span><span class="sxs-lookup"><span data-stu-id="778e2-128">[!code-csharp[Expressions](../../../samples/snippets/csharp/tour/statements/Program.cs#L24-L31)]</span></span>

* <span data-ttu-id="778e2-129">Instruction `if` :</span><span class="sxs-lookup"><span data-stu-id="778e2-129">`if` statement:</span></span>

 <span data-ttu-id="778e2-130">[!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]</span><span class="sxs-lookup"><span data-stu-id="778e2-130">[!code-csharp[IfStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L33-L43)]</span></span>

* <span data-ttu-id="778e2-131">Instruction `switch` :</span><span class="sxs-lookup"><span data-stu-id="778e2-131">`switch` statement:</span></span>

 <span data-ttu-id="778e2-132">[!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]</span><span class="sxs-lookup"><span data-stu-id="778e2-132">[!code-csharp[SwitchStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L45-L60)]</span></span>

* <span data-ttu-id="778e2-133">Instruction `while` :</span><span class="sxs-lookup"><span data-stu-id="778e2-133">`while` statement:</span></span>

 <span data-ttu-id="778e2-134">[!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]</span><span class="sxs-lookup"><span data-stu-id="778e2-134">[!code-csharp[WhileStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L62-L70)]</span></span>

* <span data-ttu-id="778e2-135">Instruction `do` :</span><span class="sxs-lookup"><span data-stu-id="778e2-135">`do` statement:</span></span>

 <span data-ttu-id="778e2-136">[!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]</span><span class="sxs-lookup"><span data-stu-id="778e2-136">[!code-csharp[DoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L72-L81)]</span></span>

* <span data-ttu-id="778e2-137">Instruction `for` :</span><span class="sxs-lookup"><span data-stu-id="778e2-137">`for` statement:</span></span>

 <span data-ttu-id="778e2-138">[!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]</span><span class="sxs-lookup"><span data-stu-id="778e2-138">[!code-csharp[ForStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L83-L89)]</span></span>

* <span data-ttu-id="778e2-139">Instruction `foreach` :</span><span class="sxs-lookup"><span data-stu-id="778e2-139">`foreach` statement:</span></span>

 <span data-ttu-id="778e2-140">[!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]</span><span class="sxs-lookup"><span data-stu-id="778e2-140">[!code-csharp[ForEachStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L91-L97)]</span></span>

* <span data-ttu-id="778e2-141">Instruction `break` :</span><span class="sxs-lookup"><span data-stu-id="778e2-141">`break` statement:</span></span>

 <span data-ttu-id="778e2-142">[!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]</span><span class="sxs-lookup"><span data-stu-id="778e2-142">[!code-csharp[BreakStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L99-L108)]</span></span>

* <span data-ttu-id="778e2-143">Instruction `continue` :</span><span class="sxs-lookup"><span data-stu-id="778e2-143">`continue` statement:</span></span>

 <span data-ttu-id="778e2-144">[!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]</span><span class="sxs-lookup"><span data-stu-id="778e2-144">[!code-csharp[ContinueStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L110-L118)]</span></span>

* <span data-ttu-id="778e2-145">Instruction `goto` :</span><span class="sxs-lookup"><span data-stu-id="778e2-145">`goto` statement:</span></span>

 <span data-ttu-id="778e2-146">[!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]</span><span class="sxs-lookup"><span data-stu-id="778e2-146">[!code-csharp[GotoStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L120-L129)]</span></span>

* <span data-ttu-id="778e2-147">Instruction `return` :</span><span class="sxs-lookup"><span data-stu-id="778e2-147">`return` statement:</span></span>

 <span data-ttu-id="778e2-148">[!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]</span><span class="sxs-lookup"><span data-stu-id="778e2-148">[!code-csharp[ReturnStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L131-L139)]</span></span>

* <span data-ttu-id="778e2-149">Instruction `yield` :</span><span class="sxs-lookup"><span data-stu-id="778e2-149">`yield` statement:</span></span>

 <span data-ttu-id="778e2-150">[!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]</span><span class="sxs-lookup"><span data-stu-id="778e2-150">[!code-csharp[YieldStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L141-L155)]</span></span>

* <span data-ttu-id="778e2-151">Instructions `throw` et instructions `try` :</span><span class="sxs-lookup"><span data-stu-id="778e2-151">`throw` statements and `try` statements:</span></span>

 <span data-ttu-id="778e2-152">[!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]</span><span class="sxs-lookup"><span data-stu-id="778e2-152">[!code-csharp[TryThrow](../../../samples/snippets/csharp/tour/statements/Program.cs#L157-L183)]</span></span>

* <span data-ttu-id="778e2-153">Instructions `checked` et `unchecked` :</span><span class="sxs-lookup"><span data-stu-id="778e2-153">`checked` and `unchecked` statements:</span></span>

 <span data-ttu-id="778e2-154">[!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]</span><span class="sxs-lookup"><span data-stu-id="778e2-154">[!code-csharp[CheckedUncheckedStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L185-L196)]</span></span>

* <span data-ttu-id="778e2-155">Instruction `lock` :</span><span class="sxs-lookup"><span data-stu-id="778e2-155">`lock` statement:</span></span>

 <span data-ttu-id="778e2-156">[!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]</span><span class="sxs-lookup"><span data-stu-id="778e2-156">[!code-csharp[LockStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L257-L273)]</span></span>

* <span data-ttu-id="778e2-157">Instruction `using` :</span><span class="sxs-lookup"><span data-stu-id="778e2-157">`using` statement:</span></span>

 <span data-ttu-id="778e2-158">[!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]</span><span class="sxs-lookup"><span data-stu-id="778e2-158">[!code-csharp[UsingStatement](../../../samples/snippets/csharp/tour/statements/Program.cs#L198-L206)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="778e2-159">[Précédent](expressions.md)
[Suivant](classes-and-objects.md)</span><span class="sxs-lookup"><span data-stu-id="778e2-159">[Previous](expressions.md)
[Next](classes-and-objects.md)</span></span>

