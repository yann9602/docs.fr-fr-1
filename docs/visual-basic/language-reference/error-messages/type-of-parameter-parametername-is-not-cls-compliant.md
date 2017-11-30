---
title: "Type de paramètre &#39; &lt;nom_paramètre&gt;&#39; n’est pas conforme CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords: BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c495a21603f1977bd0f0630104f75ab02728928
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a><span data-ttu-id="5111d-102">Type de paramètre &#39; &lt;nom_paramètre&gt;&#39; n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="5111d-102">Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="5111d-103">Une procédure est marquée comme `<CLSCompliant(True)>` mais déclare un paramètre avec un type qui est marqué comme `<CLSCompliant(False)>`, n’est pas marqué ou ne répond pas, car il s’agit d’un type non conforme.</span><span class="sxs-lookup"><span data-stu-id="5111d-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="5111d-104">Pour qu’une procédure soit conforme à CLS ([Indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3)), elle doit utiliser uniquement des types conformes à CLS.</span><span class="sxs-lookup"><span data-stu-id="5111d-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="5111d-105">Cette règle s’applique aux types des paramètres, au type de retour et aux types de toutes ses variables locales.</span><span class="sxs-lookup"><span data-stu-id="5111d-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="5111d-106">Les types de données [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] suivants ne sont pas conformes CLS :</span><span class="sxs-lookup"><span data-stu-id="5111d-106">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="5111d-107">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="5111d-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="5111d-108">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="5111d-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="5111d-109">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="5111d-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="5111d-110">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="5111d-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="5111d-111">Quand vous appliquez l’attribut <xref:System.CLSCompliantAttribute> à un élément de programmation, vous affectez au paramètre `isCompliant` de l’attribut la valeur `True` ou `False` pour indiquer la conformité ou la non-conformité.</span><span class="sxs-lookup"><span data-stu-id="5111d-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="5111d-112">Il n’existe pas de valeur par défaut pour ce paramètre et vous devez fournir une valeur.</span><span class="sxs-lookup"><span data-stu-id="5111d-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="5111d-113">Si vous n’appliquez pas <xref:System.CLSCompliantAttribute> à un élément, il est considéré comme étant non conforme.</span><span class="sxs-lookup"><span data-stu-id="5111d-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="5111d-114">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="5111d-114">By default, this message is a warning.</span></span> <span data-ttu-id="5111d-115">Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5111d-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5111d-116">**ID d’erreur :** BC40028</span><span class="sxs-lookup"><span data-stu-id="5111d-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5111d-117">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="5111d-117">To correct this error</span></span>  
  
-   <span data-ttu-id="5111d-118">Si la procédure doit prendre un paramètre de ce type particulier, supprimez le <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="5111d-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="5111d-119">La procédure ne peut pas être conforme à CLS.</span><span class="sxs-lookup"><span data-stu-id="5111d-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="5111d-120">Si la procédure doit être conforme CLS, modifier le type de ce paramètre pour le type conforme CLS le plus proche.</span><span class="sxs-lookup"><span data-stu-id="5111d-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="5111d-121">Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="5111d-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="5111d-122">Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.</span><span class="sxs-lookup"><span data-stu-id="5111d-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="5111d-123">Si vous interfacez avec des objets Automation ou COM, n’oubliez pas que certains types ont des largeurs de données différentes de celles du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5111d-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="5111d-124">Par exemple, `int` correspond souvent à 16 bits dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="5111d-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="5111d-125">Si vous passez un entier sur 16 bits à un tel composant, déclarez-le comme `Short` au lieu de `Integer` dans votre code [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] managé.</span><span class="sxs-lookup"><span data-stu-id="5111d-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5111d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5111d-126">See Also</span></span>  
 [<span data-ttu-id="5111d-127">\<PAVE sur > écriture d’un Code conforme CLS</span><span class="sxs-lookup"><span data-stu-id="5111d-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
