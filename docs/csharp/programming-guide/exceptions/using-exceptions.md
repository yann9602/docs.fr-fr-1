---
title: Utilisation d'exceptions (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 96fc082d135d38f521429de7b4e9a668773982ea
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-exceptions-c-programming-guide"></a><span data-ttu-id="af253-102">Utilisation d'exceptions (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="af253-102">Using Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="af253-103">En C#, les erreurs qui se produisent dans le programme au moment de l’exécution sont propagées à travers le programme à l’aide du mécanisme des exceptions.</span><span class="sxs-lookup"><span data-stu-id="af253-103">In C#, errors in the program at run time are propagated through the program by using a mechanism called exceptions.</span></span> <span data-ttu-id="af253-104">Les exceptions sont levées par le code qui rencontre une erreur et interceptées par le code qui peut corriger l’erreur.</span><span class="sxs-lookup"><span data-stu-id="af253-104">Exceptions are thrown by code that encounters an error and caught by code that can correct the error.</span></span> <span data-ttu-id="af253-105">Les exceptions peuvent être levées par le CLR (Common Language Runtime) du .NET Framework ou par du code dans un programme.</span><span class="sxs-lookup"><span data-stu-id="af253-105">Exceptions can be thrown by the .NET Framework common language runtime (CLR) or by code in a program.</span></span> <span data-ttu-id="af253-106">Une fois qu’une exception est levée, elle se propage jusqu’en haut de la pile des appels, jusqu’à ce qu’une instruction `catch` soit trouvée pour l’exception.</span><span class="sxs-lookup"><span data-stu-id="af253-106">Once an exception is thrown, it propagates up the call stack until a `catch` statement for the exception is found.</span></span> <span data-ttu-id="af253-107">Les exceptions non interceptées sont gérées par un gestionnaire d’exceptions génériques fourni par le système qui affiche une boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="af253-107">Uncaught exceptions are handled by a generic exception handler provided by the system that displays a dialog box.</span></span>  
  
 <span data-ttu-id="af253-108">Les exceptions sont représentées par des classes dérivées de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="af253-108">Exceptions are represented by classes derived from <xref:System.Exception>.</span></span> <span data-ttu-id="af253-109">Cette classe identifie le type d’exception et contient des propriétés comportant des détails sur l’exception.</span><span class="sxs-lookup"><span data-stu-id="af253-109">This class identifies the type of exception and contains properties that have details about the exception.</span></span> <span data-ttu-id="af253-110">Lever une exception implique de créer une instance d’une classe dérivée d’une exception, de configurer éventuellement les propriétés de l’exception, puis de lever l’objet à l’aide du mot clé `throw`.</span><span class="sxs-lookup"><span data-stu-id="af253-110">Throwing an exception involves creating an instance of an exception-derived class, optionally configuring properties of the exception, and then throwing the object by using the `throw` keyword.</span></span> <span data-ttu-id="af253-111">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af253-111">For example:</span></span>  
  
 <span data-ttu-id="af253-112">[!code-cs[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="af253-112">[!code-cs[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]</span></span>  
  
 <span data-ttu-id="af253-113">Après la levée d’une exception, le runtime vérifie l’instruction actuelle pour voir si elle se trouve dans un bloc `try`.</span><span class="sxs-lookup"><span data-stu-id="af253-113">After an exception is thrown, the runtime checks the current statement to see whether it is within a `try` block.</span></span> <span data-ttu-id="af253-114">Si tel est le cas, tous les blocs `catch` associés au bloc `try` font l’objet d’un contrôle permettant de déterminer s’ils peuvent intercepter l’exception.</span><span class="sxs-lookup"><span data-stu-id="af253-114">If it is, any `catch` blocks associated with the `try` block are checked to see whether they can catch the exception.</span></span> <span data-ttu-id="af253-115">Les blocs `Catch` spécifient généralement des types d’exception ; si le type du bloc `catch` est identique à celui de l’exception ou d’une classe de base de l’exception, le bloc `catch` peut gérer la méthode.</span><span class="sxs-lookup"><span data-stu-id="af253-115">`Catch` blocks typically specify exception types; if the type of the `catch` block is the same type as the exception, or a base class of the exception, the `catch` block can handle the method.</span></span> <span data-ttu-id="af253-116">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af253-116">For example:</span></span>  
  
 <span data-ttu-id="af253-117">[!code-cs[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="af253-117">[!code-cs[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]</span></span>  
  
 <span data-ttu-id="af253-118">Si l’instruction qui lève une exception ne se trouve pas à l’intérieur d’un bloc `try` ou si le bloc `try` qui la contient n’a pas de bloc `catch` correspondant, le runtime vérifie que la méthode d’appel dispose d’une instruction `try` et de blocs `catch`.</span><span class="sxs-lookup"><span data-stu-id="af253-118">If the statement that throws an exception is not within a `try` block or if the `try` block that encloses it has no matching `catch` block, the runtime checks the calling method for a `try` statement and `catch` blocks.</span></span> <span data-ttu-id="af253-119">Le runtime continue jusqu’à la pile appelante, à la recherche d’un bloc `catch` compatible.</span><span class="sxs-lookup"><span data-stu-id="af253-119">The runtime continues up the calling stack, searching for a compatible `catch` block.</span></span> <span data-ttu-id="af253-120">Une fois le bloc `catch` trouvé et exécuté, le contrôle est passé à l’instruction suivante après le bloc `catch`.</span><span class="sxs-lookup"><span data-stu-id="af253-120">After the `catch` block is found and executed, control is passed to the next statement after that `catch` block.</span></span>  
  
 <span data-ttu-id="af253-121">Une instruction `try` peut contenir plusieurs blocs `catch`.</span><span class="sxs-lookup"><span data-stu-id="af253-121">A `try` statement can contain more than one `catch` block.</span></span> <span data-ttu-id="af253-122">La première instruction `catch` qui peut gérer l’exception est exécutée ; toutes les instructions `catch` suivantes, même compatibles, sont ignorées.</span><span class="sxs-lookup"><span data-stu-id="af253-122">The first `catch` statement that can handle the exception is executed; any following `catch` statements, even if they are compatible, are ignored.</span></span> <span data-ttu-id="af253-123">Par conséquent, les blocs catch doivent toujours être classés du plus spécifique (ou du plus dérivé) au moins spécifique.</span><span class="sxs-lookup"><span data-stu-id="af253-123">Therefore, catch blocks should always be ordered from most specific (or most-derived) to least specific.</span></span> <span data-ttu-id="af253-124">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af253-124">For example:</span></span>  
  
 <span data-ttu-id="af253-125">[!code-cs[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="af253-125">[!code-cs[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]</span></span>  
  
 <span data-ttu-id="af253-126">Avant que le bloc `catch` ne soit exécuté, le runtime vérifie la présence de blocs `finally`.</span><span class="sxs-lookup"><span data-stu-id="af253-126">Before the `catch` block is executed, the runtime checks for `finally` blocks.</span></span> <span data-ttu-id="af253-127">Les blocs `Finally` permettent au programmeur de nettoyer tout état ambigu qui pourrait subsister après l’abandon d’un bloc `try`, ou de libérer les ressources externes (telles que les handles graphiques, les connexions de bases de données ou les flux de fichiers) sans attendre que le garbage collector du runtime ne finalise les objets.</span><span class="sxs-lookup"><span data-stu-id="af253-127">`Finally` blocks enable the programmer to clean up any ambiguous state that could be left over from an aborted `try` block, or to release any external resources (such as graphics handles, database connections or file streams) without waiting for the garbage collector in the runtime to finalize the objects.</span></span> <span data-ttu-id="af253-128">Exemple :</span><span class="sxs-lookup"><span data-stu-id="af253-128">For example:</span></span>  
  
 <span data-ttu-id="af253-129">[!code-cs[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="af253-129">[!code-cs[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]</span></span>  
  
 <span data-ttu-id="af253-130">Si `WriteByte()` a levé une exception, le code du deuxième bloc `try` qui essaie de rouvrir le fichier échoue si `file.Close()` n’est pas appelé, et le fichier reste verrouillé.</span><span class="sxs-lookup"><span data-stu-id="af253-130">If `WriteByte()` threw an exception, the code in the second `try` block that tries to reopen the file would fail if `file.Close()` is not called, and the file would remain locked.</span></span> <span data-ttu-id="af253-131">Étant donné que les blocs `finally` sont exécutés même si une exception est levée, le bloc `finally` de l’exemple précédent autorise la fermeture correcte du fichier et permet d’éviter une erreur.</span><span class="sxs-lookup"><span data-stu-id="af253-131">Because `finally` blocks are executed even if an exception is thrown, the `finally` block in the previous example allows for the file to be closed correctly and helps avoid an error.</span></span>  
  
 <span data-ttu-id="af253-132">Si aucun bloc `catch` compatible n’est trouvé sur la pile des appels après la levée d’une exception, l’une des trois situations suivantes se produit :</span><span class="sxs-lookup"><span data-stu-id="af253-132">If no compatible `catch` block is found on the call stack after an exception is thrown, one of three things occurs:</span></span>  
  
-   <span data-ttu-id="af253-133">Si l’exception se trouve dans un finaliseur, le finaliseur est abandonné et le finaliseur de base, le cas échéant, est appelé.</span><span class="sxs-lookup"><span data-stu-id="af253-133">If the exception is within a finalizer, the finalizer is aborted and the base finalizer, if any, is called.</span></span>  
  
-   <span data-ttu-id="af253-134">Si la pile des appels contient un constructeur statique ou un initialiseur de champ statique, une <xref:System.TypeInitializationException> est levée, avec l’exception d’origine assignée à la propriété <xref:System.Exception.InnerException%2A> de la nouvelle exception.</span><span class="sxs-lookup"><span data-stu-id="af253-134">If the call stack contains a static constructor, or a static field initializer, a <xref:System.TypeInitializationException> is thrown, with the original exception assigned to the <xref:System.Exception.InnerException%2A> property of the new exception.</span></span>  
  
-   <span data-ttu-id="af253-135">Si le début du thread est atteint, le thread est terminé.</span><span class="sxs-lookup"><span data-stu-id="af253-135">If the start of the thread is reached, the thread is terminated.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af253-136">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="af253-136">See Also</span></span>  
 <span data-ttu-id="af253-137">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="af253-137">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="af253-138">Exceptions et gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="af253-138">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)

