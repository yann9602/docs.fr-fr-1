---
title: "Différences entre le passage d’un Argument par valeur et par référence (Visual Basic) | Documents Microsoft"
ms.custom: 
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
- ByRef keyword, passing arguments by reference
- Visual Basic code, procedures
- procedures, passing arguments
- ByVal keyword, passing arguments by value
- arguments [Visual Basic], passing by value or by reference
ms.assetid: 5f5c38fe-3e2d-494c-8fff-f4025b55ec93
caps.latest.revision: 14
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 93c515dd8524cde85555a27879baee00185f78e3
ms.lasthandoff: 03/13/2017

---
# <a name="differences-between-passing-an-argument-by-value-and-by-reference-visual-basic"></a>Différences entre le passage d’un argument par valeur et par référence (Visual Basic)
Lorsque vous passez un ou plusieurs arguments à une procédure, chaque argument correspond à un élément de programmation sous-jacent dans le code appelant. Vous pouvez passer la valeur de cet élément sous-jacent, ou une référence à celle-ci. Il s’agit du *mécanisme de transmission*.  
  
## <a name="passing-by-value"></a>passer par valeur  
 Vous passez un argument *par valeur* en spécifiant le [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) mot clé pour le paramètre correspondant dans la définition de procédure. Lorsque vous utilisez ce mécanisme de passage, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] copie la valeur de l’élément de programmation sous-jacent dans une variable locale de la procédure. Le code de procédure n’a pas accès à l’élément sous-jacent dans le code appelant.  
  
## <a name="passing-by-reference"></a>Le passage par référence  
 Vous passez un argument *par référence* en spécifiant le [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) mot clé pour le paramètre correspondant dans la définition de procédure. Lorsque vous utilisez ce mécanisme de passage, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit à la procédure une référence directe à l’élément de programmation sous-jacent dans le code appelant.  
  
## <a name="passing-mechanism-and-element-type"></a>Mécanisme de passage et le Type d’élément  
 Le choix du mécanisme de transmission n’est pas identique à la classification du type d’élément sous-jacent. Passage par valeur ou par référence fait référence à ce que [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fournit le code de procédure. Un type valeur ou un type référence fait référence à la façon dont un élément de programmation est stocké en mémoire.  
  
 Toutefois, le mécanisme de passage et le type d’élément sont reliés entre eux. La valeur d’un type référence est un pointeur vers les données ailleurs dans la mémoire. Cela signifie que lorsque vous passez un type référence par valeur, le code de procédure a un pointeur vers les données de l’élément sous-jacent, bien qu’il ne peut pas accéder à l’élément sous-jacent lui-même. Par exemple, si l’élément est une variable de tableau, le code de procédure n’a pas accès à la variable elle-même, mais il peut accéder aux membres du groupe.  
  
## <a name="ability-to-modify"></a>Capacité à modifier  
 Lorsque vous passez un élément non modifiable en tant qu’argument, la procédure ne peut jamais modifier dans le code appelant, qu’il soit passé `ByVal` ou `ByRef`.  
  
 Pour un élément modifiable, le tableau suivant résume l’interaction entre le type d’élément et le mécanisme de passage.  
  
|Type d'élément|Passé`ByVal`|Passé`ByRef`|  
|------------------|--------------------|--------------------|  
|Type de valeur (contient uniquement une valeur)|La procédure ne peut pas modifier la variable ou l’un de ses membres.|La procédure peut modifier la variable et ses membres.|  
|Type référence (contient un pointeur vers une instance de classe ou une structure)|La procédure ne peut pas modifier la variable, mais peut modifier les membres de l’instance vers laquelle il pointe.|La procédure peut modifier la variable et les membres de l’instance vers laquelle il pointe.|  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Comment : passer des Arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)   
 [Passage des Arguments par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)   
 [Différences entre les Arguments modifiables et non modifiables](./differences-between-modifiable-and-nonmodifiable-arguments.md)   
 [Comment : modifier la valeur d’un Argument de procédure](./how-to-change-the-value-of-a-procedure-argument.md)   
 [Comment : protéger un Argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)   
 [Comment : forcer un Argument à passer par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)   
 [Passage des Arguments par Position et par nom](./passing-arguments-by-position-and-by-name.md)   
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
