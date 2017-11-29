---
title: /optimize
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dead17435cd147bdcdf91bdc5b8e0aa651e9e9fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="optimize"></a><span data-ttu-id="4d792-102">/optimize</span><span class="sxs-lookup"><span data-stu-id="4d792-102">/optimize</span></span>
<span data-ttu-id="4d792-103">Active ou désactive les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="4d792-103">Enables or disables compiler optimizations.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d792-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d792-104">Syntax</span></span>  
  
```  
/optimize[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4d792-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="4d792-105">Arguments</span></span>  
  
|<span data-ttu-id="4d792-106">Terme</span><span class="sxs-lookup"><span data-stu-id="4d792-106">Term</span></span>|<span data-ttu-id="4d792-107">Définition</span><span class="sxs-lookup"><span data-stu-id="4d792-107">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="4d792-108">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="4d792-108">`+` &#124; `-`</span></span>|<span data-ttu-id="4d792-109">Facultatif.</span><span class="sxs-lookup"><span data-stu-id="4d792-109">Optional.</span></span> <span data-ttu-id="4d792-110">Le `/optimize-` option désactive les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="4d792-110">The `/optimize-` option disables compiler optimizations.</span></span> <span data-ttu-id="4d792-111">Le `/optimize+` option active les optimisations.</span><span class="sxs-lookup"><span data-stu-id="4d792-111">The `/optimize+` option enables optimizations.</span></span> <span data-ttu-id="4d792-112">Par défaut, les optimisations sont désactivées.</span><span class="sxs-lookup"><span data-stu-id="4d792-112">By default, optimizations are disabled.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d792-113">Remarques</span><span class="sxs-lookup"><span data-stu-id="4d792-113">Remarks</span></span>  
 <span data-ttu-id="4d792-114">Optimisations du compilateur que votre fichier de sortie plus petit, plus rapide et plus efficace.</span><span class="sxs-lookup"><span data-stu-id="4d792-114">Compiler optimizations make your output file smaller, faster, and more efficient.</span></span> <span data-ttu-id="4d792-115">Toutefois, étant donné que les optimisations entraînent une réorganisation du code dans le fichier de sortie `/optimize+` peut compliquer le débogage.</span><span class="sxs-lookup"><span data-stu-id="4d792-115">However, because optimizations result in code rearrangement in the output file, `/optimize+` can make debugging difficult.</span></span>  
  
 <span data-ttu-id="4d792-116">Tous les modules générés avec `/target:module` pour un assembly doit utiliser le même `/optimize` paramètres que l’assembly.</span><span class="sxs-lookup"><span data-stu-id="4d792-116">All modules generated with `/target:module` for an assembly must use the same `/optimize` settings as the assembly.</span></span> <span data-ttu-id="4d792-117">Pour plus d’informations, consultez [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span><span class="sxs-lookup"><span data-stu-id="4d792-117">For more information, see [/target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md).</span></span>  
  
 <span data-ttu-id="4d792-118">Vous pouvez combiner la `/optimize` et `/debug` options.</span><span class="sxs-lookup"><span data-stu-id="4d792-118">You can combine the `/optimize` and `/debug` options.</span></span>  
  
|<span data-ttu-id="4d792-119">Pour définir /optimize dans l’environnement de développement intégré Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4d792-119">To set /optimize in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="4d792-120">1.  Sélectionnez un projet dans l' **Explorateur de solutions**.</span><span class="sxs-lookup"><span data-stu-id="4d792-120">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="4d792-121">Dans le menu **Projet**, cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="4d792-121">On the **Project** menu, click **Properties**.</span></span><br />     <span data-ttu-id="4d792-122">Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span><span class="sxs-lookup"><span data-stu-id="4d792-122">For more information, see [Introduction to the Project Designer](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).</span></span><br /><span data-ttu-id="4d792-123">2.  Cliquez sur l’onglet **Compiler**.</span><span class="sxs-lookup"><span data-stu-id="4d792-123">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="4d792-124">3.  Cliquez sur le bouton **Avancées** .</span><span class="sxs-lookup"><span data-stu-id="4d792-124">3.  Click the **Advanced** button.</span></span><br /><span data-ttu-id="4d792-125">4.  Modifier la **activer les optimisations** case à cocher.</span><span class="sxs-lookup"><span data-stu-id="4d792-125">4.  Modify the **Enable optimizations** check box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="4d792-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="4d792-126">Example</span></span>  
 <span data-ttu-id="4d792-127">Le code suivant compile `T2.vb` et Active les optimisations du compilateur.</span><span class="sxs-lookup"><span data-stu-id="4d792-127">The following code compiles `T2.vb` and enables compiler optimizations.</span></span>  
  
```  
vbc t2.vb /optimize  
```  
  
## <a name="see-also"></a><span data-ttu-id="4d792-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4d792-128">See Also</span></span>  
 [<span data-ttu-id="4d792-129">Compilateur de ligne de commande de Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d792-129">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="4d792-130">/Debug (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d792-130">/debug (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/debug.md)  
 [<span data-ttu-id="4d792-131">Exemples de lignes de commande de compilation</span><span class="sxs-lookup"><span data-stu-id="4d792-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [<span data-ttu-id="4d792-132">/target (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d792-132">/target (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/target.md)
