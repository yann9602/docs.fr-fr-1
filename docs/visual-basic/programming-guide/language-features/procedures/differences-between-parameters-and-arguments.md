---
title: "Différences entre les paramètres et les arguments (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- parameters [Visual Basic], and arguments
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], and parameters
- procedure parameters
- parameters [Visual Basic], definition
ms.assetid: c237c056-74f4-4749-9f2c-15864f139a31
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6613c64a24ef18239422b69f8b5320eadc95b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-parameters-and-arguments-visual-basic"></a><span data-ttu-id="469c7-102">Différences entre les paramètres et les arguments (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="469c7-102">Differences Between Parameters and Arguments (Visual Basic)</span></span>
<span data-ttu-id="469c7-103">Dans la plupart des cas, une procédure doit avoir des informations sur les circonstances dans lesquelles elle a été appelée.</span><span class="sxs-lookup"><span data-stu-id="469c7-103">In most cases, a procedure must have some information about the circumstances in which it has been called.</span></span> <span data-ttu-id="469c7-104">Une procédure qui exécute des tâches répétitives ou partagées utilise des informations différentes pour chaque appel.</span><span class="sxs-lookup"><span data-stu-id="469c7-104">A procedure that performs repeated or shared tasks uses different information for each call.</span></span> <span data-ttu-id="469c7-105">Ces informations se composent des variables, des constantes et des expressions que vous passez à la procédure lorsque vous appelez.</span><span class="sxs-lookup"><span data-stu-id="469c7-105">This information consists of variables, constants, and expressions that you pass to the procedure when you call it.</span></span>  
  
 <span data-ttu-id="469c7-106">Pour communiquer ces informations à la procédure, la procédure définit un *paramètre*, et le code appelant passe un *argument* à ce paramètre.</span><span class="sxs-lookup"><span data-stu-id="469c7-106">To communicate this information to the procedure, the procedure defines a *parameter*, and the calling code passes an *argument* to that parameter.</span></span> <span data-ttu-id="469c7-107">Vous pouvez considérer le paramètre comme un espace de parking et l’argument comme une voiture.</span><span class="sxs-lookup"><span data-stu-id="469c7-107">You can think of the parameter as a parking space and the argument as an automobile.</span></span> <span data-ttu-id="469c7-108">De même que plusieurs automobiles peuvent se dans un espace de parking à des moments différents, le code appelant peut passer un argument différent au même paramètre chaque fois qu’il appelle la procédure.</span><span class="sxs-lookup"><span data-stu-id="469c7-108">Just as different automobiles can park in a parking space at different times, the calling code can pass a different argument to the same parameter every time that it calls the procedure.</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="469c7-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="469c7-109">Parameters</span></span>  
 <span data-ttu-id="469c7-110">A *paramètre* représente une valeur de la procédure que vous devez passer lorsque vous appelez.</span><span class="sxs-lookup"><span data-stu-id="469c7-110">A *parameter* represents a value that the procedure expects you to pass when you call it.</span></span> <span data-ttu-id="469c7-111">Déclaration de la procédure définit ses paramètres.</span><span class="sxs-lookup"><span data-stu-id="469c7-111">The procedure's declaration defines its parameters.</span></span>  
  
 <span data-ttu-id="469c7-112">Lorsque vous définissez un `Function` ou `Sub` procédure, vous spécifiez un *liste de paramètres* entre parenthèses le nom de la procédure qui suit immédiatement.</span><span class="sxs-lookup"><span data-stu-id="469c7-112">When you define a `Function` or `Sub` procedure, you specify a *parameter list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="469c7-113">Pour chaque paramètre, vous spécifiez un nom, un type de données et un mécanisme de passage ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) ou [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span><span class="sxs-lookup"><span data-stu-id="469c7-113">For each parameter, you specify a name, a data type, and a passing mechanism ([ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)).</span></span> <span data-ttu-id="469c7-114">Vous pouvez également indiquer qu’un paramètre est facultatif.</span><span class="sxs-lookup"><span data-stu-id="469c7-114">You can also indicate that a parameter is optional.</span></span> <span data-ttu-id="469c7-115">Cela signifie que le code appelant ne dispose pas de passer une valeur pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="469c7-115">This means that the calling code does not have to pass a value for it.</span></span>  
  
 <span data-ttu-id="469c7-116">Le nom de chaque paramètre sert un *variable locale* dans la procédure.</span><span class="sxs-lookup"><span data-stu-id="469c7-116">The name of each parameter serves as a *local variable* in the procedure.</span></span> <span data-ttu-id="469c7-117">Vous utilisez le nom du paramètre de la même façon que vous utilisez toute autre variable.</span><span class="sxs-lookup"><span data-stu-id="469c7-117">You use the parameter name the same way you use any other variable.</span></span>  
  
## <a name="arguments"></a><span data-ttu-id="469c7-118">Arguments</span><span class="sxs-lookup"><span data-stu-id="469c7-118">Arguments</span></span>  
 <span data-ttu-id="469c7-119">Un *argument* représente la valeur que vous passez à un paramètre de procédure lorsque vous appelez la procédure.</span><span class="sxs-lookup"><span data-stu-id="469c7-119">An *argument* represents the value that you pass to a procedure parameter when you call the procedure.</span></span> <span data-ttu-id="469c7-120">Le code appelant fournit les arguments lorsqu’il appelle la procédure.</span><span class="sxs-lookup"><span data-stu-id="469c7-120">The calling code supplies the arguments when it calls the procedure.</span></span>  
  
 <span data-ttu-id="469c7-121">Lorsque vous appelez un `Function` ou `Sub` procédure, vous incluez un *liste d’arguments* entre parenthèses le nom de la procédure qui suit immédiatement.</span><span class="sxs-lookup"><span data-stu-id="469c7-121">When you call a `Function` or `Sub` procedure, you include an *argument list* in parentheses immediately following the procedure name.</span></span> <span data-ttu-id="469c7-122">Chaque argument correspond au paramètre dans la même position dans la liste.</span><span class="sxs-lookup"><span data-stu-id="469c7-122">Each argument corresponds to the parameter in the same position in the list.</span></span>  
  
 <span data-ttu-id="469c7-123">Contrairement à la définition des paramètres, arguments n’ont pas de noms.</span><span class="sxs-lookup"><span data-stu-id="469c7-123">In contrast to parameter definition, arguments do not have names.</span></span> <span data-ttu-id="469c7-124">Chaque argument est une expression qui peut contenir zéro ou plusieurs variables, de constantes et des littéraux.</span><span class="sxs-lookup"><span data-stu-id="469c7-124">Each argument is an expression, which can contain zero or more variables, constants, and literals.</span></span> <span data-ttu-id="469c7-125">Le type de données de l’expression évaluée doit correspondre en général, le type de données défini pour le paramètre correspondant, et dans tous les cas, il doit être convertible au type de paramètre.</span><span class="sxs-lookup"><span data-stu-id="469c7-125">The data type of the evaluated expression should typically match the data type defined for the corresponding parameter, and in any case it must be convertible to the parameter type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="469c7-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="469c7-126">See Also</span></span>  
 [<span data-ttu-id="469c7-127">Procédures</span><span class="sxs-lookup"><span data-stu-id="469c7-127">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="469c7-128">Procédures Sub</span><span class="sxs-lookup"><span data-stu-id="469c7-128">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="469c7-129">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="469c7-129">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="469c7-130">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="469c7-130">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="469c7-131">Procédures d’opérateur</span><span class="sxs-lookup"><span data-stu-id="469c7-131">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="469c7-132">Guide pratique : définir un paramètre pour une procédure</span><span class="sxs-lookup"><span data-stu-id="469c7-132">How to: Define a Parameter for a Procedure</span></span>](./how-to-define-a-parameter-for-a-procedure.md)  
 [<span data-ttu-id="469c7-133">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="469c7-133">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="469c7-134">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="469c7-134">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="469c7-135">Procédures récursives</span><span class="sxs-lookup"><span data-stu-id="469c7-135">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="469c7-136">Surcharge de procédure</span><span class="sxs-lookup"><span data-stu-id="469c7-136">Procedure Overloading</span></span>](./procedure-overloading.md)
