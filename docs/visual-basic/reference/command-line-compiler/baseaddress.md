---
title: /baseaddress
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1ad39acdec92667fbb0848a1c64c567b504dcb67
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="baseaddress"></a><span data-ttu-id="cc577-102">/baseaddress</span><span class="sxs-lookup"><span data-stu-id="cc577-102">/baseaddress</span></span>
<span data-ttu-id="cc577-103">Spécifie une adresse de base par défaut lors de la création d’une DLL.</span><span class="sxs-lookup"><span data-stu-id="cc577-103">Specifies a default base address when creating a DLL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc577-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc577-104">Syntax</span></span>  
  
```  
/baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="cc577-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="cc577-105">Arguments</span></span>  
  
|<span data-ttu-id="cc577-106">Terme</span><span class="sxs-lookup"><span data-stu-id="cc577-106">Term</span></span>|<span data-ttu-id="cc577-107">Définition</span><span class="sxs-lookup"><span data-stu-id="cc577-107">Definition</span></span>|  
|---|---|  
|`address`|<span data-ttu-id="cc577-108">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="cc577-108">Required.</span></span> <span data-ttu-id="cc577-109">Adresse de base de la DLL.</span><span class="sxs-lookup"><span data-stu-id="cc577-109">The base address for the DLL.</span></span> <span data-ttu-id="cc577-110">Cette adresse doit être spécifiée comme un nombre hexadécimal.</span><span class="sxs-lookup"><span data-stu-id="cc577-110">This address must be specified as a hexadecimal number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc577-111">Notes</span><span class="sxs-lookup"><span data-stu-id="cc577-111">Remarks</span></span>  
 <span data-ttu-id="cc577-112">L’adresse de base par défaut pour une DLL est définie par le [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cc577-112">The default base address for a DLL is set by the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
 <span data-ttu-id="cc577-113">N’oubliez pas que le mot de poids faible de cette adresse est arrondi.</span><span class="sxs-lookup"><span data-stu-id="cc577-113">Be aware that the lower-order word in this address is rounded.</span></span> <span data-ttu-id="cc577-114">Par exemple, si vous spécifiez 0 x 11110001, il est arrondi à 0 x 11110000.</span><span class="sxs-lookup"><span data-stu-id="cc577-114">For example, if you specify 0x11110001, it is rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="cc577-115">Pour terminer le processus de signature d’une DLL, utilisez la `–R` option de l’outil Strong Name (Sn.exe).</span><span class="sxs-lookup"><span data-stu-id="cc577-115">To complete the signing process for a DLL, use the `–R` option of the Strong Naming tool (Sn.exe).</span></span>  
  
 <span data-ttu-id="cc577-116">Cette option est ignorée si la cible n’est pas une DLL.</span><span class="sxs-lookup"><span data-stu-id="cc577-116">This option is ignored if the target is not a DLL.</span></span>  
  
|<span data-ttu-id="cc577-117">Pour définir /baseaddress dans l’IDE de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="cc577-117">To set /baseaddress in the Visual Studio IDE</span></span>|  
|---|  
|<span data-ttu-id="cc577-118">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="cc577-118">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="cc577-119">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="cc577-119">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="cc577-120">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="cc577-120">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="cc577-121">3.  Cliquez sur **Avancé**.</span><span class="sxs-lookup"><span data-stu-id="cc577-121">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="cc577-122">4.  Modifiez la valeur dans la **adresse de base DLL :** boîte.</span><span class="sxs-lookup"><span data-stu-id="cc577-122">4.  Modify the value in the **DLL base address:** box.</span></span> <span data-ttu-id="cc577-123">**Remarque :** le **adresse de base DLL :** zone est en lecture seule, sauf si la cible est une DLL.</span><span class="sxs-lookup"><span data-stu-id="cc577-123">**Note:**      The **DLL base address:** box is read-only unless the target is a DLL.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc577-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cc577-124">See Also</span></span>  
 [<span data-ttu-id="cc577-125">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cc577-125">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="cc577-126">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc577-126">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)  
 [<span data-ttu-id="cc577-127">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="cc577-127">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 <span data-ttu-id="cc577-128">[Sn.exe (outil Strong Name)] [Sn.exe (outil Strong Name)](../../../framework/tools/sn-exe-strong-name-tool.md))</span><span class="sxs-lookup"><span data-stu-id="cc577-128">[Sn.exe (Strong Name Tool)][Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md))</span></span>
