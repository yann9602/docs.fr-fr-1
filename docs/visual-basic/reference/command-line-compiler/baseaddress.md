---
title: /BaseAddress | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
dev_langs:
- VB
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: 16
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
ms.openlocfilehash: 5687f119a57e0e54eca4df8f91fdf5e8b2775f82
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="baseaddress"></a><span data-ttu-id="63950-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="63950-102">/baseaddress</span></span>
<span data-ttu-id="63950-103">Spécifie une adresse de base par défaut lors de la création d’une DLL.</span><span class="sxs-lookup"><span data-stu-id="63950-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63950-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="63950-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="63950-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="63950-105">Arguments</span></span>  
  
|<span data-ttu-id="63950-106">Terme</span><span class="sxs-lookup"><span data-stu-id="63950-106">Term</span></span>|<span data-ttu-id="63950-107">Définition</span><span class="sxs-lookup"><span data-stu-id="63950-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="63950-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="63950-108">Required.</span></span> <span data-ttu-id="63950-109">L’adresse de base pour la DLL.</span><span class="sxs-lookup"><span data-stu-id="63950-109">The base address for the DLL.</span></span> <span data-ttu-id="63950-110">Cette adresse doit être spécifiée comme un nombre hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="63950-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63950-111">Remarques</span><span class="sxs-lookup"><span data-stu-id="63950-111">Remarks</span></span>  
 <span data-ttu-id="63950-112">L’adresse de base par défaut pour une DLL est définie par le [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span><span class="sxs-lookup"><span data-stu-id="63950-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)].</span></span>  
  
 <span data-ttu-id="63950-113">N’oubliez pas que le mot de poids faible de cette adresse est arrondi.</span><span class="sxs-lookup"><span data-stu-id="63950-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="63950-114">Par exemple, si vous spécifiez 0 x 11110001, il est arrondi à 0 x 11110000.</span><span class="sxs-lookup"><span data-stu-id="63950-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="63950-115">Pour terminer le processus de signature d’une DLL, utilisez la `–R` option de l’outil Strong Name (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="63950-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="63950-116">Cette option est ignorée si la cible n’est pas une DLL.</span><span class="sxs-lookup"><span data-stu-id="63950-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="63950-117">Pour définir /baseaddress dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="63950-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="63950-118">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="63950-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="63950-119">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="63950-119">On the **Project** menu, click **Properties**.</span></span> <span data-ttu-id="63950-120">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="63950-120">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="63950-121">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="63950-121">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="63950-122">3.  Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="63950-122">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="63950-123">4.  Modifiez la valeur dans la **adresse de base DLL :** boîte.</span><span class="sxs-lookup"><span data-stu-id="63950-123">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="63950-124">**Remarque :** le **adresse de base DLL :** zone est en lecture seule, sauf si la cible est une DLL.</span><span class="sxs-lookup"><span data-stu-id="63950-124">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="63950-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="63950-125">See Also</span></span>  
 <span data-ttu-id="63950-126">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="63950-126">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="63950-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="63950-127"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="63950-128"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="63950-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="63950-129"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23)</span><span class="sxs-lookup"><span data-stu-id="63950-129"> [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23)</span></span>
