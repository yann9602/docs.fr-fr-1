---
title: /moduleassemblyname | Documents Microsoft
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
- moduleassemblyname compiler option [Visual Basic]
- /moduleassemblyname compiler option [Visual Basic]
- -moduleassemblyname compiler option [Visual Basic]
ms.assetid: 013a57b6-f425-4dd3-b333-512d72c42f55
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
ms.openlocfilehash: 6852b8a0d9874fd65e93cdd9507fe9b7119ce5b3
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="moduleassemblyname"></a><span data-ttu-id="593c6-102">/moduleassemblyname</span><span class="sxs-lookup"><span data-stu-id="593c6-102">/moduleassemblyname</span></span>
<span data-ttu-id="593c6-103">Spécifie le nom de l’assembly dont ce module doit faire partie.</span><span class="sxs-lookup"><span data-stu-id="593c6-103">Specifies the name of the assembly that this module will be a part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="593c6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="593c6-104">Syntax</span></span>  
  
```  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a><span data-ttu-id="593c6-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="593c6-105">Arguments</span></span>  
  
|<span data-ttu-id="593c6-106">Terme</span><span class="sxs-lookup"><span data-stu-id="593c6-106">Term</span></span>|<span data-ttu-id="593c6-107">Définition</span><span class="sxs-lookup"><span data-stu-id="593c6-107">Definition</span></span>|  
|---|---|  
|`assembly_name`|<span data-ttu-id="593c6-108">Le nom de ce module fera partie de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="593c6-108">The name of the assembly that this module will be a part of.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="593c6-109">Remarques</span><span class="sxs-lookup"><span data-stu-id="593c6-109">Remarks</span></span>  
 <span data-ttu-id="593c6-110">Le compilateur traite les `/moduleassemblyname` option uniquement si la `/target:module` option a été spécifiée.</span><span class="sxs-lookup"><span data-stu-id="593c6-110">The compiler processes the `/moduleassemblyname` option only if the `/target:module` option has been specified.</span></span> <span data-ttu-id="593c6-111">Cela entraîne le compilateur à créer un module.</span><span class="sxs-lookup"><span data-stu-id="593c6-111">This causes the compiler to create a module.</span></span> <span data-ttu-id="593c6-112">Le module créé par le compilateur est valide uniquement pour l’assembly spécifié avec la `/moduleassemblyname` option.</span><span class="sxs-lookup"><span data-stu-id="593c6-112">The module created by the compiler is valid only for the assembly specified with the `/moduleassemblyname` option.</span></span> <span data-ttu-id="593c6-113">Si vous placez le module dans un assembly différent, les erreurs d’exécution seront produit.</span><span class="sxs-lookup"><span data-stu-id="593c6-113">If you place the module in a different assembly, run-time errors will occur.</span></span>  
  
 <span data-ttu-id="593c6-114">La `/moduleassemblyname` option est uniquement requise lorsque les conditions suivantes sont remplies :</span><span class="sxs-lookup"><span data-stu-id="593c6-114">The `/moduleassemblyname` option is needed only when the following are true:</span></span>  
  
-   <span data-ttu-id="593c6-115">Un type de données dans le module a besoin d’accéder à un `Friend` type dans un assembly référencé.</span><span class="sxs-lookup"><span data-stu-id="593c6-115">A data type in the module needs access to a `Friend` type in a referenced assembly.</span></span>  
  
-   <span data-ttu-id="593c6-116">L’assembly référencé a accordé l’accès d’assembly friend à l’assembly dans lequel le module sera généré.</span><span class="sxs-lookup"><span data-stu-id="593c6-116">The referenced assembly has granted friend assembly access to the assembly into which the module will be built.</span></span>  
  
 <span data-ttu-id="593c6-117">Pour plus d’informations sur la création d’un module, consultez [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="593c6-117">For more information about creating a module, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span> <span data-ttu-id="593c6-118">Pour plus d’informations sur les assemblys friend, consultez [assemblys Friend](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span><span class="sxs-lookup"><span data-stu-id="593c6-118">For more information about friend assemblies, see [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="593c6-119">La `/moduleassemblyname` option n’est pas disponible dans l’environnement de développement Visual Studio ; il est disponible uniquement lorsque vous compilez à partir d’une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="593c6-119">The `/moduleassemblyname` option is not available from within the Visual Studio development environment; it is available only when you compile from a command prompt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="593c6-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="593c6-120">See Also</span></span>  
 <span data-ttu-id="593c6-121">[Comment : générer un Assembly multifichier](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5) </span><span class="sxs-lookup"><span data-stu-id="593c6-121">[How to: Build a Multifile Assembly](http://msdn.microsoft.com/library/261c5583-8a76-412d-bda7-9b8ee3b131e5) </span></span>  
<span data-ttu-id="593c6-122"> [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="593c6-122"> [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="593c6-123"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span><span class="sxs-lookup"><span data-stu-id="593c6-123"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) </span></span>  
<span data-ttu-id="593c6-124"> [/ main](../../../visual-basic/reference/command-line-compiler/main.md) </span><span class="sxs-lookup"><span data-stu-id="593c6-124"> [/main](../../../visual-basic/reference/command-line-compiler/main.md) </span></span>  
<span data-ttu-id="593c6-125"> [Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span><span class="sxs-lookup"><span data-stu-id="593c6-125"> [/reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) </span></span>  
<span data-ttu-id="593c6-126"> [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) </span><span class="sxs-lookup"><span data-stu-id="593c6-126"> [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md) </span></span>  
<span data-ttu-id="593c6-127"> [Assemblys et le Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="593c6-127"> [Assemblies and the Global Assembly Cache](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="593c6-128"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="593c6-128"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="593c6-129"> [Assemblys friend](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)</span><span class="sxs-lookup"><span data-stu-id="593c6-129"> [Friend Assemblies](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)</span></span>
