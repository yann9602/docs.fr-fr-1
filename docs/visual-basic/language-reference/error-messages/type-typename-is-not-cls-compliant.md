---
title: "Type &lt;typename&gt; n’est pas conforme à CLS | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40041
- vbc40041
dev_langs:
- VB
helpviewer_keywords:
- BC40041
ms.assetid: 634132c2-5646-44aa-98c6-f773e2e63882
caps.latest.revision: 7
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
ms.openlocfilehash: a8d65568e862c941d5b927582833dff803219bf9
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="type-lttypenamegt-is-not-cls-compliant"></a><span data-ttu-id="2060f-102">Type &lt;typename&gt; n’est pas conforme CLS</span><span class="sxs-lookup"><span data-stu-id="2060f-102">Type &lt;typename&gt; is not CLS-compliant</span></span>
<span data-ttu-id="2060f-103">Une variable, une propriété ou un retour de fonction est déclaré avec un type de données qui n’est pas conforme CLS.</span><span class="sxs-lookup"><span data-stu-id="2060f-103">A variable, property, or function return is declared with a data type that is not CLS-compliant.</span></span>  
  
 <span data-ttu-id="2060f-104">Pour une application conforme à la [indépendance du langage et composants indépendants du langage](https://msdn.microsoft.com/library/12a7a7h3) (CLS), il doit utiliser uniquement des types conformes CLS.</span><span class="sxs-lookup"><span data-stu-id="2060f-104">For an application to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span>  
  
 <span data-ttu-id="2060f-105">Les types de données [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] suivants ne sont pas conformes CLS :</span><span class="sxs-lookup"><span data-stu-id="2060f-105">The following [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="2060f-106">SByte (type de données)</span><span class="sxs-lookup"><span data-stu-id="2060f-106">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="2060f-107">UInteger (type de données)</span><span class="sxs-lookup"><span data-stu-id="2060f-107">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="2060f-108">ULong (type de données)</span><span class="sxs-lookup"><span data-stu-id="2060f-108">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="2060f-109">UShort (type de données)</span><span class="sxs-lookup"><span data-stu-id="2060f-109">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="2060f-110">**ID d’erreur :** BC40041</span><span class="sxs-lookup"><span data-stu-id="2060f-110">**Error ID:** BC40041</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2060f-111">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="2060f-111">To correct this error</span></span>  
  
-   <span data-ttu-id="2060f-112">Si votre application doit être conforme CLS, modifiez le type de données de cet élément au type conforme CLS le plus proche.</span><span class="sxs-lookup"><span data-stu-id="2060f-112">If your application needs to be CLS-compliant, change the data type of this element to the closest CLS-compliant type.</span></span> <span data-ttu-id="2060f-113">Par exemple, vous pouvez utiliser `UInteger` au lieu de `Integer` si vous n’avez pas besoin de la plage de valeurs située au-dessus de 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="2060f-113">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="2060f-114">Si vous avez besoin de la plage étendue, vous pouvez remplacer `UInteger` par `Long`.</span><span class="sxs-lookup"><span data-stu-id="2060f-114">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="2060f-115">Si votre application n’a pas besoin être conforme CLS, il est inutile de modifier quoi que ce soit.</span><span class="sxs-lookup"><span data-stu-id="2060f-115">If your application does not need to be CLS-compliant, you do not need to change anything.</span></span> <span data-ttu-id="2060f-116">Vous devez être conscient de sa non-conformité, toutefois.</span><span class="sxs-lookup"><span data-stu-id="2060f-116">You should be aware of its noncompliance, however.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2060f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2060f-117">See Also</span></span>  
 [<span data-ttu-id="2060f-118">\<PAVE sur > écrire du Code conforme CLS</span><span class="sxs-lookup"><span data-stu-id="2060f-118">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
