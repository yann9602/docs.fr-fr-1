---
title: /langversion (Visual Basic) | Documents Microsoft
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
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
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
ms.openlocfilehash: 56411df907bd5ff0416e6d0539cbe46df3b34947
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="langversion-visual-basic"></a><span data-ttu-id="65428-102">/langversion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="65428-102">/langversion (Visual Basic)</span></span>
<span data-ttu-id="65428-103">Entraîne le compilateur à accepter uniquement la syntaxe qui est incluse dans la version du langage Visual Basic spécifiée.</span><span class="sxs-lookup"><span data-stu-id="65428-103">Causes the compiler to accept only syntax that is included in the specified Visual Basic language version.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65428-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65428-104">Syntax</span></span>  
  
```  
/langversion:version  
```  
  
## <a name="arguments"></a><span data-ttu-id="65428-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="65428-105">Arguments</span></span>  
 `version`  
 <span data-ttu-id="65428-106">Obligatoire.</span><span class="sxs-lookup"><span data-stu-id="65428-106">Required.</span></span> <span data-ttu-id="65428-107">La langue à utiliser lors de la compilation.</span><span class="sxs-lookup"><span data-stu-id="65428-107">The language version to be used during the compilation.</span></span> <span data-ttu-id="65428-108">Valeurs acceptées sont `9`, `9.0`, `10`, et `10.0`.</span><span class="sxs-lookup"><span data-stu-id="65428-108">Accepted values are `9`, `9.0`, `10`, and `10.0`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65428-109">Notes</span><span class="sxs-lookup"><span data-stu-id="65428-109">Remarks</span></span>  
 <span data-ttu-id="65428-110">La `/langversion` option spécifie la syntaxe acceptée le compilateur.</span><span class="sxs-lookup"><span data-stu-id="65428-110">The `/langversion` option specifies what syntax the compiler accepts.</span></span> <span data-ttu-id="65428-111">Par exemple, si vous spécifiez que la version est 9.0, le compilateur génère des erreurs de syntaxe qui est valide uniquement dans la version 10.0 et versions ultérieures.</span><span class="sxs-lookup"><span data-stu-id="65428-111">For example, if you specify that the language version is 9.0, the compiler generates errors for syntax that is valid only in version 10.0 and later.</span></span>  
  
 <span data-ttu-id="65428-112">Vous pouvez utiliser cette option lorsque vous développez des applications qui ciblent des versions différentes du .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="65428-112">You can use this option when you develop applications that target different versions of the .NET Framework.</span></span> <span data-ttu-id="65428-113">Par exemple, si vous ciblez .NET Framework 3.5, vous pouvez utiliser cette option pour vous assurer que vous n’utilisez pas la syntaxe de la version de langage 10.0.</span><span class="sxs-lookup"><span data-stu-id="65428-113">For example, if you are targeting .NET Framework 3.5, you could use this option to ensure that you do not use syntax from language version 10.0.</span></span>  
  
 <span data-ttu-id="65428-114">Vous pouvez définir `/langversion` directement uniquement à l’aide de la ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="65428-114">You can set `/langversion` directly only by using the command line.</span></span> <span data-ttu-id="65428-115">Pour plus d’informations, consultez [Ciblage d’une version spécifique du .NET Framework](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span><span class="sxs-lookup"><span data-stu-id="65428-115">For more information, see [Targeting a Specific .NET Framework Version](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version).</span></span>  
  
## <a name="example"></a><span data-ttu-id="65428-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="65428-116">Example</span></span>  
 <span data-ttu-id="65428-117">Le code suivant compile `sample.vb` pour Visual Basic 9.0.</span><span class="sxs-lookup"><span data-stu-id="65428-117">The following code compiles `sample.vb` for Visual Basic 9.0.</span></span>  
  
```  
vbc /langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="65428-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65428-118">See Also</span></span>  
 <span data-ttu-id="65428-119">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="65428-119">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="65428-120"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="65428-120"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="65428-121"> [Ciblage d’une version spécifique du .NET Framework](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)</span><span class="sxs-lookup"><span data-stu-id="65428-121"> [Targeting a Specific .NET Framework Version](https://docs.microsoft.com/visualstudio/ide/targeting-a-specific-dotnet-framework-version)</span></span>
