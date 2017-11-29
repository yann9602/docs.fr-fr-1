---
title: /sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 876922385124db3e8db12c93c75194da83d2526c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sdkpath"></a><span data-ttu-id="170c3-102">/sdkpath</span><span class="sxs-lookup"><span data-stu-id="170c3-102">/sdkpath</span></span>
<span data-ttu-id="170c3-103">Spécifie l'emplacement de Mscorlib.dll et de Microsoft.VisualBasic.dll.</span><span class="sxs-lookup"><span data-stu-id="170c3-103">Specifies the location of Mscorlib.dll and Microsoft.VisualBasic.dll.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="170c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="170c3-104">Syntax</span></span>  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a><span data-ttu-id="170c3-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="170c3-105">Arguments</span></span>  
 `path`  
 <span data-ttu-id="170c3-106">Le répertoire contenant les versions de Mscorlib.dll et de Microsoft.VisualBasic.dll à utiliser pour la compilation.</span><span class="sxs-lookup"><span data-stu-id="170c3-106">The directory containing the versions of Mscorlib.dll and Microsoft.VisualBasic.dll to use for compilation.</span></span> <span data-ttu-id="170c3-107">Ce chemin d’accès n’est pas vérifiée jusqu'à ce qu’il est chargé.</span><span class="sxs-lookup"><span data-stu-id="170c3-107">This path is not verified until it is loaded.</span></span> <span data-ttu-id="170c3-108">Placez le nom de répertoire entre guillemets ( » «) si elle contient un espace.</span><span class="sxs-lookup"><span data-stu-id="170c3-108">Enclose the directory name in quotation marks (" ") if it contains a space.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="170c3-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="170c3-109">Remarks</span></span>  
 <span data-ttu-id="170c3-110">Cette option indique à le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur de charger les fichiers Mscorlib.dll et de Microsoft.VisualBasic.dll à partir d’un emplacement non définis par défaut.</span><span class="sxs-lookup"><span data-stu-id="170c3-110">This option tells the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler to load the Mscorlib.dll and Microsoft.VisualBasic.dll files from a non-default location.</span></span> <span data-ttu-id="170c3-111">Le `/sdkpath` option a été conçue pour être utilisé avec [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span><span class="sxs-lookup"><span data-stu-id="170c3-111">The `/sdkpath` option was designed to be used with [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md).</span></span> <span data-ttu-id="170c3-112">Le [!INCLUDE[Compact](~/includes/compact-md.md)] utilise différentes versions de ces bibliothèques d’assistance pour éviter l’utilisation de types et de fonctionnalités de langage introuvables sur les appareils.</span><span class="sxs-lookup"><span data-stu-id="170c3-112">The [!INCLUDE[Compact](~/includes/compact-md.md)] uses different versions of these support libraries to avoid the use of types and language features not found on the devices.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="170c3-113">Le `/sdkpath` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="170c3-113">The `/sdkpath` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span> <span data-ttu-id="170c3-114">Le `/sdkpath` option est définie lorsque un [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projet smart device est chargé.</span><span class="sxs-lookup"><span data-stu-id="170c3-114">The `/sdkpath` option is set when a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] device project is loaded.</span></span>  
  
 <span data-ttu-id="170c3-115">Vous pouvez spécifier que le compilateur doit compiler sans référence à la bibliothèque Runtime Visual Basic à l’aide de la `/vbruntime` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="170c3-115">You can specify that the compiler should compile without a reference to the Visual Basic Runtime Library by using the `/vbruntime` compiler option.</span></span> <span data-ttu-id="170c3-116">Pour plus d’informations, consultez [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span><span class="sxs-lookup"><span data-stu-id="170c3-116">For more information, see [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="170c3-117">Exemple</span><span class="sxs-lookup"><span data-stu-id="170c3-117">Example</span></span>  
 <span data-ttu-id="170c3-118">Le code suivant compile `Myfile.vb` avec la [!INCLUDE[Compact](~/includes/compact-md.md)], l’utilisation des versions de Mscorlib.dll et de Microsoft.VisualBasic.dll trouvées dans le répertoire d’installation par défaut de la [!INCLUDE[Compact](~/includes/compact-md.md)] sur le lecteur C.</span><span class="sxs-lookup"><span data-stu-id="170c3-118">The following code compiles `Myfile.vb` with the [!INCLUDE[Compact](~/includes/compact-md.md)], using the versions of Mscorlib.dll and Microsoft.VisualBasic.dll found in the default installation directory of the [!INCLUDE[Compact](~/includes/compact-md.md)] on the C drive.</span></span> <span data-ttu-id="170c3-119">En règle générale, vous utiliseriez la version la plus récente de la [!INCLUDE[Compact](~/includes/compact-md.md)].</span><span class="sxs-lookup"><span data-stu-id="170c3-119">Typically, you would use the most recent version of the [!INCLUDE[Compact](~/includes/compact-md.md)].</span></span>  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="170c3-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="170c3-120">See Also</span></span>  
 [<span data-ttu-id="170c3-121">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="170c3-121">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="170c3-122">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="170c3-122">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="170c3-123">/netcf</span><span class="sxs-lookup"><span data-stu-id="170c3-123">/netcf</span></span>](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [<span data-ttu-id="170c3-124">/vbruntime</span><span class="sxs-lookup"><span data-stu-id="170c3-124">/vbruntime</span></span>](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
