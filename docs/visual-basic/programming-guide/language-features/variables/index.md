---
title: Variables en Visual Basic | Microsoft Docs
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: 9a19838abed2d947e8e7ebf96fa4603feb208012
ms.contentlocale: fr-fr
ms.lasthandoff: 05/26/2017

---
<a id="variables-in-visual-basic" class="xliff"></a>

# Variables en Visual Basic
Il est souvent nécessaire de stocker des valeurs lors de l’exécution de calculs avec [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Par exemple, vous pouvez être amené à calculer plusieurs valeurs, à les comparer et à effectuer différentes opérations sur ces valeurs, en fonction du résultat de la comparaison. Vous devez conserver les valeurs si vous souhaitez les comparer.  
  
<a id="usage" class="xliff"></a>

## Utilisation  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], comme la plupart des langages de programmation, utilise des variables pour le stockage des valeurs. Une *variable* a un nom (le mot que vous utilisez pour faire référence à la valeur que la variable contient). Une variable a également un type de données (lequel détermine le genre des données que la variable peut stocker). Une variable peut représenter un tableau si elle doit stocker un ensemble indexé d’éléments de données étroitement liés.  
  
 L’inférence de type de variable locale vous permet de déclarer des variables sans déclarer explicitement un type de données. À la place, le compilateur déduit le type de la variable à partir du type de l’expression d’initialisation. Pour plus d’informations, consultez [Inférence de type de variable locale](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) et [Option Infer, instruction](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
<a id="assigning-values" class="xliff"></a>

## Assignation de valeurs  
 Vous utilisez des instructions d’assignation pour effectuer des calculs et assigner le résultat à une variable, comme le montre l’exemple suivant.  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  Dans cet exemple, le signe égal (`=`) représente un opérateur d’assignation, et non un opérateur d’égalité. La valeur est assignée à la variable `applesSold`.  
  
 Pour plus d’informations, consultez [Guide pratique pour placer des données dans et en dehors d’une variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
<a id="variables-and-properties" class="xliff"></a>

## Variables et propriétés  
 À l’instar d’une variable, une *propriété* représente une valeur à laquelle vous pouvez accéder. Toutefois, elle est plus complexe qu’une variable. Une propriété utilise des blocs de code qui contrôlent la définition et la récupération de sa valeur. Pour plus d’informations, consultez [Différences entre les propriétés et les variables en Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
<a id="see-also" class="xliff"></a>

## Voir aussi  
 [Déclaration de variable](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Variables objet](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)   
 [Dépannage des variables](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)   
 [Guide pratique pour placer des données dans et en dehors d’une variable](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)   
 [Différences entre les propriétés et les variables en Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)   
 [Inférence de type local](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
