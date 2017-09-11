---
title: "Nom de &lt;membername&gt; n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40031
- vbc40031
dev_langs:
- VB
helpviewer_keywords:
- BC40031
ms.assetid: e2b885dc-cbf9-49ff-bbbe-531657ea99f7
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
ms.openlocfilehash: cbe0a8db6d801a0d083a6828af75342f15f0178d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="name-ltmembernamegt-is-not-cls-compliant"></a><span data-ttu-id="9af52-102">Nom de &lt;membername&gt; n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="9af52-102">Name &lt;membername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="9af52-103">Un assembly est marqué comme `<CLSCompliant(True)>` , mais il expose un membre portant un nom qui commence par un trait de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="9af52-103">An assembly is marked as `<CLSCompliant(True)>` but exposes a member with a name that begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="9af52-104">Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais afin être conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), il ne doit pas commencer par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="9af52-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="9af52-105">Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="9af52-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="9af52-106">Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="9af52-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="9af52-107">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="9af52-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="9af52-108">Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="9af52-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="9af52-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="9af52-109">By default, this message is a warning.</span></span> <span data-ttu-id="9af52-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="9af52-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="9af52-111">**ID d’erreur :** BC40031</span><span class="sxs-lookup"><span data-stu-id="9af52-111">**Error ID:** BC40031</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9af52-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="9af52-112">To correct this error</span></span>  
  
-   <span data-ttu-id="9af52-113">Si vous avez un contrôle sur le code source, modifiez le nom du membre afin qu’il ne commence pas par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="9af52-113">If you have control over the source code, change the member name so that it does not begin with an underscore.</span></span>  
  
-   <span data-ttu-id="9af52-114">Si vous avez besoin que le nom de membre reste inchangé, supprimez le <xref:System.CLSCompliantAttribute>à partir de sa définition ou marquez-le comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="9af52-114">If you require that the member name remain unchanged, remove the <xref:System.CLSCompliantAttribute> from its definition or mark it as `<CLSCompliant(False)>`.</span></span> <span data-ttu-id="9af52-115">Vous pouvez toujours marquer l’assembly comme `<CLSCompliant(True)>`.</span><span class="sxs-lookup"><span data-stu-id="9af52-115">You can still mark the assembly as `<CLSCompliant(True)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9af52-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9af52-116">See Also</span></span>  
 <span data-ttu-id="9af52-117">[Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="9af52-117">[Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="9af52-118"> [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="9af52-118"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="9af52-119"> [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="9af52-119"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
