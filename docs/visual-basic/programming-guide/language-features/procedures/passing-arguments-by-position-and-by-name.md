---
title: Passage des arguments par position et par nom (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 164f69fcf23049441a0acbe05058c792d5363a03
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a><span data-ttu-id="a1a31-102">Passage des arguments par position et par nom (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1a31-102">Passing Arguments by Position and by Name (Visual Basic)</span></span>
<span data-ttu-id="a1a31-103">Lorsque vous appelez un `Sub` ou `Function` procédure, vous pouvez passer des arguments *par position* , dans l’ordre dans lequel elles apparaissent dans la définition de la procédure, ou vous pouvez passer les *par nom*, sans vu les positionner.</span><span class="sxs-lookup"><span data-stu-id="a1a31-103">When you call a `Sub` or `Function` procedure, you can pass arguments *by position* — in the order in which they appear in the procedure's definition — or you can pass them *by name*, without regard to position.</span></span>  
  
 <span data-ttu-id="a1a31-104">Lorsque vous passez un argument par nom, vous spécifiez l’argument déclaré de le nom suivi d’un signe deux-points et un signe égal (`:=`), suivi par la valeur d’argument.</span><span class="sxs-lookup"><span data-stu-id="a1a31-104">When you pass an argument by name, you specify the argument's declared name followed by a colon and an equal sign (`:=`), followed by the argument value.</span></span> <span data-ttu-id="a1a31-105">Vous pouvez fournir des arguments nommés dans n’importe quel ordre.</span><span class="sxs-lookup"><span data-stu-id="a1a31-105">You can supply named arguments in any order.</span></span>  
  
 <span data-ttu-id="a1a31-106">Par exemple, les éléments suivants `Sub` procédure prend trois arguments :</span><span class="sxs-lookup"><span data-stu-id="a1a31-106">For example, the following `Sub` procedure takes three arguments:</span></span>  
  
 [!code-vb[VbVbcnProcedures#41](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_1.vb)]  
  
 <span data-ttu-id="a1a31-107">Lorsque vous appelez cette procédure, vous pouvez fournir les arguments par position, par nom ou à l’aide d’une combinaison des deux.</span><span class="sxs-lookup"><span data-stu-id="a1a31-107">When you call this procedure, you can supply the arguments by position, by name, or by using a mixture of both.</span></span>  
  
## <a name="passing-arguments-by-position"></a><span data-ttu-id="a1a31-108">Passage des Arguments par Position</span><span class="sxs-lookup"><span data-stu-id="a1a31-108">Passing Arguments by Position</span></span>  
 <span data-ttu-id="a1a31-109">Vous pouvez appeler la procédure `studentInfo` avec des arguments passés par position et délimités par des virgules, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a1a31-109">You can call the procedure `studentInfo` with its arguments passed by position and delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#42](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_2.vb)]  
  
 <span data-ttu-id="a1a31-110">Si vous omettez un argument facultatif dans une liste d’arguments positionnels, vous devez marquer son emplacement avec une virgule.</span><span class="sxs-lookup"><span data-stu-id="a1a31-110">If you omit an optional argument in a positional argument list, you must hold its place with a comma.</span></span> <span data-ttu-id="a1a31-111">L’exemple suivant appelle `studentInfo` sans le `age` argument :</span><span class="sxs-lookup"><span data-stu-id="a1a31-111">The following example calls `studentInfo` without the `age` argument:</span></span>  
  
 [!code-vb[VbVbcnProcedures#43](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_3.vb)]  
  
## <a name="passing-arguments-by-name"></a><span data-ttu-id="a1a31-112">Passage des Arguments par nom</span><span class="sxs-lookup"><span data-stu-id="a1a31-112">Passing Arguments by Name</span></span>  
 <span data-ttu-id="a1a31-113">Vous pouvez également appeler `studentInfo` avec les arguments passés par nom, également délimitées par des virgules, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a1a31-113">Alternatively, you can call `studentInfo` with the arguments passed by name, also delimited by commas, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#44](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_4.vb)]  
  
## <a name="mixing-arguments-by-position-and-by-name"></a><span data-ttu-id="a1a31-114">Mélange d’Arguments par Position et par nom</span><span class="sxs-lookup"><span data-stu-id="a1a31-114">Mixing Arguments by Position and by Name</span></span>  
 <span data-ttu-id="a1a31-115">Vous pouvez fournir des arguments par position et par nom dans un seul appel de procédure, comme indiqué dans l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="a1a31-115">You can supply arguments both by position and by name in a single procedure call, as shown in the following example:</span></span>  
  
 [!code-vb[VbVbcnProcedures#45](./codesnippet/VisualBasic/passing-arguments-by-position-and-by-name_5.vb)]  
  
 <span data-ttu-id="a1a31-116">Dans l’exemple précédent, aucune virgule supplémentaire n’est nécessaire pour marquer l’emplacement de l’indication `age` argument, étant donné que `birth` est passé par nom.</span><span class="sxs-lookup"><span data-stu-id="a1a31-116">In the preceding example, no extra comma is necessary to hold the place of the omitted `age` argument, since `birth` is passed by name.</span></span>  
  
 <span data-ttu-id="a1a31-117">Lorsque vous fournissez des arguments par un mélange de position et le nom, les arguments positionnels doivent tous figurer en premier.</span><span class="sxs-lookup"><span data-stu-id="a1a31-117">When you supply arguments by a mixture of position and name, the positional arguments must all come first.</span></span> <span data-ttu-id="a1a31-118">Une fois que vous fournissez un argument par nom, les arguments restants doivent tous être par nom.</span><span class="sxs-lookup"><span data-stu-id="a1a31-118">Once you supply an argument by name, the remaining arguments must all be by name.</span></span>  
  
## <a name="supplying-optional-arguments-by-name"></a><span data-ttu-id="a1a31-119">Spécification d’Arguments facultatifs par nom</span><span class="sxs-lookup"><span data-stu-id="a1a31-119">Supplying Optional Arguments by Name</span></span>  
 <span data-ttu-id="a1a31-120">Passer des arguments par nom est particulièrement utile lorsque vous appelez une procédure qui possède plusieurs arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="a1a31-120">Passing arguments by name is especially useful when you call a procedure that has more than one optional argument.</span></span> <span data-ttu-id="a1a31-121">Si vous fournissez des arguments par nom, vous n’avez pas à utiliser des virgules successives pour signaler l’absence d’arguments de position.</span><span class="sxs-lookup"><span data-stu-id="a1a31-121">If you supply arguments by name, you do not have to use consecutive commas to denote missing positional arguments.</span></span> <span data-ttu-id="a1a31-122">Passer des arguments par nom facilite également suivre les arguments que vous passez et ceux qui sont omis.</span><span class="sxs-lookup"><span data-stu-id="a1a31-122">Passing arguments by name also makes it easier to keep track of which arguments you are passing and which ones you are omitting.</span></span>  
  
## <a name="restrictions-on-supplying-arguments-by-name"></a><span data-ttu-id="a1a31-123">Restrictions sur la fourniture des Arguments par nom</span><span class="sxs-lookup"><span data-stu-id="a1a31-123">Restrictions on Supplying Arguments by Name</span></span>  
 <span data-ttu-id="a1a31-124">Vous ne peut pas passer d’arguments par nom pour éviter d’entrer des arguments requis.</span><span class="sxs-lookup"><span data-stu-id="a1a31-124">You cannot pass arguments by name to avoid entering required arguments.</span></span> <span data-ttu-id="a1a31-125">Vous pouvez omettre que les arguments facultatifs.</span><span class="sxs-lookup"><span data-stu-id="a1a31-125">You can omit only the optional arguments.</span></span>  
  
 <span data-ttu-id="a1a31-126">Vous ne pouvez pas passer un tableau de paramètres par nom.</span><span class="sxs-lookup"><span data-stu-id="a1a31-126">You cannot pass a parameter array by name.</span></span> <span data-ttu-id="a1a31-127">Il s’agit, car lorsque vous appelez la procédure, vous indiquez un nombre indéfini d’arguments de séparées par des virgules pour le tableau de paramètres, et le compilateur ne peut pas associer plusieurs arguments avec un nom unique.</span><span class="sxs-lookup"><span data-stu-id="a1a31-127">This is because when you call the procedure, you supply an indefinite number of comma-separated arguments for the parameter array, and the compiler cannot associate more than one argument with a single name.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1a31-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a1a31-128">See Also</span></span>  
 [<span data-ttu-id="a1a31-129">Procédures</span><span class="sxs-lookup"><span data-stu-id="a1a31-129">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="a1a31-130">Paramètres et arguments d’une procédure</span><span class="sxs-lookup"><span data-stu-id="a1a31-130">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="a1a31-131">Guide pratique : passer des arguments à une procédure</span><span class="sxs-lookup"><span data-stu-id="a1a31-131">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="a1a31-132">Passage d’un argument par valeur et par référence</span><span class="sxs-lookup"><span data-stu-id="a1a31-132">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="a1a31-133">Paramètres facultatifs</span><span class="sxs-lookup"><span data-stu-id="a1a31-133">Optional Parameters</span></span>](./optional-parameters.md)  
 [<span data-ttu-id="a1a31-134">tableaux de paramètres</span><span class="sxs-lookup"><span data-stu-id="a1a31-134">Parameter Arrays</span></span>](./parameter-arrays.md)  
 [<span data-ttu-id="a1a31-135">Optional</span><span class="sxs-lookup"><span data-stu-id="a1a31-135">Optional</span></span>](../../../../visual-basic/language-reference/modifiers/optional.md)  
 [<span data-ttu-id="a1a31-136">ParamArray</span><span class="sxs-lookup"><span data-stu-id="a1a31-136">ParamArray</span></span>](../../../../visual-basic/language-reference/modifiers/paramarray.md)
