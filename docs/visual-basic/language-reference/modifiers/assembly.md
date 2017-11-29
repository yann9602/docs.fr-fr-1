---
title: Assembly (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
helpviewer_keywords:
- Assembly modifier
- Assembly keyword [Visual Basic]
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ef4434f0bc520abfc621567fc68e0b8bcfd6e381
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-visual-basic"></a><span data-ttu-id="c20e4-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c20e4-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="c20e4-103">Spécifie qu’un attribut situé au début d’un fichier source s’applique à la totalité de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="c20e4-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c20e4-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="c20e4-104">Remarks</span></span>  
 <span data-ttu-id="c20e4-105">Nombre d’attributs se rapport à un élément de programmation individuel, tel qu’une classe ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="c20e4-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="c20e4-106">Vous appliquez ce type d’attribut en attachant le bloc d’attributs, entre crochets (`< >`), directement à l’instruction de déclaration.</span><span class="sxs-lookup"><span data-stu-id="c20e4-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="c20e4-107">Si un attribut applique non seulement à l’élément suivant, mais aussi à la totalité de l’assembly, vous placez le bloc d’attributs au début du fichier source et identifiez l’attribut avec le `Assembly` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="c20e4-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="c20e4-108">Si elle s’applique à l’assembly actuel, vous utilisez la [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="c20e4-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="c20e4-109">Vous pouvez également appliquer un attribut à un assembly dans le fichier AssemblyInfo.vb, auquel cas il est inutile d’utiliser un bloc d’attributs dans votre fichier de code source principal.</span><span class="sxs-lookup"><span data-stu-id="c20e4-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c20e4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c20e4-110">See Also</span></span>  
 [<span data-ttu-id="c20e4-111">\<mot clé> du module</span><span class="sxs-lookup"><span data-stu-id="c20e4-111">Module \<keyword></span></span>](../../../visual-basic/language-reference/modifiers/module-keyword.md)  
 [<span data-ttu-id="c20e4-112">Vue d’ensemble des attributs</span><span class="sxs-lookup"><span data-stu-id="c20e4-112">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)

