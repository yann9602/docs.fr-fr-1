---
title: "Différences entre les arguments modifiables et non modifiables (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedure arguments
- arguments [Visual Basic], nonmodifiable
- Visual Basic code, procedures
- arguments [Visual Basic], modifiable
ms.assetid: 87b2df69-e1f7-4657-9caf-b3f48d693428
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab108d064f5c6740f80328a9b6db4785334550ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-modifiable-and-nonmodifiable-arguments-visual-basic"></a>Différences entre les arguments modifiables et non modifiables (Visual Basic)
Lorsque vous appelez une procédure, vous passez généralement un ou plusieurs arguments à celui-ci. Chaque argument correspond à un élément de programmation sous-jacent. Les éléments sous-jacents et les arguments peuvent être modifiables ou non.  
  
## <a name="modifiable-and-nonmodifiable-elements"></a>Éléments non modifiables et non modifiables  
 Un élément de programmation peut être un *élément modifiable*, qui peut avoir la valeur est modifiable ou un *élément non modifiable*, qui a une valeur fixe, une fois qu’elle a été créée.  
  
 Le tableau suivant répertorie les éléments de programmation modifiables et non modifiables.  
  
|Éléments modifiables|Éléments non modifiables|  
|-------------------------|----------------------------|  
|Les variables locales (déclarées à l’intérieur des procédures), y compris les variables d’objet, à l’exception en lecture seule|Propriétés, champs et variables en lecture seule|  
|Champs (variables membres de modules, les classes et structures), à l’exception en lecture seule|Littéraux et des constantes|  
|Propriétés, à l’exception en lecture seule|Membres de l’énumération|  
|Éléments de tableau|Expressions (même si leurs éléments sont modifiables)|  
  
## <a name="modifiable-and-nonmodifiable-arguments"></a>Arguments modifiables et non modifiables  
 A *argument modifiable* est doté d’un élément sous-jacent modifiable. Le code appelant peut stocker une nouvelle valeur à tout moment, et si vous passez l’argument [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md), le code dans la procédure peut également modifier l’élément sous-jacent dans le code appelant.  
  
 A *argument non modifiable* a un élément non modifiable sous-jacent ou est passé [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md). La procédure ne peut pas modifier l’élément sous-jacent dans le code appelant, même si elle est un élément modifiable. S’il est un élément non modifiable, le code appelant ne peut pas modifier.  
  
 La procédure appelée peut modifier sa copie locale d’un argument non modifiable, mais cette modification n’affecte pas l’élément sous-jacent dans le code appelant.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures](./index.md)  
 [Paramètres et arguments d’une procédure](./procedure-parameters-and-arguments.md)  
 [Guide pratique : passer des arguments à une procédure](./how-to-pass-arguments-to-a-procedure.md)  
 [Passage d’un argument par valeur et par référence](./passing-arguments-by-value-and-by-reference.md)  
 [Différences entre le passage d’un argument par valeur et par référence](./differences-between-passing-an-argument-by-value-and-by-reference.md)  
 [Guide pratique : modifier la valeur d’un argument de la procédure](./how-to-change-the-value-of-a-procedure-argument.md)  
 [Guide pratique : protéger un argument de procédure contre les modifications de valeur](./how-to-protect-a-procedure-argument-against-value-changes.md)  
 [Guide pratique : forcer le passage d’un argument par valeur](./how-to-force-an-argument-to-be-passed-by-value.md)  
 [Passage des arguments par position et par nom](./passing-arguments-by-position-and-by-name.md)  
 [Types valeur et types référence](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
