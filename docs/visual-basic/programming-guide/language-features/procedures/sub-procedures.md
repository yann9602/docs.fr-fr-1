---
title: "Sub de procédures (Visual Basic) | Documents Microsoft"
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
- Sub procedures, about Sub procedures
- statement blocks
- Sub procedures, calling
- procedures, calling
- Sub procedures, syntax
- Sub procedures
- procedures, Sub
- syntax, Sub procedures
ms.assetid: 6a0a4958-ed0a-4d3d-8d31-0772c82bda58
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
ms.openlocfilehash: 83f0a16498accf383da96d702c4e3a4b7de1c861
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="sub-procedures-visual-basic"></a><span data-ttu-id="f1aa1-102">Procédures Sub (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1aa1-102">Sub Procedures (Visual Basic)</span></span>
<span data-ttu-id="f1aa1-103">A `Sub` procédure est une série de [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] instructions placées par le `Sub` et `End Sub` instructions.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-103">A `Sub` procedure is a series of [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] statements enclosed by the `Sub` and `End Sub` statements.</span></span> <span data-ttu-id="f1aa1-104">Le `Sub` procédure effectue une tâche, puis retourne le contrôle au code appelant, mais elle ne retourne pas de valeur au code appelant.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-104">The `Sub` procedure performs a task and then returns control to the calling code, but it does not return a value to the calling code.</span></span>  
  
 <span data-ttu-id="f1aa1-105">Chaque fois que la procédure est appelée, ses instructions sont exécutées à partir de la première instruction exécutable après le `Sub` instruction et se terminant par la première `End Sub`, `Exit Sub`, ou `Return` instruction rencontrée.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-105">Each time the procedure is called, its statements are executed, starting with the first executable statement after the `Sub` statement and ending with the first `End Sub`, `Exit Sub`, or `Return` statement encountered.</span></span>  
  
 <span data-ttu-id="f1aa1-106">Vous pouvez définir un `Sub` procédure dans les modules, les classes et structures.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-106">You can define a `Sub` procedure in modules, classes, and structures.</span></span> <span data-ttu-id="f1aa1-107">Par défaut, il est `Public`, ce qui signifie que vous pouvez l’appeler depuis n’importe où dans votre application qui a accès au module, classe ou une structure dans laquelle vous définie.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-107">By default, it is `Public`, which means you can call it from anywhere in your application that has access to the module, class, or structure in which you defined it.</span></span> <span data-ttu-id="f1aa1-108">Le terme *méthode*, décrit une `Sub` ou `Function` procédure qui est accessible en dehors de sa définition de module, classe ou structure.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-108">The term, *method*, describes a `Sub` or `Function` procedure that is accessed from outside its defining module, class, or structure.</span></span> <span data-ttu-id="f1aa1-109">Pour plus d’informations, consultez [procédures](./index.md).</span><span class="sxs-lookup"><span data-stu-id="f1aa1-109">For more information, see [Procedures](./index.md).</span></span>  
  
 <span data-ttu-id="f1aa1-110">Un `Sub` procédure peut prendre des arguments, tels que les constantes, variables ou expressions qui sont passées par le code appelant.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-110">A `Sub` procedure can take arguments, such as constants, variables, or expressions, which are passed to it by the calling code.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="f1aa1-111">Syntaxe de déclaration</span><span class="sxs-lookup"><span data-stu-id="f1aa1-111">Declaration Syntax</span></span>  
 <span data-ttu-id="f1aa1-112">La syntaxe de déclaration d’un `Sub` comme suit :</span><span class="sxs-lookup"><span data-stu-id="f1aa1-112">The syntax for declaring a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="f1aa1-113">`[`*modifiers* `] Sub`*subname* `[(` *parameterlist*  `)]`</span><span class="sxs-lookup"><span data-stu-id="f1aa1-113">`[` *modifiers* `] Sub`  *subname* `[(` *parameterlist* `)]`</span></span>  
  
 `' Statements of the Sub procedure.`  
  
 `End Sub`  
  
 <span data-ttu-id="f1aa1-114">Le `modifiers` peut spécifier de niveau d’accès et des informations sur la surcharge, la substitution, le partage et l’occultation.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-114">The `modifiers` can specify access level and information about overloading, overriding, sharing, and shadowing.</span></span> <span data-ttu-id="f1aa1-115">Pour plus d’informations, consultez [Sub, instruction](../../../../visual-basic/language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f1aa1-115">For more information, see [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md).</span></span>  
  
## <a name="parameter-declaration"></a><span data-ttu-id="f1aa1-116">Déclaration de paramètre</span><span class="sxs-lookup"><span data-stu-id="f1aa1-116">Parameter Declaration</span></span>  
 <span data-ttu-id="f1aa1-117">Vous déclarez chaque paramètre de procédure de la même façon à comment vous déclarez une variable, en spécifiant le type de données et le nom du paramètre.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-117">You declare each procedure parameter similarly to how you declare a variable, specifying the parameter name and data type.</span></span> <span data-ttu-id="f1aa1-118">Vous pouvez également spécifier le mécanisme de passage et si le paramètre est facultatif ou un tableau de paramètres.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-118">You can also specify the passing mechanism, and whether the parameter is optional or a parameter array.</span></span>  
  
 <span data-ttu-id="f1aa1-119">La syntaxe de chaque paramètre dans la liste des paramètres est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f1aa1-119">The syntax for each parameter in the parameter list is as follows:</span></span>  
  
 <span data-ttu-id="f1aa1-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *ParameterName*`As`*type de données    *</span><span class="sxs-lookup"><span data-stu-id="f1aa1-120">`[Optional] [ByVal | ByRef] [ParamArray]`  *parametername*  `As`  *datatype*</span></span>  
  
 <span data-ttu-id="f1aa1-121">Si le paramètre est facultatif, vous devez également fournir une valeur par défaut dans le cadre de sa déclaration.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-121">If the parameter is optional, you must also supply a default value as part of its declaration.</span></span> <span data-ttu-id="f1aa1-122">La syntaxe de spécification d’une valeur par défaut est la suivante :</span><span class="sxs-lookup"><span data-stu-id="f1aa1-122">The syntax for specifying a default value is as follows:</span></span>  
  
 <span data-ttu-id="f1aa1-123">`Optional [ByVal | ByRef]`  *ParameterName*`As`*type de données*`=`*defaultvalue        *</span><span class="sxs-lookup"><span data-stu-id="f1aa1-123">`Optional [ByVal | ByRef]`  *parametername*  `As`  *datatype*  `=`  *defaultvalue*</span></span>  
  
### <a name="parameters-as-local-variables"></a><span data-ttu-id="f1aa1-124">Paramètres en tant que Variables locales</span><span class="sxs-lookup"><span data-stu-id="f1aa1-124">Parameters as Local Variables</span></span>  
 <span data-ttu-id="f1aa1-125">Lorsque le contrôle passe à la procédure, chaque paramètre est traité comme une variable locale.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-125">When control passes to the procedure, each parameter is treated as a local variable.</span></span> <span data-ttu-id="f1aa1-126">Cela signifie que sa durée de vie est la même que celle de la procédure, et son étendue est l’ensemble de la procédure.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-126">This means that its lifetime is the same as that of the procedure, and its scope is the whole procedure.</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="f1aa1-127">Syntaxe d’appel</span><span class="sxs-lookup"><span data-stu-id="f1aa1-127">Calling Syntax</span></span>  
 <span data-ttu-id="f1aa1-128">Vous appelez un `Sub` procédure explicitement avec une instruction d’appel autonome.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-128">You invoke a `Sub` procedure explicitly with a stand-alone calling statement.</span></span> <span data-ttu-id="f1aa1-129">Vous ne pouvez pas l’appeler en utilisant son nom dans une expression.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-129">You cannot call it by using its name in an expression.</span></span> <span data-ttu-id="f1aa1-130">Vous devez fournir des valeurs pour tous les arguments qui ne sont pas facultatifs, et vous devez placer la liste d’arguments entre parenthèses.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-130">You must provide values for all arguments that are not optional, and you must enclose the argument list in parentheses.</span></span> <span data-ttu-id="f1aa1-131">Si aucun argument n’est fourni, vous pouvez omettre les parenthèses.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-131">If no arguments are supplied, you can optionally omit the parentheses.</span></span> <span data-ttu-id="f1aa1-132">L’utilisation de la `Call` mot clé est facultatif, mais non recommandée.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-132">The use of the `Call` keyword is optional but not recommended.</span></span>  
  
 <span data-ttu-id="f1aa1-133">La syntaxe d’un appel à une `Sub` comme suit :</span><span class="sxs-lookup"><span data-stu-id="f1aa1-133">The syntax for a call to a `Sub` procedure is as follows:</span></span>  
  
 <span data-ttu-id="f1aa1-134">`[Call]`  *nomsub* `[(` *argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="f1aa1-134">`[Call]`  *subname* `[(` *argumentlist* `)]`</span></span>  
  
 <span data-ttu-id="f1aa1-135">Vous pouvez appeler une `Sub` méthode en dehors de la classe qui le définit.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-135">You can call a `Sub` method from outside the class that defines it.</span></span> <span data-ttu-id="f1aa1-136">Tout d’abord, vous devez utiliser le `New` (mot clé) pour créer une instance de la classe ou appeler une méthode qui retourne une instance de la classe.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-136">First, you have to use the `New` keyword to create an instance of the class, or call a method that returns an instance of the class.</span></span> <span data-ttu-id="f1aa1-137">Pour plus d’informations, consultez [nouveau opérateur](../../../../visual-basic/language-reference/operators/new-operator.md).</span><span class="sxs-lookup"><span data-stu-id="f1aa1-137">For more information, see [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md).</span></span> <span data-ttu-id="f1aa1-138">Ensuite, vous pouvez utiliser la syntaxe suivante pour appeler le `Sub` méthode sur l’objet d’instance :</span><span class="sxs-lookup"><span data-stu-id="f1aa1-138">Then, you can use the following syntax to call the `Sub` method on the instance object:</span></span>  
  
 <span data-ttu-id="f1aa1-139">*Object*.* MethodName*`[(`*argumentlist*`)]`</span><span class="sxs-lookup"><span data-stu-id="f1aa1-139">*Object*.*methodname*`[(`*argumentlist*`)]`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="f1aa1-140">Illustration de déclaration et d’appel</span><span class="sxs-lookup"><span data-stu-id="f1aa1-140">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="f1aa1-141">Les éléments suivants `Sub` procédure indique à l’opérateur la tâche que l’application est sur le point d’exécuter et affiche également un horodatage.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-141">The following `Sub` procedure tells the computer operator which task the application is about to perform, and also displays a time stamp.</span></span> <span data-ttu-id="f1aa1-142">Au lieu de dupliquer ce code au début de chaque tâche, l’application appelle simplement `tellOperator` à partir de différents emplacements.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-142">Instead of duplicating this code at the start of every task, the application just calls `tellOperator` from various locations.</span></span> <span data-ttu-id="f1aa1-143">Chaque appel passe une chaîne dans le `task` qui identifie la tâche en cours de démarrage.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-143">Each call passes a string in the `task` argument that identifies the task being started.</span></span>  
  
 <span data-ttu-id="f1aa1-144">[!code-vb[VbVbcnProcedures n °&2;](./codesnippet/VisualBasic/sub-procedures_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f1aa1-144">[!code-vb[VbVbcnProcedures#2](./codesnippet/VisualBasic/sub-procedures_1.vb)]</span></span>  
  
 <span data-ttu-id="f1aa1-145">L’exemple suivant montre un appel typique à `tellOperator`.</span><span class="sxs-lookup"><span data-stu-id="f1aa1-145">The following example shows a typical call to `tellOperator`.</span></span>  
  
 <span data-ttu-id="f1aa1-146">[!code-vb[VbVbcnProcedures n °&3;](./codesnippet/VisualBasic/sub-procedures_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="f1aa1-146">[!code-vb[VbVbcnProcedures#3](./codesnippet/VisualBasic/sub-procedures_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1aa1-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f1aa1-147">See Also</span></span>  
 <span data-ttu-id="f1aa1-148">[Procédures](./index.md) </span><span class="sxs-lookup"><span data-stu-id="f1aa1-148">[Procedures](./index.md) </span></span>  
<span data-ttu-id="f1aa1-149"> [Procédures Function](./function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f1aa1-149"> [Function Procedures](./function-procedures.md) </span></span>  
<span data-ttu-id="f1aa1-150"> [Procédures de propriété](./property-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f1aa1-150"> [Property Procedures](./property-procedures.md) </span></span>  
<span data-ttu-id="f1aa1-151"> [Procédures d’opérateur](./operator-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="f1aa1-151"> [Operator Procedures](./operator-procedures.md) </span></span>  
<span data-ttu-id="f1aa1-152"> [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md) </span><span class="sxs-lookup"><span data-stu-id="f1aa1-152"> [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md) </span></span>  
<span data-ttu-id="f1aa1-153"> [Sub (instruction)](../../../../visual-basic/language-reference/statements/sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="f1aa1-153"> [Sub Statement](../../../../visual-basic/language-reference/statements/sub-statement.md) </span></span>  
<span data-ttu-id="f1aa1-154"> [Comment : appeler une procédure qui ne retourne pas de valeur](./how-to-call-a-procedure-that-does-not-return-a-value.md) </span><span class="sxs-lookup"><span data-stu-id="f1aa1-154"> [How to: Call a Procedure that Does Not Return a Value](./how-to-call-a-procedure-that-does-not-return-a-value.md) </span></span>  
<span data-ttu-id="f1aa1-155"> [Comment : appeler un gestionnaire d’événements en Visual Basic](./how-to-call-an-event-handler.md)</span><span class="sxs-lookup"><span data-stu-id="f1aa1-155"> [How to: Call an Event Handler in Visual Basic](./how-to-call-an-event-handler.md)</span></span>
