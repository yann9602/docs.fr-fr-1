---
title: "Fonction &#39; &lt;nom_procédure&gt;&#39; n &#39; t retournent une valeur sur tous les chemins de code"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords: BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="77eae-102">Fonction &#39; &lt;nom_procédure&gt;&#39; n &#39; t retournent une valeur sur tous les chemins de code</span><span class="sxs-lookup"><span data-stu-id="77eae-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="77eae-103">Fonction '\<nom_procédure >' ne retourne pas une valeur pour tous les chemins de code.</span><span class="sxs-lookup"><span data-stu-id="77eae-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="77eae-104">Une instruction 'Return' est-elle manquante ?</span><span class="sxs-lookup"><span data-stu-id="77eae-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="77eae-105">A `Function` procédure possède au moins un chemin possible du code qui ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="77eae-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="77eae-106">Vous pouvez retourner une valeur depuis une `Function` procédure dans une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="77eae-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="77eae-107">Inclure la valeur dans un [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77eae-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="77eae-108">Assigner la valeur à la `Function` procédure nom, puis effectuez une `Exit Function` instruction.</span><span class="sxs-lookup"><span data-stu-id="77eae-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="77eae-109">Assigner la valeur à la `Function` procédure nom, puis effectuez la `End Function` instruction.</span><span class="sxs-lookup"><span data-stu-id="77eae-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="77eae-110">Si le contrôle passe à `Exit Function` ou `End Function` et que vous n’avez pas affecté n’importe quelle valeur pour le nom de la procédure, la procédure retourne la valeur par défaut du type de données de retour.</span><span class="sxs-lookup"><span data-stu-id="77eae-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="77eae-111">Pour plus d’informations, consultez « Comportement » dans [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="77eae-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="77eae-112">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="77eae-112">By default, this message is a warning.</span></span> <span data-ttu-id="77eae-113">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="77eae-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="77eae-114">**ID d’erreur :** BC42105</span><span class="sxs-lookup"><span data-stu-id="77eae-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="77eae-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="77eae-115">To correct this error</span></span>  
  
-   <span data-ttu-id="77eae-116">Vérifiez votre logique de flux de contrôle et assurez-vous que vous assignez une valeur avant chaque instruction qui provoque un retour.</span><span class="sxs-lookup"><span data-stu-id="77eae-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="77eae-117">Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours la `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="77eae-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="77eae-118">Dans ce cas, la dernière instruction avant `End Function` doit être un `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="77eae-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77eae-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="77eae-119">See Also</span></span>  
 [<span data-ttu-id="77eae-120">Procédures Function</span><span class="sxs-lookup"><span data-stu-id="77eae-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="77eae-121">Function (instruction)</span><span class="sxs-lookup"><span data-stu-id="77eae-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="77eae-122">Page Compiler, Concepteur de projet (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77eae-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
