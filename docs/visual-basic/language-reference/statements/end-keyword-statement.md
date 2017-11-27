---
title: "Fin &lt;mot clé&gt; , instruction (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.EndDefinition
helpviewer_keywords: End keyword [Visual Basic]
ms.assetid: 42d6e088-ab0f-4cda-88e8-fdce3e5fcf4f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cf0ac1221f8a85a8a43599d9c5ec210884205e5e
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/22/2017
---
# <a name="end-ltkeywordgt-statement-visual-basic"></a><span data-ttu-id="29598-102">Fin &lt;mot clé&gt; , instruction (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29598-102">End &lt;keyword&gt; Statement (Visual Basic)</span></span>
<span data-ttu-id="29598-103">Lorsque le suivi d’un mot clé supplémentaire, termine la définition du bloc d’instruction introduit par ce mot clé.</span><span class="sxs-lookup"><span data-stu-id="29598-103">When followed by an additional keyword, terminates the definition of the statement block introduced by that keyword.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29598-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29598-104">Syntax</span></span>  
  
```  
End AddHandler  
End Class   
End Enum   
End Event   
End Function   
End Get   
End If   
End Interface   
End Module   
End Namespace   
End Operator   
End Property   
End RaiseEvent  
End RemoveHandler  
End Select   
End Set   
End Structure   
End Sub   
End SyncLock   
End Try   
End While   
End With  
```  
  
## <a name="parts"></a><span data-ttu-id="29598-105">Composants</span><span class="sxs-lookup"><span data-stu-id="29598-105">Parts</span></span>  
 `End`  
 <span data-ttu-id="29598-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="29598-106">Required.</span></span> <span data-ttu-id="29598-107">Termine la définition de l’élément de programmation.</span><span class="sxs-lookup"><span data-stu-id="29598-107">Terminates the definition of the programming element.</span></span>  
  
 `AddHandler`  
 <span data-ttu-id="29598-108">Requis pour terminer une `AddHandler` accesseur commencé par une mise en correspondance `AddHandler` instruction personnalisé [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-108">Required to terminate an `AddHandler` accessor begun by a matching `AddHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Class`  
 <span data-ttu-id="29598-109">Requis pour terminer une définition de classe commencée par un correspondant [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-109">Required to terminate a class definition begun by a matching [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md).</span></span>  
  
 `Enum`  
 <span data-ttu-id="29598-110">Requis pour terminer une définition d’énumération commencée par une mise en correspondance [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-110">Required to terminate an enumeration definition begun by a matching [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md).</span></span>  
  
 `Event`  
 <span data-ttu-id="29598-111">Requis pour terminer un `Custom` événement commencée par une mise en correspondance [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-111">Required to terminate a `Custom` event definition begun by a matching [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Function`  
 <span data-ttu-id="29598-112">Requis pour terminer un `Function` procédure commencée par une mise en correspondance [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-112">Required to terminate a `Function` procedure definition begun by a matching [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="29598-113">Si l’exécution rencontre une `End``Function` instruction, contrôle retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="29598-113">If execution encounters an `End``Function` statement, control returns to the calling code.</span></span>  
  
 `Get`  
 <span data-ttu-id="29598-114">Requis pour terminer un `Property` procédure commencée par une mise en correspondance [instruction Get](../../../visual-basic/language-reference/statements/get-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-114">Required to terminate a `Property` procedure definition begun by a matching [Get Statement](../../../visual-basic/language-reference/statements/get-statement.md).</span></span> <span data-ttu-id="29598-115">Si l’exécution rencontre une `End``Get` instruction, contrôle retourne à l’instruction demandant la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="29598-115">If execution encounters an `End``Get` statement, control returns to the statement requesting the property's value.</span></span>  
  
 `If`  
 <span data-ttu-id="29598-116">Requis pour terminer une `If`... `Then`... `Else` commencée par une mise en correspondance `If` instruction.</span><span class="sxs-lookup"><span data-stu-id="29598-116">Required to terminate an `If`...`Then`...`Else` block definition begun by a matching `If` statement.</span></span> <span data-ttu-id="29598-117">Consultez [si... Puis... Else, instruction](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-117">See [If...Then...Else Statement](../../../visual-basic/language-reference/statements/if-then-else-statement.md).</span></span>  
  
 `Interface`  
 <span data-ttu-id="29598-118">Requis pour terminer une définition d’interface commencée par un correspondant [instruction Interface](../../../visual-basic/language-reference/statements/interface-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-118">Required to terminate an interface definition begun by a matching [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md).</span></span>  
  
 `Module`  
 <span data-ttu-id="29598-119">Requis pour terminer une définition de module commencée par un correspondant [Module, instruction](../../../visual-basic/language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-119">Required to terminate a module definition begun by a matching [Module Statement](../../../visual-basic/language-reference/statements/module-statement.md).</span></span>  
  
 `Namespace`  
 <span data-ttu-id="29598-120">Requis pour terminer une définition de l’espace de noms commencée par un correspondant [Namespace instruction](../../../visual-basic/language-reference/statements/namespace-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-120">Required to terminate a namespace definition begun by a matching [Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md).</span></span>  
  
 `Operator`  
 <span data-ttu-id="29598-121">Requis pour terminer une définition d’opérateur commencée par un correspondant [Operator, instruction](../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-121">Required to terminate an operator definition begun by a matching [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 `Property`  
 <span data-ttu-id="29598-122">Requis pour terminer une définition de propriété commencée par une mise en correspondance [Property, instruction](../../../visual-basic/language-reference/statements/property-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-122">Required to terminate a property definition begun by a matching [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md).</span></span>  
  
 `RaiseEvent`  
 <span data-ttu-id="29598-123">Requis pour terminer un `RaiseEvent` accesseur commencé par une mise en correspondance `RaiseEvent` instruction personnalisé [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-123">Required to terminate a `RaiseEvent` accessor begun by a matching `RaiseEvent` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `RemoveHandler`  
 <span data-ttu-id="29598-124">Requis pour terminer un `RemoveHandler` accesseur commencé par une mise en correspondance `RemoveHandler` instruction personnalisé [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-124">Required to terminate a `RemoveHandler` accessor begun by a matching `RemoveHandler` statement in a custom [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
 `Select`  
 <span data-ttu-id="29598-125">Requis pour terminer un `Select`... `Case` commencée par une mise en correspondance `Select` instruction.</span><span class="sxs-lookup"><span data-stu-id="29598-125">Required to terminate a `Select`...`Case` block definition begun by a matching `Select` statement.</span></span> <span data-ttu-id="29598-126">Consultez [sélectionnez... Cas d’instruction](../../../visual-basic/language-reference/statements/select-case-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-126">See [Select...Case Statement](../../../visual-basic/language-reference/statements/select-case-statement.md).</span></span>  
  
 `Set`  
 <span data-ttu-id="29598-127">Requis pour terminer un `Property` procédure commencée par une mise en correspondance [instruction Set](../../../visual-basic/language-reference/statements/set-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-127">Required to terminate a `Property` procedure definition begun by a matching [Set Statement](../../../visual-basic/language-reference/statements/set-statement.md).</span></span> <span data-ttu-id="29598-128">Si l’exécution rencontre une `End``Set` instruction, contrôle retourne à l’instruction définissant la valeur de propriété.</span><span class="sxs-lookup"><span data-stu-id="29598-128">If execution encounters an `End``Set` statement, control returns to the statement setting the property's value.</span></span>  
  
 `Structure`  
 <span data-ttu-id="29598-129">Requis pour terminer une définition de structure commencée par une mise en correspondance [instruction Structure](../../../visual-basic/language-reference/statements/structure-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-129">Required to terminate a structure definition begun by a matching [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md).</span></span>  
  
 `Sub`  
 <span data-ttu-id="29598-130">Requis pour terminer un `Sub` procédure commencée par une mise en correspondance [Sub, instruction](../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-130">Required to terminate a `Sub` procedure definition begun by a matching [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md).</span></span> <span data-ttu-id="29598-131">Si l’exécution rencontre une `End``Sub` instruction, contrôle retourne au code appelant.</span><span class="sxs-lookup"><span data-stu-id="29598-131">If execution encounters an `End``Sub` statement, control returns to the calling code.</span></span>  
  
 `SyncLock`  
 <span data-ttu-id="29598-132">Requis pour terminer un `SyncLock` commencée par une mise en correspondance `SyncLock` instruction.</span><span class="sxs-lookup"><span data-stu-id="29598-132">Required to terminate a `SyncLock` block definition begun by a matching `SyncLock` statement.</span></span> <span data-ttu-id="29598-133">Consultez [SyncLock, instruction](../../../visual-basic/language-reference/statements/synclock-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-133">See [SyncLock Statement](../../../visual-basic/language-reference/statements/synclock-statement.md).</span></span>  
  
 `Try`  
 <span data-ttu-id="29598-134">Requis pour terminer un `Try`... `Catch`... `Finally` commencée par une mise en correspondance `Try` instruction.</span><span class="sxs-lookup"><span data-stu-id="29598-134">Required to terminate a `Try`...`Catch`...`Finally` block definition begun by a matching `Try` statement.</span></span> <span data-ttu-id="29598-135">Consultez [essayez... Catch... Instruction finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-135">See [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 `While`  
 <span data-ttu-id="29598-136">Requis pour terminer un `While` commencée par une mise en correspondance de boucle `While` instruction.</span><span class="sxs-lookup"><span data-stu-id="29598-136">Required to terminate a `While` loop definition begun by a matching `While` statement.</span></span> <span data-ttu-id="29598-137">Consultez [tandis que... End While, instruction](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-137">See [While...End While Statement](../../../visual-basic/language-reference/statements/while-end-while-statement.md).</span></span>  
  
 `With`  
 <span data-ttu-id="29598-138">Requis pour terminer un `With` commencée par une mise en correspondance `With` instruction.</span><span class="sxs-lookup"><span data-stu-id="29598-138">Required to terminate a `With` block definition begun by a matching `With` statement.</span></span> <span data-ttu-id="29598-139">Consultez [avec... End With, instruction](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29598-139">See [With...End With Statement](../../../visual-basic/language-reference/statements/with-end-with-statement.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29598-140">Remarques</span><span class="sxs-lookup"><span data-stu-id="29598-140">Remarks</span></span>  
 <span data-ttu-id="29598-141">Le [l’instruction End](../../../visual-basic/language-reference/statements/end-statement.md), sans mot clé supplémentaire, termine l’exécution immédiatement.</span><span class="sxs-lookup"><span data-stu-id="29598-141">The [End Statement](../../../visual-basic/language-reference/statements/end-statement.md), without an additional keyword, terminates execution immediately.</span></span>  
  
 <span data-ttu-id="29598-142">Lorsque précédé par un signe dièse (`#`), le `End` mot clé termine un bloc de prétraitement introduit par la directive correspondante.</span><span class="sxs-lookup"><span data-stu-id="29598-142">When preceded by a number sign (`#`), the `End` keyword terminates a preprocessing block introduced by the corresponding directive.</span></span>  
  
 `#End`  
 <span data-ttu-id="29598-143">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="29598-143">Required.</span></span> <span data-ttu-id="29598-144">Termine la définition du bloc de prétraitement.</span><span class="sxs-lookup"><span data-stu-id="29598-144">Terminates the definition of the preprocessing block.</span></span>  
  
 `#ExternalSource`  
 <span data-ttu-id="29598-145">Requis pour terminer un bloc source externe commencé par une mise en correspondance [Directive #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span><span class="sxs-lookup"><span data-stu-id="29598-145">Required to terminate an external source block begun by a matching [#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md).</span></span>  
  
 `#If`  
 <span data-ttu-id="29598-146">Requis pour terminer un bloc de compilation conditionnelle commencé par une mise en correspondance `#If` directive.</span><span class="sxs-lookup"><span data-stu-id="29598-146">Required to terminate a conditional compilation block begun by a matching `#If` directive.</span></span> <span data-ttu-id="29598-147">Consultez [#If... Then... #Else, Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span><span class="sxs-lookup"><span data-stu-id="29598-147">See [#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md).</span></span>  
  
 `#Region`  
 <span data-ttu-id="29598-148">Requis pour terminer un bloc de région source commencé par une mise en correspondance [Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md).</span><span class="sxs-lookup"><span data-stu-id="29598-148">Required to terminate a source region block begun by a matching [#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md).</span></span>  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="29598-149">Remarques sur le développement Smart Device</span><span class="sxs-lookup"><span data-stu-id="29598-149">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="29598-150">La `End` instruction, sans mot clé supplémentaire, n’est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="29598-150">The `End` statement, without an additional keyword, is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29598-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="29598-151">See Also</span></span>  
 [<span data-ttu-id="29598-152">End (instruction)</span><span class="sxs-lookup"><span data-stu-id="29598-152">End Statement</span></span>](../../../visual-basic/language-reference/statements/end-statement.md)
