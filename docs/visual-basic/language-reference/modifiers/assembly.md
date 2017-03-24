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
author: stevehoag
ms.author: shoag
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: b496b96360ff891554ab71ba2b3227b2dabbc416
ms.lasthandoff: 03/13/2017

---
# <a name="assembly-visual-basic"></a>Assembly (Visual Basic)
Spécifie qu’un attribut au début d’un fichier source s’applique à la totalité de l’assembly.  
  
## <a name="remarks"></a>Remarques  
 Beaucoup d’attributs appartiennent à un élément de programmation, tel qu’une classe ou une propriété. Vous appliquez ce type d’attribut en liant le bloc d’attributs, entre crochets (`< >`), directement à l’instruction de déclaration.  
  
 Si un attribut appartient non seulement à l’élément suivant, mais aussi à l’intégralité de l’assembly, vous placez le bloc d’attributs au début du fichier source et identifiez l’attribut avec le `Assembly` (mot clé). Si elle s’applique à l’assembly actuel, vous utilisez la [Module](../../../visual-basic/language-reference/modifiers/module-keyword.md) (mot clé).  
  
 Vous pouvez également appliquer un attribut à un assembly dans le fichier AssemblyInfo.vb, auquel cas vous n’avez pas à utiliser un bloc d’attributs dans votre fichier de code source principal.  
  
## <a name="see-also"></a>Voir aussi  
 [Module \<mot-clé >](../../../visual-basic/language-reference/modifiers/module-keyword.md)   
 [Vue d’ensemble des attributs](../../../visual-basic/programming-guide/concepts/attributes/index.md)


