---
title: "Procédures dans Visual Basic"
ms.custom: 
ms.date: 2017-04-28
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- procedures, structured code
- Visual Basic code, procedures
- procedures, types of
- structured code, procedures
- procedures
ms.assetid: 9effbcf0-80a0-4d1a-98f4-2c6920592766
caps.latest.revision: 16
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: fd1a369ecfc1fa23cba694941fa47ab872ca1368
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="procedures-in-visual-basic"></a><span data-ttu-id="34af0-102">Procédures dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="34af0-102">Procedures in Visual Basic</span></span>
<span data-ttu-id="34af0-103">Une *procédure* est un bloc d’instructions [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] délimitées par une instruction de déclaration (`Function`, `Sub`, `Operator`, `Get`, `Set`) et une déclaration `End` correspondante.</span><span class="sxs-lookup"><span data-stu-id="34af0-103">A *procedure* is a block of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements enclosed by a declaration statement (`Function`, `Sub`, `Operator`, `Get`, `Set`) and a matching `End` declaration.</span></span> <span data-ttu-id="34af0-104">Toutes les instructions exécutables dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] doivent figurer dans une procédure.</span><span class="sxs-lookup"><span data-stu-id="34af0-104">All executable statements in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must be within some procedure.</span></span>  
  
## <a name="calling-a-procedure"></a><span data-ttu-id="34af0-105">Appel d’une procédure</span><span class="sxs-lookup"><span data-stu-id="34af0-105">Calling a Procedure</span></span>  
 <span data-ttu-id="34af0-106">Vous appelez une procédure à partir d’une autre partie du code.</span><span class="sxs-lookup"><span data-stu-id="34af0-106">You invoke a procedure from some other place in the code.</span></span> <span data-ttu-id="34af0-107">Il s’agit d’un *appel de procédure*.</span><span class="sxs-lookup"><span data-stu-id="34af0-107">This is known as a *procedure call*.</span></span> <span data-ttu-id="34af0-108">Une fois la procédure exécutée, elle renvoie le contrôle au code qui l’a appelée, opération qui se nomme *appel du code*.</span><span class="sxs-lookup"><span data-stu-id="34af0-108">When the procedure is finished running, it returns control to the code that invoked it, which is known as the *calling code*.</span></span> <span data-ttu-id="34af0-109">Le code appelant est une instruction ou une expression au sein d’une instruction, qui désigne la procédure par nom et lui transfère le contrôle.</span><span class="sxs-lookup"><span data-stu-id="34af0-109">The calling code is a statement, or an expression within a statement, that specifies the procedure by name and transfers control to it.</span></span>  
  
## <a name="returning-from-a-procedure"></a><span data-ttu-id="34af0-110">Retour d’une procédure</span><span class="sxs-lookup"><span data-stu-id="34af0-110">Returning from a Procedure</span></span>  
 <span data-ttu-id="34af0-111">Une procédure retourne le contrôle au code appelant lorsqu’elle est terminée.</span><span class="sxs-lookup"><span data-stu-id="34af0-111">A procedure returns control to the calling code when it has finished running.</span></span> <span data-ttu-id="34af0-112">Pour cela, elle peut utiliser une [instruction de retour](../../../../visual-basic/language-reference/statements/return-statement.md), l’instruction [Exit Statement](../../../../visual-basic/language-reference/statements/exit-statement.md) correspondant à la procédure, ou l’instruction [End \<keyword> Statement](../../../../visual-basic/language-reference/statements/end-keyword-statement.md).</span><span class="sxs-lookup"><span data-stu-id="34af0-112">To do this, it can use a [Return Statement](../../../../visual-basic/language-reference/statements/return-statement.md), the appropriate [Exit Statement](../../../../visual-basic/language-reference/statements/exit-statement.md) statement for the procedure, or the procedure's [End \<keyword> Statement](../../../../visual-basic/language-reference/statements/end-keyword-statement.md) statement.</span></span> <span data-ttu-id="34af0-113">Le contrôle passe ensuite au code appelant après le point de l’appel de procédure.</span><span class="sxs-lookup"><span data-stu-id="34af0-113">Control then passes to the calling code following the point of the procedure call.</span></span>  
  
-   <span data-ttu-id="34af0-114">Avec une instruction `Return`, le contrôle retourne immédiatement au code appelant.</span><span class="sxs-lookup"><span data-stu-id="34af0-114">With a `Return` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="34af0-115">Les instructions qui suivent l’instruction `Return` ne s’exécutent pas.</span><span class="sxs-lookup"><span data-stu-id="34af0-115">Statements following the `Return` statement do not run.</span></span> <span data-ttu-id="34af0-116">Vous pouvez utiliser plusieurs instructions `Return` dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="34af0-116">You can have more than one `Return` statement in the same procedure.</span></span>  
  
-   <span data-ttu-id="34af0-117">Avec une instruction `Exit Sub` ou `Exit Function`, le contrôle retourne immédiatement au code appelant.</span><span class="sxs-lookup"><span data-stu-id="34af0-117">With an `Exit Sub` or `Exit Function` statement, control returns immediately to the calling code.</span></span> <span data-ttu-id="34af0-118">Les instructions qui suivent l’instruction `Exit` ne s’exécutent pas.</span><span class="sxs-lookup"><span data-stu-id="34af0-118">Statements following the `Exit` statement do not run.</span></span> <span data-ttu-id="34af0-119">Vous pouvez utiliser plusieurs instructions `Exit` dans la même procédure et combiner des instructions `Return` et `Exit` dans la même procédure.</span><span class="sxs-lookup"><span data-stu-id="34af0-119">You can have more than one `Exit` statement in the same procedure, and you can mix `Return` and `Exit` statements in the same procedure.</span></span>  
  
-   <span data-ttu-id="34af0-120">Si une procédure ne comporte pas d’instructions `Return` ou `Exit`, elle se termine par une instruction `End Sub` ou `End Function`, `End Get`, ou l’instruction `End Set` qui suit la dernière instruction du corps de la procédure.</span><span class="sxs-lookup"><span data-stu-id="34af0-120">If a procedure has no `Return` or `Exit` statements, it concludes with an `End Sub` or `End Function`, `End Get`, or `End Set` statement following the last statement of the procedure body.</span></span> <span data-ttu-id="34af0-121">L’instruction `End` retourne immédiatement le contrôle au code appelant.</span><span class="sxs-lookup"><span data-stu-id="34af0-121">The `End` statement returns control immediately to the calling code.</span></span> <span data-ttu-id="34af0-122">Une procédure ne peut contenir qu’une seule instruction `End`.</span><span class="sxs-lookup"><span data-stu-id="34af0-122">You can have only one `End` statement in a procedure.</span></span>  
  
## <a name="parameters-and-arguments"></a><span data-ttu-id="34af0-123">Paramètres et arguments</span><span class="sxs-lookup"><span data-stu-id="34af0-123">Parameters and Arguments</span></span>  
 <span data-ttu-id="34af0-124">Dans la plupart des cas, une procédure doit s’exécuter sur des données différentes chaque fois que vous l’appelez.</span><span class="sxs-lookup"><span data-stu-id="34af0-124">In most cases, a procedure needs to operate on different data each time you call it.</span></span> <span data-ttu-id="34af0-125">Vous pouvez transmettre ces informations à la procédure dans le cadre de l’appel de procédure.</span><span class="sxs-lookup"><span data-stu-id="34af0-125">You can pass this information to the procedure as part of the procedure call.</span></span> <span data-ttu-id="34af0-126">La procédure définit zéro ou plusieurs *paramètres*, chacun d’eux représentant une valeur qu’elle s’attend à recevoir de votre part.</span><span class="sxs-lookup"><span data-stu-id="34af0-126">The procedure defines zero or more *parameters*, each of which represents a value it expects you to pass to it.</span></span> <span data-ttu-id="34af0-127">Dans l’appel de procédure, un *argument* est associé à chaque paramètre dans la définition de la procédure.</span><span class="sxs-lookup"><span data-stu-id="34af0-127">Corresponding to each parameter in the procedure definition is an *argument* in the procedure call.</span></span> <span data-ttu-id="34af0-128">Un argument représente la valeur que vous passez au paramètre correspondant dans un appel de procédure donné.</span><span class="sxs-lookup"><span data-stu-id="34af0-128">An argument represents the value you pass to the corresponding parameter in a given procedure call.</span></span>  
  
## <a name="types-of-procedures"></a><span data-ttu-id="34af0-129">Types de procédures</span><span class="sxs-lookup"><span data-stu-id="34af0-129">Types of Procedures</span></span>  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="34af0-130"> utilise plusieurs types de procédures :</span><span class="sxs-lookup"><span data-stu-id="34af0-130"> uses several types of procedures:</span></span>  
  
-   <span data-ttu-id="34af0-131">Les [procédures Sub](./sub-procedures.md) exécutent des actions mais ne retournent aucune valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="34af0-131">[Sub Procedures](./sub-procedures.md) perform actions but do not return a value to the calling code.</span></span>  
  
-   <span data-ttu-id="34af0-132">Les procédures de gestion d’événements sont des procédures `Sub` qui s’exécutent en réponse à un événement déclenché par une action de l’utilisateur ou une occurrence dans un programme.</span><span class="sxs-lookup"><span data-stu-id="34af0-132">Event-handling procedures are `Sub` procedures that execute in response to an event raised by user action or by an occurrence in a program.</span></span>  
  
-   <span data-ttu-id="34af0-133">Les [procédures Function](./function-procedures.md) retournent une valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="34af0-133">[Function Procedures](./function-procedures.md) return a value to the calling code.</span></span> <span data-ttu-id="34af0-134">Elles peuvent effectuer d’autres actions avant de retourner une valeur.</span><span class="sxs-lookup"><span data-stu-id="34af0-134">They can perform other actions before returning.</span></span>

    <span data-ttu-id="34af0-135">Certaines fonctions écrites en langage C# retournent une *valeur de retour de référence*.</span><span class="sxs-lookup"><span data-stu-id="34af0-135">Some functions written in C# return a *reference return value*.</span></span> <span data-ttu-id="34af0-136">Les appelants de fonction peuvent modifier la valeur de retour, et cette modification est répercutée dans l’état de l’objet appelé.</span><span class="sxs-lookup"><span data-stu-id="34af0-136">Function callers can modify the return value, and this modification is reflected in the state of the called object.</span></span> <span data-ttu-id="34af0-137">À partir de Visual Basic 2017, le code Visual Basic peut consommer des valeurs de retour de référence, même s’il ne peut pas retourner une valeur par référence.</span><span class="sxs-lookup"><span data-stu-id="34af0-137">Starting with Visual Basic 2017, Visual Basic code can consume reference return values, although it cannot return a value by reference.</span></span> <span data-ttu-id="34af0-138">Pour plus d’informations, consultez [Valeurs de retour de référence](ref-return-values.md).</span><span class="sxs-lookup"><span data-stu-id="34af0-138">For more information, see [Reference return values](ref-return-values.md).</span></span>
  
-   <span data-ttu-id="34af0-139">Les [procédures Property](./property-procedures.md) renvoient et attribuent des valeurs de propriétés à des objets ou modules.</span><span class="sxs-lookup"><span data-stu-id="34af0-139">[Property Procedures](./property-procedures.md) return and assign values of properties on objects or modules.</span></span>  
  
-   <span data-ttu-id="34af0-140">Les [procédures Operator](./operator-procedures.md) définissent le comportement d’un opérateur standard lorsqu’un ou les deux opérandes représentent une structure ou classe qui vient d’être définie.</span><span class="sxs-lookup"><span data-stu-id="34af0-140">[Operator Procedures](./operator-procedures.md) define the behavior of a standard operator when one or both of the operands is a newly-defined class or structure.</span></span>  
  
-   <span data-ttu-id="34af0-141">Les [procédures génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) définissent un ou plusieurs *paramètres de type* en plus de leurs paramètres normaux, et le code appelant peut donc passer des types de données spécifiques chaque fois qu’il effectue un appel.</span><span class="sxs-lookup"><span data-stu-id="34af0-141">[Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) define one or more *type parameters* in addition to their normal parameters, so the calling code can pass specific data types each time it makes a call.</span></span>  
  
## <a name="procedures-and-structured-code"></a><span data-ttu-id="34af0-142">Procédures et code structuré</span><span class="sxs-lookup"><span data-stu-id="34af0-142">Procedures and Structured Code</span></span>  
 <span data-ttu-id="34af0-143">Chaque ligne de code exécutable dans votre application doit figurer à l’intérieur d’une procédure, par exemple `Main`, `calculate`, ou `Button1_Click`.</span><span class="sxs-lookup"><span data-stu-id="34af0-143">Every line of executable code in your application must be inside some procedure, such as `Main`, `calculate`, or `Button1_Click`.</span></span> <span data-ttu-id="34af0-144">Si vous décomposez des procédures complexes en procédures plus simples, votre application devient plus lisible.</span><span class="sxs-lookup"><span data-stu-id="34af0-144">If you subdivide large procedures into smaller ones, your application is more readable.</span></span>  
  
 <span data-ttu-id="34af0-145">Les procédures sont utiles pour effectuer des tâches répétitives ou partagées, notamment des calculs fréquemment utilisés, la manipulation de texte et de contrôle et les opérations dans des bases de données.</span><span class="sxs-lookup"><span data-stu-id="34af0-145">Procedures are useful for performing repeated or shared tasks, such as frequently used calculations, text and control manipulation, and database operations.</span></span> <span data-ttu-id="34af0-146">Vous pouvez appeler une procédure à partir de différentes sections de votre code et ainsi utiliser les procédures comme des blocs de construction pour votre application.</span><span class="sxs-lookup"><span data-stu-id="34af0-146">You can call a procedure from many different places in your code, so you can use procedures as building blocks for your application.</span></span>  
  
 <span data-ttu-id="34af0-147">Structurer votre code avec des procédures vous offre les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="34af0-147">Structuring your code with procedures gives you the following benefits:</span></span>  
  
-   <span data-ttu-id="34af0-148">Les procédures vous permettent de décomposer vos programmes en unités logiques discrètes.</span><span class="sxs-lookup"><span data-stu-id="34af0-148">Procedures allow you to break your programs into discrete logical units.</span></span> <span data-ttu-id="34af0-149">Vous pouvez déboguer des unités distinctes plus facilement qu’en déboguant un programme entier sans procédure.</span><span class="sxs-lookup"><span data-stu-id="34af0-149">You can debug separate units more easily than you can debug an entire program without procedures.</span></span>  
  
-   <span data-ttu-id="34af0-150">Après avoir développé des procédures pour les utiliser dans un programme, vous pouvez les utiliser dans d’autres programmes, avec peu ou pas de modifications.</span><span class="sxs-lookup"><span data-stu-id="34af0-150">After you develop procedures for use in one program, you can use them in other programs, often with little or no modification.</span></span> <span data-ttu-id="34af0-151">Cela vous évite une duplication de code.</span><span class="sxs-lookup"><span data-stu-id="34af0-151">This helps you avoid code duplication.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34af0-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="34af0-152">See Also</span></span>  
 <span data-ttu-id="34af0-153">[Guide pratique : créer une procédure](./how-to-create-a-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-153">[How to: Create a Procedure](./how-to-create-a-procedure.md) </span></span>  
 <span data-ttu-id="34af0-154">[Procédures Sub](./sub-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-154">[Sub Procedures](./sub-procedures.md) </span></span>  
 <span data-ttu-id="34af0-155">[Procédures Function](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-155">[Function Procedures](./function-procedures.md) </span></span>  
 <span data-ttu-id="34af0-156">[Procédures Property](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-156">[Property Procedures](./property-procedures.md) </span></span>  
 <span data-ttu-id="34af0-157">[Procédures Operator](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-157">[Operator Procedures](./operator-procedures.md) </span></span>  
 <span data-ttu-id="34af0-158">[Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-158">[Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
 <span data-ttu-id="34af0-159">[Procédures récursives](./recursive-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-159">[Recursive Procedures](./recursive-procedures.md) </span></span>  
 <span data-ttu-id="34af0-160">[Surcharge de procédure](./procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-160">[Procedure Overloading](./procedure-overloading.md) </span></span>  
 <span data-ttu-id="34af0-161">[Procédures génériques dans Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="34af0-161">[Generic Procedures in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md) </span></span>  
 [<span data-ttu-id="34af0-162">Objets et classes</span><span class="sxs-lookup"><span data-stu-id="34af0-162">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)

