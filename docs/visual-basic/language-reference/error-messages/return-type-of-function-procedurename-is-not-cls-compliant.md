---
title: "Type de retour de la fonction &quot;&lt;NomProcédure&gt;&quot; n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
dev_langs:
- VB
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
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
ms.openlocfilehash: 949104d77996cb7678bb9841cd1cd1e9b7f71b56
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="fdf69-102">Type de retour de la fonction '&lt;NomProcédure&gt;' n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="fdf69-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="fdf69-103">A `Function` procédure est marquée comme `<CLSCompliant(True)>` , mais retourne un type qui est marqué comme `<CLSCompliant(False)>`, n’est pas marqué ou non qualifié, car c’est un type non conforme.</span><span class="sxs-lookup"><span data-stu-id="fdf69-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="fdf69-104">Pour qu’une procédure soit conforme à CLS ([Indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3)), elle doit utiliser uniquement des types conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="fdf69-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="fdf69-105">Cette règle s’applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales.</span><span class="sxs-lookup"><span data-stu-id="fdf69-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="fdf69-106">Les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :</span><span class="sxs-lookup"><span data-stu-id="fdf69-106">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="fdf69-107">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="fdf69-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="fdf69-108">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="fdf69-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="fdf69-109">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="fdf69-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="fdf69-110">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="fdf69-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="fdf69-111">Lorsque vous appliquez le <xref:System.CLSCompliantAttribute>à un élément de programmation, vous définissez l’attribut `isCompliant` paramètre soit `True` ou `False` pour indiquer la conformité ou non-conformité.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="fdf69-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="fdf69-112">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="fdf69-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="fdf69-113">Si vous n’appliquez pas le <xref:System.CLSCompliantAttribute>à un élément, il est considéré comme non conforme.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="fdf69-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="fdf69-114">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="fdf69-114">By default, this message is a warning.</span></span> <span data-ttu-id="fdf69-115">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="fdf69-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="fdf69-116">**ID d’erreur :** BC40027</span><span class="sxs-lookup"><span data-stu-id="fdf69-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fdf69-117">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="fdf69-117">To correct this error</span></span>  
  
-   <span data-ttu-id="fdf69-118">Si le `Function` procédure doit retourner ce type particulier, supprimez le <xref:System.CLSCompliantAttribute>.</xref:System.CLSCompliantAttribute></span><span class="sxs-lookup"><span data-stu-id="fdf69-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="fdf69-119">La procédure ne peut pas être conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="fdf69-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="fdf69-120">Si le `Function` procédure doit être conforme CLS, modifiez le type de retour vers le type conforme CLS le plus proche.</span><span class="sxs-lookup"><span data-stu-id="fdf69-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="fdf69-121">Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="fdf69-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="fdf69-122">Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.</span><span class="sxs-lookup"><span data-stu-id="fdf69-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="fdf69-123">Si vous interfacez avec des objets Automation ou COM, n’oubliez pas que certains types ont des largeurs de données différentes de celles du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="fdf69-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="fdf69-124">Par exemple, `int` correspond souvent à 16 bits dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="fdf69-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="fdf69-125">Si vous retournez un entier 16 bits à un tel composant, déclarez-le en tant que `Short` au lieu de `Integer` dans votre [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span><span class="sxs-lookup"><span data-stu-id="fdf69-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdf69-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdf69-126">See Also</span></span>  
 [<span data-ttu-id="fdf69-127">\<PAVE sur > écrire du Code conforme CLS</span><span class="sxs-lookup"><span data-stu-id="fdf69-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
