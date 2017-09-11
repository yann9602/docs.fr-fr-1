---
title: "Non conforme CLS &lt;membername&gt; n’est pas autorisée dans une interface conforme CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40033
- vbc40033
dev_langs:
- VB
helpviewer_keywords:
- BC40033
ms.assetid: 060c4b08-798e-40f1-94cf-c05c524f1b8a
caps.latest.revision: 9
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
ms.openlocfilehash: 27e83344c68d73c992d2395ab5d1bfcdb67520b0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="non-cls-compliant-ltmembernamegt-is-not-allowed-in-a-cls-compliant-interface"></a><span data-ttu-id="5398f-102">Non conforme CLS &lt;membername&gt; n’est pas autorisée dans une interface conforme CLS</span><span class="sxs-lookup"><span data-stu-id="5398f-102">Non-CLS-compliant &lt;membername&gt; is not allowed in a CLS-compliant interface</span></span>
<span data-ttu-id="5398f-103">Une propriété, une procédure ou un événement dans une interface est marquée comme `<CLSCompliant(True)>` lorsque l’interface proprement dite est marquée comme `<CLSCompliant(False)>` ou n’est pas marquée.</span><span class="sxs-lookup"><span data-stu-id="5398f-103">A property, procedure, or event in an interface is marked as `<CLSCompliant(True)>` when the interface itself is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="5398f-104">Pour une interface conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), tous ses membres doivent être conformes.</span><span class="sxs-lookup"><span data-stu-id="5398f-104">For an interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), all its members must be compliant.</span></span>  
  
 <span data-ttu-id="5398f-105">Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="5398f-105">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="5398f-106">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="5398f-106">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="5398f-107">Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="5398f-107">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="5398f-108">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="5398f-108">By default, this message is a warning.</span></span> <span data-ttu-id="5398f-109">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5398f-109">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5398f-110">**ID d’erreur :** BC40033</span><span class="sxs-lookup"><span data-stu-id="5398f-110">**Error ID:** BC40033</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5398f-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5398f-111">To correct this error</span></span>  
  
-   <span data-ttu-id="5398f-112">Si vous la conformité CLS et contrôlez le code source de l’interface, marquez l’interface comme `<CLSCompliant(True)>` si tous ses membres sont conformes.</span><span class="sxs-lookup"><span data-stu-id="5398f-112">If you require CLS compliance and have control over the interface source code, mark the interface as `<CLSCompliant(True)>` if all its members are compliant.</span></span>  
  
-   <span data-ttu-id="5398f-113">Si la conformité CLS et vous n’avez aucun contrôle sur le code source de l’interface, ou si elle n’est pas considérée comme conforme, définissez ce membre dans une autre interface.</span><span class="sxs-lookup"><span data-stu-id="5398f-113">If you require CLS compliance and do not have control over the interface source code, or if it does not qualify to be compliant, define this member within a different interface.</span></span>  
  
-   <span data-ttu-id="5398f-114">Si vous avez besoin que ce membre doit rester dans son interface actuelle, supprimez le <xref:System.CLSCompliantAttribute>à partir de sa définition ou marquez-le comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="5398f-114">If you require that this member remain within its current interface, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5398f-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5398f-115">See Also</span></span>  
 <span data-ttu-id="5398f-116">[Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md) </span><span class="sxs-lookup"><span data-stu-id="5398f-116">[Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md) </span></span>  
<span data-ttu-id="5398f-117"> [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="5398f-117"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
