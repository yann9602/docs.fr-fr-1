---
title: "«&lt;classname&gt;&quot; n’est pas conforme CLS, car l’interface &quot;&lt;interfacename&gt;&quot; il implémente n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40029
- vbc40029
dev_langs:
- VB
helpviewer_keywords:
- BC40029
ms.assetid: 178452f3-5575-4da0-9d6c-53bcddb6a338
caps.latest.revision: 13
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
ms.openlocfilehash: d2819bf2dc76291cbaf7ca9215608a11b1a98b3a
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="39ltclassnamegt39-is-not-cls-compliant-because-the-interface-39ltinterfacenamegt39-it-implements-is-not-cls-compliant"></a><span data-ttu-id="f7450-102">«&lt;classname&gt;' n’est pas conforme CLS, car l’interface '&lt;interfacename&gt;' il implémente n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="f7450-102">&#39;&lt;classname&gt;&#39; is not CLS-compliant because the interface &#39;&lt;interfacename&gt;&#39; it implements is not CLS-compliant</span></span>
<span data-ttu-id="f7450-103">Une classe ou une interface est marquée comme `<CLSCompliant(True)>` quand elle est dérivée d’un type ou implémente un type qui est marqué comme `<CLSCompliant(False)>` ou qui n’est pas marqué.</span><span class="sxs-lookup"><span data-stu-id="f7450-103">A class or interface is marked as `<CLSCompliant(True)>` when it derives from or implements a type that is marked as `<CLSCompliant(False)>` or is not marked.</span></span>  
  
 <span data-ttu-id="f7450-104">Pour une classe ou une interface conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), sa hiérarchie d’héritage entière doit être conforme.</span><span class="sxs-lookup"><span data-stu-id="f7450-104">For a class or interface to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), its entire inheritance hierarchy must be compliant.</span></span> <span data-ttu-id="f7450-105">Cela signifie que chaque type dont elle hérite, directement ou indirectement, doit être conforme.</span><span class="sxs-lookup"><span data-stu-id="f7450-105">That means every type from which it inherits, directly or indirectly, must be compliant.</span></span> <span data-ttu-id="f7450-106">De même, si une classe implémente une ou plusieurs interfaces, celles-ci doivent toutes être conformes au sein de leurs hiérarchies d’héritage.</span><span class="sxs-lookup"><span data-stu-id="f7450-106">Similarly, if a class implements one or more interfaces, they must all be compliant throughout their inheritance hierarchies.</span></span>  
  
 <span data-ttu-id="f7450-107">Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="f7450-107">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="f7450-108">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="f7450-108">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="f7450-109">Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="f7450-109">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="f7450-110">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="f7450-110">By default, this message is a warning.</span></span> <span data-ttu-id="f7450-111">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="f7450-111">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="f7450-112">**ID d’erreur :** BC40029</span><span class="sxs-lookup"><span data-stu-id="f7450-112">**Error ID:** BC40029</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f7450-113">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="f7450-113">To correct this error</span></span>  
  
-   <span data-ttu-id="f7450-114">Si la conformité CLS est obligatoire, définissez ce type dans une autre hiérarchie d’héritage ou dans un autre schéma d’implémentation.</span><span class="sxs-lookup"><span data-stu-id="f7450-114">If you require CLS compliance, define this type within a different inheritance hierarchy or implementation scheme.</span></span>  
  
-   <span data-ttu-id="f7450-115">Si vous avez besoin de rester au sein de son schéma d’implémentation ou la hiérarchie d’héritage actuelle, supprimez le <xref:System.CLSCompliantAttribute>à partir de sa définition ou marquez-le comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="f7450-115">If you require that this type remain within its current inheritance hierarchy or implementation scheme, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7450-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f7450-116">See Also</span></span>  
 [<span data-ttu-id="f7450-117">\<PAVE sur > écrire du Code conforme CLS</span><span class="sxs-lookup"><span data-stu-id="f7450-117">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
