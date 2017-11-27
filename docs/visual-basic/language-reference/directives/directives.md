---
title: Directives (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- directives, Visual Basic compiler
- Visual Basic code, directives
- directives
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8219f17f1b8093b4d02b370c7b008101923b1873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="directives-visual-basic"></a><span data-ttu-id="35487-102">Directives (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35487-102">Directives (Visual Basic)</span></span>
<span data-ttu-id="35487-103">Les rubriques de cette section documentent les directives du compilateur de code source Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="35487-103">The topics in this section document the Visual Basic source code compiler directives.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="35487-104">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="35487-104">In This Section</span></span>  
 <span data-ttu-id="35487-105">[#Const, Directive](../../../visual-basic/language-reference/directives/const-directive.md) --définir une constante de compilation</span><span class="sxs-lookup"><span data-stu-id="35487-105">[#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) -- Define a compiler constant</span></span>  
  
 <span data-ttu-id="35487-106">[Directive #ExternalSource](../../../visual-basic/language-reference/directives/externalsource-directive.md) --indiquent un mappage entre des lignes sources et du texte externe à la source</span><span class="sxs-lookup"><span data-stu-id="35487-106">[#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) -- Indicate a mapping between source lines and text external to the source</span></span>  
  
 <span data-ttu-id="35487-107">[#If... ... #Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) --compiler des blocs de code sélectionnés</span><span class="sxs-lookup"><span data-stu-id="35487-107">[#If...Then...#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) -- Compile selected blocks of code</span></span>  
  
 <span data-ttu-id="35487-108">[Directive #Region](../../../visual-basic/language-reference/directives/region-directive.md) : réduire et masquer des sections de code dans l’éditeur Visual Studio</span><span class="sxs-lookup"><span data-stu-id="35487-108">[#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) -- Collapse and hide sections of code in the Visual Studio editor</span></span>  
  
 <span data-ttu-id="35487-109">**#Disable, #Enable** : désactiver et activer des avertissements spécifiques pour les régions de code.</span><span class="sxs-lookup"><span data-stu-id="35487-109">**#Disable, #Enable** -- Disable and enable specific warnings for regions of code.</span></span>  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
```  
  
 <span data-ttu-id="35487-110">Vous pouvez désactiver et activer une liste séparée par des virgules de codes d'avertissement.</span><span class="sxs-lookup"><span data-stu-id="35487-110">You can disable and enable a comma-separated list of warning codes too.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="35487-111">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="35487-111">Related Sections</span></span>  
 [<span data-ttu-id="35487-112">Informations de référence sur le langage Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35487-112">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
  
 [<span data-ttu-id="35487-113">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35487-113">Visual Basic</span></span>](../../../visual-basic/index.md)
