---
title: "Propriété &#39; &lt;propertyname&gt;&#39; n &#39; t retournent une valeur sur tous les chemins de code"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords: BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="f8e89-102">Propriété &#39; &lt;propertyname&gt;&#39; n &#39; t retournent une valeur sur tous les chemins de code</span><span class="sxs-lookup"><span data-stu-id="f8e89-102">Property &#39;&lt;propertyname&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="f8e89-103">Propriété '\<nom_propriété >' ne retourne pas une valeur pour tous les chemins de code.</span><span class="sxs-lookup"><span data-stu-id="f8e89-103">Property '\<propertyname>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="f8e89-104">Une exception de référence null peut se produire au moment de l'exécution lorsque le résultat est utilisé.</span><span class="sxs-lookup"><span data-stu-id="f8e89-104">A null reference exception could occur at run time when the result is used.</span></span>  
  
 <span data-ttu-id="f8e89-105">Une propriété `Get` procédure possède au moins un chemin possible du code qui ne retourne pas de valeur.</span><span class="sxs-lookup"><span data-stu-id="f8e89-105">A property `Get` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="f8e89-106">Vous pouvez retourner une valeur d’une propriété `Get` procédure dans une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="f8e89-106">You can return a value from a property `Get` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="f8e89-107">Assignez la valeur au nom de propriété, puis exécutez une `Exit Property` instruction.</span><span class="sxs-lookup"><span data-stu-id="f8e89-107">Assign the value to the property name and then perform an `Exit Property` statement.</span></span>  
  
-   <span data-ttu-id="f8e89-108">Assignez la valeur au nom de propriété, puis exécutez la `End Get` instruction.</span><span class="sxs-lookup"><span data-stu-id="f8e89-108">Assign the value to the property name and then perform the `End Get` statement.</span></span>  
  
-   <span data-ttu-id="f8e89-109">Inclure la valeur dans un [instruction Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f8e89-109">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="f8e89-110">Si le contrôle passe à `Exit Property` ou `End Get` et vous n’avez pas affecté n’importe quelle valeur au nom de propriété, le `Get` procédure retourne la valeur par défaut de la propriété type de données.</span><span class="sxs-lookup"><span data-stu-id="f8e89-110">If control passes to `Exit Property` or `End Get` and you have not assigned any value to the property name, the `Get` procedure returns the default value of the property's data type.</span></span> <span data-ttu-id="f8e89-111">Pour plus d’informations, consultez « Comportement » dans [Function, instruction](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="f8e89-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="f8e89-112">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="f8e89-112">By default, this message is a warning.</span></span> <span data-ttu-id="f8e89-113">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f8e89-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f8e89-114">**ID d’erreur :** BC42107</span><span class="sxs-lookup"><span data-stu-id="f8e89-114">**Error ID:** BC42107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f8e89-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f8e89-115">To correct this error</span></span>  
  
-   <span data-ttu-id="f8e89-116">Vérifiez votre logique de flux de contrôle et assurez-vous que vous assignez une valeur avant chaque instruction qui provoque un retour.</span><span class="sxs-lookup"><span data-stu-id="f8e89-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="f8e89-117">Il est plus facile de garantir que chaque retour de la procédure retourne une valeur si vous utilisez toujours la `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="f8e89-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="f8e89-118">Dans ce cas, la dernière instruction avant `End Get` doit être un `Return` instruction.</span><span class="sxs-lookup"><span data-stu-id="f8e89-118">If you do this, the last statement before `End Get` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8e89-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8e89-119">See Also</span></span>  
 [<span data-ttu-id="f8e89-120">Procédures de propriété</span><span class="sxs-lookup"><span data-stu-id="f8e89-120">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="f8e89-121">Property (instruction)</span><span class="sxs-lookup"><span data-stu-id="f8e89-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="f8e89-122">Get (instruction)</span><span class="sxs-lookup"><span data-stu-id="f8e89-122">Get Statement</span></span>](../../../visual-basic/language-reference/statements/get-statement.md)
