---
title: "Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30369"
  - "bc30369"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Shared"
  - "BC30369"
ms.assetid: 39d9466b-c1f3-4406-91a5-3d6c52d23a3d
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Cannot refer to an instance member of a class from within a shared method or shared member initializer without an explicit instance of the class
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous avez essayé de faire référence au membre non partagé d'une classe à partir d'une procédure partagée.  L'exemple suivant illustre une telle situation.  
  
```  
Class sample  
    Public x as Integer  
    Public Shared Sub setX()  
        x = 10  
    End Sub  
End Class  
```  
  
 Dans l'exemple précédent, l'instruction d'assignation `x = 10` génère ce message d'erreur.  Cela est dû au fait qu'une procédure partagée tente d'accéder à une variable d'instance.  
  
 La variable `x` est un membre d'instance parce qu'elle n'est pas déclarée en tant que [Shared](../../../visual-basic/language-reference/modifiers/shared.md).  Chaque instance de la classe `sample` contient sa propre variable individuelle `x`.  Lorsqu'une instance définit ou modifie la valeur de `x`, elle n'affecte la valeur de `x` dans aucune autre instance.  
  
 Toutefois, la procédure `setX` est `Shared` entre toutes les instances de la classe `sample`.  Cela signifie qu'elle n'est associée à aucune instance de la classe, mais qu'elle fonctionne plutôt indépendamment des instances individuelles.  N'ayant pas de connexion avec une instance particulière, la procédure `setX` ne peut pas accéder à une variable d'instance.  Elle ne doit fonctionner que sur les variables `Shared`.  Lorsque `setX` définit ou modifie la valeur d'une variable partagée, la nouvelle valeur est accessible à toutes les instances de la classe.  
  
 **ID d'erreur :** BC30369  
  
### Pour corriger cette erreur  
  
1.  Déterminez si vous souhaitez partager le membre entre toutes les instances de la classe ou en laisser une copie individuelle pour chaque instance.  
  
2.  Si vous souhaitez qu'une seule copie du membre soit partagée entre toutes les instances, ajoutez le mot clé `Shared` à la déclaration de membre.  Conservez le mot clé `Shared` dans la déclaration de procédure.  
  
3.  Si vous souhaitez que chaque instance possède sa propre copie individuelle du membre, ne spécifiez pas `Shared` dans la déclaration de membre.  Supprimez le mot clé `Shared` de la déclaration de procédure.  
  
## Voir aussi  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)