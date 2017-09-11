---
title: "Type sous-jacent &lt;typename&gt; d’Enum n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
dev_langs:
- VB
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: 8
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
ms.openlocfilehash: 51628d2232b9e1c89e7fbf931ef0d6602f7cddc9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="98b93-102">Type sous-jacent &lt;typename&gt; d’Enum n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="98b93-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="98b93-103">Type de données spécifié pour cette énumération n’est pas inclus dans le [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span><span class="sxs-lookup"><span data-stu-id="98b93-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span> <span data-ttu-id="98b93-104">Ce n’est pas une erreur dans votre composant, parce que le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] et [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] prennent en charge ce type de données.</span><span class="sxs-lookup"><span data-stu-id="98b93-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] and [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] support this data type.</span></span> <span data-ttu-id="98b93-105">Toutefois, un autre composant écrit dans le code strictement conforme CLS ne prenne pas en charge ce type de données.</span><span class="sxs-lookup"><span data-stu-id="98b93-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="98b93-106">Ce composant n’est peut-être pas en mesure d’interagir correctement avec votre composant.</span><span class="sxs-lookup"><span data-stu-id="98b93-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="98b93-107">Les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :</span><span class="sxs-lookup"><span data-stu-id="98b93-107">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="98b93-108">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="98b93-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="98b93-109">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="98b93-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="98b93-110">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="98b93-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="98b93-111">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="98b93-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="98b93-112">Par défaut, ce message est un avertissement.</span><span class="sxs-lookup"><span data-stu-id="98b93-112">By default, this message is a warning.</span></span> <span data-ttu-id="98b93-113">Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="98b93-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="98b93-114">**ID d’erreur :** BC40032</span><span class="sxs-lookup"><span data-stu-id="98b93-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="98b93-115">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="98b93-115">To correct this error</span></span>  
  
-   <span data-ttu-id="98b93-116">Si votre composant sert d’interface uniquement avec d’autres [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] composants ou n’envoie pas d’interface avec d’autres composants, vous ne devez pas modifier quoi que ce soit.</span><span class="sxs-lookup"><span data-stu-id="98b93-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="98b93-117">Si vous utilisez un composant non écrit pour le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], vous pouvez déterminer, par réflexion ou à partir de la documentation, s’il prend en charge ce type de données.</span><span class="sxs-lookup"><span data-stu-id="98b93-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="98b93-118">Si c’est le cas, il est inutile de modifier quoi que ce soit.</span><span class="sxs-lookup"><span data-stu-id="98b93-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="98b93-119">Si vous utilisez un composant qui ne prend pas en charge ce type de données, vous devez le remplacer par le type conforme CLS le plus proche.</span><span class="sxs-lookup"><span data-stu-id="98b93-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="98b93-120">Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="98b93-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="98b93-121">Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.</span><span class="sxs-lookup"><span data-stu-id="98b93-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="98b93-122">Si vous interfacez avec des objets Automation ou COM, n’oubliez pas que certains types ont des largeurs de données différentes de celles du [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="98b93-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span> <span data-ttu-id="98b93-123">Par exemple, `uint` correspond souvent à 16 bits dans d’autres environnements.</span><span class="sxs-lookup"><span data-stu-id="98b93-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="98b93-124">Si vous passez un argument de 16 bits à un tel composant, déclarez-le en tant que `UShort` au lieu de `UInteger` dans votre [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span><span class="sxs-lookup"><span data-stu-id="98b93-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98b93-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="98b93-125">See Also</span></span>  
 <span data-ttu-id="98b93-126">[Réflexion](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26) </span><span class="sxs-lookup"><span data-stu-id="98b93-126">[Reflection](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26) </span></span>  
<span data-ttu-id="98b93-127"> [Réflexion](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775) </span><span class="sxs-lookup"><span data-stu-id="98b93-127"> [Reflection](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775) </span></span>  
<span data-ttu-id="98b93-128"> [\<PAVE sur > écrire du Code conforme CLS](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span><span class="sxs-lookup"><span data-stu-id="98b93-128"> [\<PAVE OVER> Writing CLS-Compliant Code](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)</span></span>
