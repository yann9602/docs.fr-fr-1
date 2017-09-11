---
title: "Résolution à liaison tardive ; erreurs d’exécution peuvent se produire | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
dev_langs:
- VB
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
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
ms.openlocfilehash: 3baf28a17077d255b42f38ade21ce6153c24e862
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a><span data-ttu-id="f0115-102">Résolution à liaison tardive ; des erreurs d’exécution peuvent se produire</span><span class="sxs-lookup"><span data-stu-id="f0115-102">Late bound resolution; runtime errors could occur</span></span>
<span data-ttu-id="f0115-103">Un objet est assigné à une variable déclarée comme le [Type de données Object](../../../visual-basic/language-reference/data-types/object-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="f0115-103">An object is assigned to a variable declared to be of the [Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md).</span></span>  
  
 <span data-ttu-id="f0115-104">Lorsque vous déclarez une variable en tant que `Object`, le compilateur doit exécuter *liaison tardive*, ce qui provoque des opérations supplémentaires au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f0115-104">When you declare a variable as `Object`, the compiler must perform *late binding*, which causes extra operations at run time.</span></span> <span data-ttu-id="f0115-105">Cela expose également votre application à des erreurs d’exécution potentielles.</span><span class="sxs-lookup"><span data-stu-id="f0115-105">It also exposes your application to potential run-time errors.</span></span> <span data-ttu-id="f0115-106">Par exemple, si vous attribuez un <xref:System.Windows.Forms.Form>à la `Object` variable et réessayez d’accéder à la <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>propriété, le runtime lève une <xref:System.MemberAccessException>car le <xref:System.Windows.Forms.Form>n’expose pas de classe une `NameTable` propriété.</xref:System.Windows.Forms.Form> </xref:System.MemberAccessException> </xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> </xref:System.Windows.Forms.Form></span><span class="sxs-lookup"><span data-stu-id="f0115-106">For example, if you assign a <xref:System.Windows.Forms.Form> to the `Object` variable and then try to access the <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> property, the runtime throws a <xref:System.MemberAccessException> because the <xref:System.Windows.Forms.Form> class does not expose a `NameTable` property.</span></span>  
  
 <span data-ttu-id="f0115-107">Si vous déclarez la variable comme étant d’un type spécifique, le compilateur peut exécuter *liaison anticipée* au moment de la compilation.</span><span class="sxs-lookup"><span data-stu-id="f0115-107">If you declare the variable to be of a specific type, the compiler can perform *early binding* at compile time.</span></span> <span data-ttu-id="f0115-108">Cela entraîne des performances améliorées, un accès contrôlé aux membres du type spécifique et une meilleure lisibilité de votre code.</span><span class="sxs-lookup"><span data-stu-id="f0115-108">This results in improved performance, controlled access to the members of the specific type, and better readability of your code.</span></span>  
  
 <span data-ttu-id="f0115-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="f0115-109">By default, this message is a warning.</span></span> <span data-ttu-id="f0115-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f0115-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f0115-111">**ID d’erreur :** BC42017</span><span class="sxs-lookup"><span data-stu-id="f0115-111">**Error ID:** BC42017</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f0115-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f0115-112">To correct this error</span></span>  
  
-   <span data-ttu-id="f0115-113">Si possible, déclarez la variable comme étant d’un type spécifique.</span><span class="sxs-lookup"><span data-stu-id="f0115-113">If possible, declare the variable to be of a specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0115-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f0115-114">See Also</span></span>  
 <span data-ttu-id="f0115-115">[Liaison anticipée et liaison tardive](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span><span class="sxs-lookup"><span data-stu-id="f0115-115">[Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md) </span></span>  
<span data-ttu-id="f0115-116"> [Déclaration des variables objets](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)</span><span class="sxs-lookup"><span data-stu-id="f0115-116"> [Object Variable Declaration](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)</span></span>
