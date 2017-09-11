---
title: "Nom de &lt;namespacename&gt; dans l’espace de noms racine &lt;fullnamespacename&gt; n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40039
- bc40039
dev_langs:
- VB
helpviewer_keywords:
- BC40039
ms.assetid: c5bd5914-ae71-416a-8bed-f76f644f78be
caps.latest.revision: 10
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
ms.openlocfilehash: 0d31657a958581b91cb448b78b8f55f8aadfe7c9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="name-ltnamespacenamegt-in-the-root-namespace-ltfullnamespacenamegt-is-not-cls-compliant"></a><span data-ttu-id="8feb1-102">Nom de &lt;namespacename&gt; dans l’espace de noms racine &lt;fullnamespacename&gt; n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="8feb1-102">Name &lt;namespacename&gt; in the root namespace &lt;fullnamespacename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="8feb1-103">Un assembly est marqué comme `<CLSCompliant(True)>`, mais un élément de l’espace de noms racine commence par un trait de soulignement (`_`).</span><span class="sxs-lookup"><span data-stu-id="8feb1-103">An assembly is marked as `<CLSCompliant(True)>`, but an element of the root namespace name begins with an underscore (`_`).</span></span>  
  
 <span data-ttu-id="8feb1-104">Un élément de programmation peut contenir un ou plusieurs traits de soulignement, mais afin être conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), il ne doit pas commencer par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="8feb1-104">A programming element can contain one or more underscores, but to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must not begin with an underscore.</span></span> <span data-ttu-id="8feb1-105">Consultez la page [noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="8feb1-105">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
 <span data-ttu-id="8feb1-106">Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="8feb1-106">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="8feb1-107">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="8feb1-107">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="8feb1-108">Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="8feb1-108">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="8feb1-109">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="8feb1-109">By default, this message is a warning.</span></span> <span data-ttu-id="8feb1-110">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8feb1-110">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8feb1-111">**ID d’erreur :** BC40039</span><span class="sxs-lookup"><span data-stu-id="8feb1-111">**Error ID:** BC40039</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8feb1-112">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="8feb1-112">To correct this error</span></span>  
  
-   <span data-ttu-id="8feb1-113">Si vous avez besoin de la conformité CLS, modifiez le nom d’espace de noms racine afin qu’aucun de ses éléments ne commence par un trait de soulignement.</span><span class="sxs-lookup"><span data-stu-id="8feb1-113">If you require CLS compliance, change the root namespace name so that none of its elements begins with an underscore.</span></span>  
  
-   <span data-ttu-id="8feb1-114">Si vous avez besoin que l’espace de noms reste inchangé, supprimez le <xref:System.CLSCompliantAttribute>à partir de l’assembly ou marquez-le comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="8feb1-114">If you require that the namespace name remain unchanged, then remove the <xref:System.CLSCompliantAttribute> from the assembly or mark it as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8feb1-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="8feb1-115">See Also</span></span>  
 <span data-ttu-id="8feb1-116">[Déclaration de Namespace](../../../visual-basic/language-reference/statements/namespace-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8feb1-116">[Namespace Statement](../../../visual-basic/language-reference/statements/namespace-statement.md) </span></span>  
<span data-ttu-id="8feb1-117"> [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span><span class="sxs-lookup"><span data-stu-id="8feb1-117"> [Namespaces in Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md) </span></span>  
<span data-ttu-id="8feb1-118"> [/RootNamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md) </span><span class="sxs-lookup"><span data-stu-id="8feb1-118"> [/rootnamespace](../../../visual-basic/reference/command-line-compiler/rootnamespace.md) </span></span>  
<span data-ttu-id="8feb1-119"> [Page Application, Concepteur de projets (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span><span class="sxs-lookup"><span data-stu-id="8feb1-119"> [Application Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/application-page-project-designer-visual-basic) </span></span>  
<span data-ttu-id="8feb1-120"> [Noms d’éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span><span class="sxs-lookup"><span data-stu-id="8feb1-120"> [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md) </span></span>  
<span data-ttu-id="8feb1-121"> [Conventions d’affectation de noms de Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span><span class="sxs-lookup"><span data-stu-id="8feb1-121"> [Visual Basic Naming Conventions](../../../visual-basic/programming-guide/program-structure/naming-conventions.md) </span></span>  
<span data-ttu-id="8feb1-122"> [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="8feb1-122"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
