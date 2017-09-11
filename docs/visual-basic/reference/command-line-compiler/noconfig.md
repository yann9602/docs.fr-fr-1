---
title: /noconfig | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
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
ms.openlocfilehash: fe3271e4a119e0c40370a7351bb39188f4d1c8ef
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="noconfig"></a><span data-ttu-id="a6f87-102">/noconfig</span><span class="sxs-lookup"><span data-stu-id="a6f87-102">/noconfig</span></span>
<span data-ttu-id="a6f87-103">Spécifie que le compilateur ne doit pas référencer automatiquement les communément utilisées [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblys ou importer les `System` et `Microsoft.VisualBasic` espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="a6f87-103">Specifies that the compiler should not automatically reference the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies or import the `System` and `Microsoft.VisualBasic` namespaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6f87-104">Syntax</span></span>  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a><span data-ttu-id="a6f87-105">Remarques</span><span class="sxs-lookup"><span data-stu-id="a6f87-105">Remarks</span></span>  
 <span data-ttu-id="a6f87-106">La `/noconfig` option indique au compilateur ne pas de compiler avec le fichier Vbc.rsp, qui se trouve dans le même répertoire que le fichier Vbc.exe.</span><span class="sxs-lookup"><span data-stu-id="a6f87-106">The `/noconfig` option tells the compiler not to compile with the Vbc.rsp file, which is located in the same directory as the Vbc.exe file.</span></span> <span data-ttu-id="a6f87-107">Le fichier Vbc.rsp référence couramment utilisées [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] les assemblys et les importations de la `System` et `Microsoft.VisualBasic` espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="a6f87-107">The Vbc.rsp file references the commonly used [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies and imports the `System` and `Microsoft.VisualBasic` namespaces.</span></span> <span data-ttu-id="a6f87-108">Le compilateur référence implicitement l’assembly System.dll à moins que le `/nostdlib` option est spécifiée.</span><span class="sxs-lookup"><span data-stu-id="a6f87-108">The compiler implicitly references the System.dll assembly unless the `/nostdlib` option is specified.</span></span> <span data-ttu-id="a6f87-109">La `/nostdlib` option indique au compilateur pas compiler avec Vbc.rsp ou de référencer automatiquement l’assembly System.dll.</span><span class="sxs-lookup"><span data-stu-id="a6f87-109">The `/nostdlib` option tells the compiler not to compile with Vbc.rsp or automatically reference the System.dll assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6f87-110">Les assemblys Mscorlib.dll et de Microsoft.VisualBasic.dll sont toujours référencés.</span><span class="sxs-lookup"><span data-stu-id="a6f87-110">The Mscorlib.dll and Microsoft.VisualBasic.dll assemblies are always referenced.</span></span>  
  
 <span data-ttu-id="a6f87-111">Vous pouvez modifier le fichier Vbc.rsp pour spécifier des options de compilateur supplémentaires qui doivent être incluses dans chaque compilation Vbc.exe (sauf si vous spécifiez la `/noconfig` option).</span><span class="sxs-lookup"><span data-stu-id="a6f87-111">You can modify the Vbc.rsp file to specify additional compiler options that should be included in every Vbc.exe compilation (except when specifying the `/noconfig` option).</span></span> <span data-ttu-id="a6f87-112">Pour plus d’informations, consultez [@ (Spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span><span class="sxs-lookup"><span data-stu-id="a6f87-112">For more information, see [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).</span></span>  
  
 <span data-ttu-id="a6f87-113">Le compilateur traite les options passées à la `vbc` commande dernier.</span><span class="sxs-lookup"><span data-stu-id="a6f87-113">The compiler processes the options passed to the `vbc` command last.</span></span> <span data-ttu-id="a6f87-114">Par conséquent, toute option de ligne de commande remplace le paramètre de la même option dans le fichier Vbc.rsp.</span><span class="sxs-lookup"><span data-stu-id="a6f87-114">Therefore, any option on the command line overrides the setting of the same option in the Vbc.rsp file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6f87-115">La `/noconfig` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="a6f87-115">The `/noconfig` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f87-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a6f87-116">See Also</span></span>  
 <span data-ttu-id="a6f87-117">[/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md) </span><span class="sxs-lookup"><span data-stu-id="a6f87-117">[/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md) </span></span>  
<span data-ttu-id="a6f87-118"> [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="a6f87-118"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="a6f87-119"> [@ (Spécifier un fichier réponse)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md) </span><span class="sxs-lookup"><span data-stu-id="a6f87-119"> [@ (Specify Response File)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md) </span></span>  
<span data-ttu-id="a6f87-120"> [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)</span><span class="sxs-lookup"><span data-stu-id="a6f87-120"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)</span></span>
