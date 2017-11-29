---
title: "Impossible de faire référence à un membre instance d'une classe à partir d'une méthode partagée ou d'un initialiseur de membre partagé sans une instance explicite de la classe"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30369
- bc30369
helpviewer_keywords:
- Shared
- BC30369
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6a15d36c0b3a4d6b1657d583de0dc61621da960d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="cannot-refer-to-an-instance-member-of-a-class-from-within-a-shared-method-or-shared-member-initializer-without-an-explicit-instance-of-the-class"></a>Impossible de faire référence à un membre instance d'une classe à partir d'une méthode partagée ou d'un initialiseur de membre partagé sans une instance explicite de la classe
Vous avez tenté de référencer un membre non partagé d’une classe à partir d’une procédure partagée. L’exemple suivant illustre une telle situation.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 Dans l’exemple précédent, l’instruction d’assignation `x = 10` génère ce message d’erreur. Il s’agit, car une procédure partagée tente d’accéder à une variable d’instance.  
  
 La variable `x` est un membre d’instance, car il n’est pas déclaré en tant que [partagé](../../../visual-basic/language-reference/modifiers/shared.md). Chaque instance de classe `sample` contient sa propre variable individuelle `x`. Lorsqu’une instance définit ou modifie la valeur de `x`, il n’affecte pas la valeur de `x` dans n’importe quelle autre instance.  
  
 Toutefois, la procédure `setX` est `Shared` entre toutes les instances de classe `sample`. Cela signifie qu’il n’est pas associé à une instance de la classe, mais au lieu de cela fonctionne indépendamment des instances individuelles. Car il ne possède aucune connexion avec une instance particulière, `setX` ne peut pas accéder à une variable d’instance. Il doit fonctionner que sur `Shared` variables. Lorsque `setX` définit ou modifie la valeur d’une variable partagée, que la nouvelle valeur est accessible à toutes les instances de la classe.  
  
 **ID d’erreur :** BC30369  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Décidez si vous souhaitez que le membre doit être partagé entre toutes les instances de la classe ou conservé individuelles pour chaque instance.  
  
2.  Si vous souhaitez une seule copie du membre à être partagé entre toutes les instances, ajoutez le `Shared` mot clé à la déclaration de membre. Conserver le `Shared` mot clé dans la déclaration de procédure.  
  
3.  Si vous souhaitez que chaque instance possède sa propre copie individuelle du membre, ne spécifiez pas `Shared` pour la déclaration de membre. Supprimer le `Shared` (mot clé) à partir de la déclaration de procédure.  
  
## <a name="see-also"></a>Voir aussi  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
