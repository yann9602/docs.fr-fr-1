---
title: "Résolution à liaison tardive ; des erreurs d’exécution peuvent se produire"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords: BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d01164914b484ef689654f048a8743f3c2eb669
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="84c6e-102">Résolution à liaison tardive ; des erreurs d’exécution peuvent se produire</span><span class="sxs-lookup"><span data-stu-id="84c6e-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="84c6e-103">Un objet est assigné à une variable déclarée comme le [Type de données d’objet](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="84c6e-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="84c6e-104">Lorsque vous déclarez une variable en tant que `Object`, le compilateur doit exécuter *liaison tardive*, ce qui entraîne des opérations supplémentaires au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="84c6e-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="84c6e-105">Cela expose également votre application à des erreurs d’exécution potentielles.</span><span class="sxs-lookup"><span data-stu-id="84c6e-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="84c6e-106">Par exemple, si vous attribuez un <xref:System.Windows.Forms.Form> à la `Object` variable et puis essayez d’accéder à la <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> propriété, le runtime lève une <xref:System.MemberAccessException> , car le <xref:System.Windows.Forms.Form> n’expose pas de classe une `NameTable` propriété.</span><span class="sxs-lookup"><span data-stu-id="84c6e-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="84c6e-107">Si vous déclarez la variable comme étant d’un type spécifique, le compilateur peut exécuter *liaison anticipée* au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="84c6e-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="84c6e-108">Cela entraîne de meilleures performances, un accès contrôlé aux membres du type spécifique et une meilleure lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="84c6e-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="84c6e-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="84c6e-109">By default, this message is a warning.</span></span> <span data-ttu-id="84c6e-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="84c6e-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="84c6e-111">**ID d’erreur :** BC42017</span><span class="sxs-lookup"><span data-stu-id="84c6e-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="84c6e-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="84c6e-112">To correct this error</span></span>  
  
-   <span data-ttu-id="84c6e-113">Si possible, déclarez la variable comme étant d’un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="84c6e-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84c6e-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="84c6e-114">See Also</span></span>  
 [<span data-ttu-id="84c6e-115">Liaison anticipée et liaison tardive</span><span class="sxs-lookup"><span data-stu-id="84c6e-115">Early and Late Binding</span></span>](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [<span data-ttu-id="84c6e-116">Déclaration des variables objets</span><span class="sxs-lookup"><span data-stu-id="84c6e-116">Object Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
