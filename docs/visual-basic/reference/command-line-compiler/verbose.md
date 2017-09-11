---
title: /verbose | Documents Microsoft
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
- verbose compiler option [Visual Basic]
- -verbose compiler option [Visual Basic]
- /verbose compiler option [Visual Basic]
ms.assetid: d1aec0c1-0261-421d-9adc-5b13756100be
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
ms.openlocfilehash: 62285a727217aa897a83a9e746588c80a2c519c0
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="verbose"></a><span data-ttu-id="2dc33-102">/verbose</span><span class="sxs-lookup"><span data-stu-id="2dc33-102">/verbose</span></span>
<span data-ttu-id="2dc33-103">Indique au compilateur de générer des messages d’état et d’erreur détaillés.</span><span class="sxs-lookup"><span data-stu-id="2dc33-103">Causes the compiler to produce verbose status and error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2dc33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2dc33-104">Syntax</span></span>  
  
```  
/verbose[+ | -]  
```  
  
## <a name="arguments"></a><span data-ttu-id="2dc33-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="2dc33-105">Arguments</span></span>  
 <span data-ttu-id="2dc33-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="2dc33-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="2dc33-107">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="2dc33-107">Optional.</span></span> <span data-ttu-id="2dc33-108">Spécification de `/verbose` est identique à `/verbose+`, ce qui entraîne le compilateur à émettre des messages documentés.</span><span class="sxs-lookup"><span data-stu-id="2dc33-108">Specifying `/verbose` is the same as specifying `/verbose+`, which causes the compiler to emit verbose messages.</span></span> <span data-ttu-id="2dc33-109">La valeur par défaut pour cette option est `/verbose-`.</span><span class="sxs-lookup"><span data-stu-id="2dc33-109">The default for this option is `/verbose-`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2dc33-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="2dc33-110">Remarks</span></span>  
 <span data-ttu-id="2dc33-111">La `/verbose` option affiche des informations sur le nombre total d’erreurs émises par le compilateur, signale les assemblys chargés par un module et affiche les fichiers qui sont en cours de compilation.</span><span class="sxs-lookup"><span data-stu-id="2dc33-111">The `/verbose` option displays information about the total number of errors issued by the compiler, reports which assemblies are being loaded by a module, and displays which files are currently being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2dc33-112">La `/verbose` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lors de la compilation à partir de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="2dc33-112">The `/verbose` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dc33-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="2dc33-113">Example</span></span>  
 <span data-ttu-id="2dc33-114">Le code suivant compile `In.vb` et demande au compilateur d’afficher des informations d’état détaillées.</span><span class="sxs-lookup"><span data-stu-id="2dc33-114">The following code compiles `In.vb` and directs the compiler to display verbose status information.</span></span>  
  
```  
vbc /verbose in.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="2dc33-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2dc33-115">See Also</span></span>  
 <span data-ttu-id="2dc33-116">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="2dc33-116">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="2dc33-117"> [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span><span class="sxs-lookup"><span data-stu-id="2dc33-117"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)</span></span>
