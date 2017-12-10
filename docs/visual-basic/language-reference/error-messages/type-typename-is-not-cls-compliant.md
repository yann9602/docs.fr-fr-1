---
title: "Type &lt;typename&gt; n’est pas conforme CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
helpviewer_keywords: BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16c12ee6c4f6efa20b9bab5ccf10077496b931ac
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="6dfd4-102">Type &lt;typename&gt; n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="6dfd4-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="6dfd4-103">Une variable, une propriété ou un retour de fonction est déclaré avec un type de données qui n’est pas conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="6dfd4-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="6dfd4-104">Une application peut être conforme à la [indépendance du langage et composants indépendants du langage](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), elle doit utiliser uniquement des types conformes CLS.</span><span class="sxs-lookup"><span data-stu-id="6dfd4-104">For an application to be compliant with the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="6dfd4-105">Les types de données [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] suivants ne sont pas conformes CLS :</span><span class="sxs-lookup"><span data-stu-id="6dfd4-105">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="6dfd4-106">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="6dfd4-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="6dfd4-107">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="6dfd4-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="6dfd4-108">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="6dfd4-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="6dfd4-109">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="6dfd4-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="6dfd4-110">**ID d’erreur :** BC40041</span><span class="sxs-lookup"><span data-stu-id="6dfd4-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6dfd4-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6dfd4-111">To correct this error</span></span>  
  
-   <span data-ttu-id="6dfd4-112">Si votre application doit être conforme CLS, modifiez le type de données de cet élément pour le type conforme CLS le plus proche.</span><span class="sxs-lookup"><span data-stu-id="6dfd4-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="6dfd4-113">Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="6dfd4-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="6dfd4-114">Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.</span><span class="sxs-lookup"><span data-stu-id="6dfd4-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="6dfd4-115">Si votre application n’a pas besoin être conforme CLS, il est inutile d’apporter de modifications.</span><span class="sxs-lookup"><span data-stu-id="6dfd4-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="6dfd4-116">Soyez conscient de sa non-conformité, toutefois.</span><span class="sxs-lookup"><span data-stu-id="6dfd4-116">You should be aware of its noncompliance, however.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dfd4-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6dfd4-117">See Also</span></span>  
 [<span data-ttu-id="6dfd4-118">\<PAVE sur > écriture d’un Code conforme CLS</span><span class="sxs-lookup"><span data-stu-id="6dfd4-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
