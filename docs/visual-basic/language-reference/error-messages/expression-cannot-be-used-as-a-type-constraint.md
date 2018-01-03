---
title: "&#39; &lt;expression&gt;&#39; ne peut pas être utilisé comme contrainte de type"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc32061
- vbc32061
helpviewer_keywords: BC32061
ms.assetid: b17821b7-fa14-4397-a211-6e2a14079f09
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c7271018a93c97ed90dc272f7f5404c0f0a22d42
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="39ltexpressiongt39-cannot-be-used-as-a-type-constraint"></a>&#39; &lt;expression&gt;&#39; ne peut pas être utilisé comme contrainte de type
Une liste de contraintes contient une expression qui ne représente pas une contrainte valide sur un paramètre de type.  
  
 Une liste de contraintes impose des exigences sur l’argument de type passé au paramètre de type. Vous pouvez spécifier les exigences suivantes dans toute combinaison :  
  
-   L’argument de type doit implémenter une ou plusieurs interfaces  
  
-   L’argument de type doit hériter d’une classe au plus  
  
-   L’argument de type doit exposer un constructeur sans paramètre accessible par le code de création (ajoutez la contrainte `New` )  
  
 Si vous n’incluez pas de classe ni d’interface spécifique dans la liste de contraintes, vous pouvez imposer une condition plus générale en spécifiant l’une des obligations suivantes :  
  
-   L’argument de type doit être un type valeur (ajoutez la contrainte `Structure` )  
  
-   L’argument de type doit être un type référence (ajoutez la contrainte `Class` )  
  
 Vous ne pouvez pas spécifier à la fois `Structure` et `Class` pour le même paramètre de type et vous ne pouvez pas spécifier l’une des deux plusieurs fois.  
  
 **ID d’erreur :** BC32061  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez que l’expression et ses éléments sont correctement orthographiés.  
  
-   Si l’expression ne répond pas à la précédente liste d’exigences, supprimez-la de la liste des contraintes.  
  
-   Si l’expression fait référence à une interface ou une classe, vérifiez que le compilateur a accès à cette interface ou classe. Vous devrez peut-être qualifier son nom et ajouter une référence à votre projet. Pour plus d’informations, consultez « Références aux projets » dans [références aux éléments de déclaré](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Types génériques en Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Types valeur et types référence](../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Références aux éléments déclarés](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 
