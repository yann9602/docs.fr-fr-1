---
title: "Erreur d’automatisation | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID440
dev_langs:
- VB
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
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
ms.openlocfilehash: 0e48d5bde8b0fd3d31265d3d287623e32c0ea4cf
ms.lasthandoff: 03/13/2017

---
# <a name="automation-error"></a>Erreur Automation
Une erreur s'est produite pendant l'exécution d'une méthode ou l'obtention / la définition d'une propriété de variable objet. L'application qui a créé l'objet a signalé l'erreur.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez les propriétés de l'objet `Err` pour déterminer la source et la nature de l'erreur.  
  
2.  Utilisez la `On Error Resume Next` instruction immédiatement avant l’instruction d’accès et vérifiez la présence d’erreurs immédiatement après l’instruction d’accès.  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Nous contacter](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
