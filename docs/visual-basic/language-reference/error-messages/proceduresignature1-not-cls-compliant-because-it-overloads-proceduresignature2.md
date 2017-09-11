---
title: "&lt;proceduresignature1&gt; n’est pas conforme CLS, car il surcharge &lt;proceduresignature2&gt; dont il diffère uniquement par un tableau de types de paramètres tableau ou par la dimension des types de paramètres tableau | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40035
- bc40035
dev_langs:
- VB
helpviewer_keywords:
- BC40035
ms.assetid: 50a66dbe-2c1e-41bf-96bc-369301c891ac
caps.latest.revision: 11
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
ms.openlocfilehash: d106f59e3faa317f67ee92ddcec8416eeff745d4
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="ltproceduresignature1gt-is-not-cls-compliant-because-it-overloads-ltproceduresignature2gt-which-differs-from-it-only-by-array-of-array-parameter-types-or-by-the-rank-of-the-array-parameter-types"></a><span data-ttu-id="1c033-102">&lt;proceduresignature1&gt; n’est pas conforme CLS, car il surcharge &lt;proceduresignature2&gt; dont il diffère uniquement par un tableau de types de paramètres tableau ou par la dimension des types de paramètres tableau</span><span class="sxs-lookup"><span data-stu-id="1c033-102">&lt;proceduresignature1&gt; is not CLS-compliant because it overloads &lt;proceduresignature2&gt; which differs from it only by array of array parameter types or by the rank of the array parameter types</span></span>
<span data-ttu-id="1c033-103">Une procédure ou une propriété est marquée en tant que `<CLSCompliant(True)>` lorsqu’elle substitue une autre procédure ou propriété et la seule différence entre leurs listes de paramètres est le niveau d’imbrication d’un tableau en escalier ou le rang d’un tableau.</span><span class="sxs-lookup"><span data-stu-id="1c033-103">A procedure or property is marked as `<CLSCompliant(True)>` when it overrides another procedure or property and the only difference between their parameter lists is the nesting level of a jagged array or the rank of an array.</span></span>  
  
 <span data-ttu-id="1c033-104">Dans les déclarations suivantes, les deuxième et troisième déclarations génèrent cette erreur.</span><span class="sxs-lookup"><span data-stu-id="1c033-104">In the following declarations, the second and third declarations generate this error.</span></span>  
  
 `Overloads Sub processArray(ByVal arrayParam() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam()() As Integer)`  
  
 `Overloads Sub processArray(ByVal arrayParam(,) As Integer)`  
  
 <span data-ttu-id="1c033-105">La deuxième déclaration remplace le paramètre unidimensionnel d’origine `arrayParam` à un tableau de tableaux.</span><span class="sxs-lookup"><span data-stu-id="1c033-105">The second declaration changes the original one-dimensional parameter `arrayParam` to an array of arrays.</span></span> <span data-ttu-id="1c033-106">La troisième déclaration remplace `arrayParam` un tableau à deux dimensions (rang 2).</span><span class="sxs-lookup"><span data-stu-id="1c033-106">The third declaration changes `arrayParam` to a two-dimensional array (rank 2).</span></span> <span data-ttu-id="1c033-107">Bien que Visual Basic autorise les surcharges à différer uniquement par une de ces modifications, une telle surcharge n’est pas conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span><span class="sxs-lookup"><span data-stu-id="1c033-107">While Visual Basic allows overloads to differ only by one of these changes, such overloading is not compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span>  
  
 <span data-ttu-id="1c033-108">Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="1c033-108">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="1c033-109">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="1c033-109">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="1c033-110">Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="1c033-110">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="1c033-111">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="1c033-111">By default, this message is a warning.</span></span> <span data-ttu-id="1c033-112">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1c033-112">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1c033-113">**ID d’erreur :** BC40035</span><span class="sxs-lookup"><span data-stu-id="1c033-113">**Error ID:** BC40035</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c033-114">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="1c033-114">To correct this error</span></span>  
  
-   <span data-ttu-id="1c033-115">Si vous avez besoin de la conformité CLS, définissez vos surcharges pour diffèrent autrement que seules les modifications mentionnées dans cette page d’aide.</span><span class="sxs-lookup"><span data-stu-id="1c033-115">If you require CLS compliance, define your overloads to differ from each other in more ways than only the changes cited on this Help page.</span></span>  
  
-   <span data-ttu-id="1c033-116">Si vous avez besoin que les surcharges diffèrent uniquement par les modifications mentionnées dans l’aide de cette page, supprimez le <xref:System.CLSCompliantAttribute>à partir de leurs définitions ou marquez-les comme `<CLSCompliant(False)>`.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="1c033-116">If you require that the overloads differ only by the changes cited on this Help page, remove the <xref:System.CLSCompliantAttribute> from their definitions or mark them as `<CLSCompliant(False)>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c033-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1c033-117">See Also</span></span>  
 <span data-ttu-id="1c033-118">[\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3) </span><span class="sxs-lookup"><span data-stu-id="1c033-118">[\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3) </span></span>  
<span data-ttu-id="1c033-119"> [Surcharge de procédure](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md) </span><span class="sxs-lookup"><span data-stu-id="1c033-119"> [Procedure Overloading](../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md) </span></span>  
<span data-ttu-id="1c033-120"> [Surcharges](../../../visual-basic/language-reference/modifiers/overloads.md)</span><span class="sxs-lookup"><span data-stu-id="1c033-120"> [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)</span></span>
