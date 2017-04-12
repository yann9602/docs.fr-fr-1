---
title: "Classe ne prend pas en charge l’automatisation ou ne prend pas en charge l’interface attendue | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID430
dev_langs:
- VB
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: 11
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
ms.openlocfilehash: a5bdce085c676f5c9c20932939486e879bb13a36
ms.lasthandoff: 03/13/2017

---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a>La classe ne prend pas en charge Automation ou l'interface attendue
La classe que vous avez spécifiée dans l'appel de fonction `GetObject` ou `CreateObject` n'a exposé aucune interface programmable, ou vous avez modifié un projet .dll en .exe, ou vice versa.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Vérifiez la documentation de l'application qui a créé l'objet pour connaître les limitations relatives à l'utilisation de l'automatisation avec cette classe d'objet.  
  
2.  Si vous avez modifié un projet .dll en .exe ou vice versa, vous devez annuler manuellement l'inscription de l'ancien projet .dll ou .exe.  
  
## <a name="see-also"></a>Voir aussi  
 [Types d’erreurs](../../../visual-basic/programming-guide/language-features/error-types.md)   
 [Nous contacter](https://docs.microsoft.com/visualstudio/ide/talk-to-us)
