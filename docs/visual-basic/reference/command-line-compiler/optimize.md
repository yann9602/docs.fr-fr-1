---
title: /Optimize | Documents Microsoft
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
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization, enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
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
ms.openlocfilehash: f01ab17d4a2f5d123538294a7a13d7a6d7a40267
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="optimize"></a><span data-ttu-id="1e702-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="1e702-102">/optimize</span></span>
<span data-ttu-id="1e702-103">Active ou désactive les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="1e702-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e702-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e702-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="1e702-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="1e702-105">Arguments</span></span>  
  
|<span data-ttu-id="1e702-106">Terme</span><span class="sxs-lookup"><span data-stu-id="1e702-106">Term</span></span>|<span data-ttu-id="1e702-107">Définition</span><span class="sxs-lookup"><span data-stu-id="1e702-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="1e702-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="1e702-108">`+` &#124; `-`</span></span>|<span data-ttu-id="1e702-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="1e702-109">Optional.</span></span> <span data-ttu-id="1e702-110">La `/optimize-` option désactive les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="1e702-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="1e702-111">La `/optimize+` option active les optimisations.</span><span class="sxs-lookup"><span data-stu-id="1e702-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="1e702-112">Par défaut, les optimisations sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="1e702-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e702-113">Notes</span><span class="sxs-lookup"><span data-stu-id="1e702-113">Remarks</span></span>  
 <span data-ttu-id="1e702-114">Optimisations du compilateur que votre fichier de sortie plus petit, plus rapide et plus efficace.</span><span class="sxs-lookup"><span data-stu-id="1e702-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="1e702-115">Toutefois, étant donné que les optimisations entraînent une réorganisation du code dans le fichier de sortie `/optimize+` peut compliquer le débogage.</span><span class="sxs-lookup"><span data-stu-id="1e702-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="1e702-116">Tous les modules générés avec `/target:module` pour un assembly doit utiliser le même `/optimize` paramètres que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="1e702-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="1e702-117">Pour plus d’informations, consultez [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="1e702-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="1e702-118">Vous pouvez combiner les `/optimize` et `/debug` options.</span><span class="sxs-lookup"><span data-stu-id="1e702-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="1e702-119">Pour définir /optimize dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1e702-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="1e702-120">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="1e702-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="1e702-121">Sur le **projet** menu, cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1e702-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="1e702-122">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="1e702-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="1e702-123">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="1e702-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="1e702-124">3.  Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="1e702-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="1e702-125">4.  Modifier la **activer les optimisations** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="1e702-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e702-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="1e702-126">Example</span></span>  
 <span data-ttu-id="1e702-127">Le code suivant compile `T2.vb` et Active les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="1e702-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e702-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1e702-128">See Also</span></span>  
 <span data-ttu-id="1e702-129">[Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md) </span><span class="sxs-lookup"><span data-stu-id="1e702-129">[Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md) </span></span>  
<span data-ttu-id="1e702-130"> [/Debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span><span class="sxs-lookup"><span data-stu-id="1e702-130"> [/debug (Visual Basic)](../../../visual-basic/reference/command-line-compiler/debug.md) </span></span>  
<span data-ttu-id="1e702-131"> [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span><span class="sxs-lookup"><span data-stu-id="1e702-131"> [Sample Compilation Command Lines](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md) </span></span>  
<span data-ttu-id="1e702-132"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)</span><span class="sxs-lookup"><span data-stu-id="1e702-132"> [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)</span></span>
