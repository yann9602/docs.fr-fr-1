---
title: Assembly (Visual Basic) | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assembly
- vb.AssemblyAttribute
- Assembly
dev_langs:
- VB
helpviewer_keywords:
- Assembly modifier
- Assembly keyword
- attribute blocks, Assembly keyword
ms.assetid: 925e7471-3bdf-4b51-bb93-cbcfc6efc52f
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
ms.openlocfilehash: b83102c24c80b7ee6ec4c0ffc4a446e26b7811cf
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="assembly-visual-basic"></a><span data-ttu-id="9d649-102">Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9d649-102">Assembly (Visual Basic)</span></span>
<span data-ttu-id="9d649-103">Spécifie qu’un attribut au début d’un fichier source s’applique à la totalité de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="9d649-103">Specifies that an attribute at the beginning of a source file applies to the entire assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9d649-104">Remarques</span><span class="sxs-lookup"><span data-stu-id="9d649-104">Remarks</span></span>  
 <span data-ttu-id="9d649-105">Beaucoup d’attributs appartiennent à un élément de programmation, tel qu’une classe ou une propriété.</span><span class="sxs-lookup"><span data-stu-id="9d649-105">Many attributes pertain to an individual programming element, such as a class or property.</span></span> <span data-ttu-id="9d649-106">Vous appliquez ce type d’attribut en liant le bloc d’attributs, entre crochets (`< >`), directement à l’instruction de déclaration.</span><span class="sxs-lookup"><span data-stu-id="9d649-106">You apply such an attribute by attaching the attribute block, within angle brackets (`< >`), directly to the declaration statement.</span></span>  
  
 <span data-ttu-id="9d649-107">Si un attribut appartient non seulement à l’élément suivant, mais aussi à l’intégralité de l’assembly, vous placez le bloc d’attributs au début du fichier source et identifiez l’attribut avec le `Assembly` (mot clé).</span><span class="sxs-lookup"><span data-stu-id="9d649-107">If an attribute pertains not only to the following element but to the entire assembly, you place the attribute block at the beginning of the source file and identify the attribute with the `Assembly` keyword.</span></span> <span data-ttu-id="9d649-108">Si elle s’applique à l’assembly actuel, vous utilisez la [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) (mot clé).</span><span class="sxs-lookup"><span data-stu-id="9d649-108">If it applies to the current assembly module, you use the [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) keyword.</span></span>  
  
 <span data-ttu-id="9d649-109">Vous pouvez également appliquer un attribut à un assembly dans le fichier AssemblyInfo.vb, auquel cas vous n’avez pas à utiliser un bloc d’attributs dans votre fichier de code source principal.</span><span class="sxs-lookup"><span data-stu-id="9d649-109">You can also apply an attribute to an assembly in the AssemblyInfo.vb file, in which case you do not have to use an attribute block in your main source-code file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d649-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9d649-110">See Also</span></span>  
 <span data-ttu-id="9d649-111">[Module \<mot-clé >](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span><span class="sxs-lookup"><span data-stu-id="9d649-111">[Module \<keyword>](../../../visual-basic/language-reference/modifiers/module-keyword.md) </span></span>  
<span data-ttu-id="9d649-112"> [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)</span><span class="sxs-lookup"><span data-stu-id="9d649-112"> [Attributes overview](../../../visual-basic/programming-guide/concepts/attributes/index.md)</span></span>


