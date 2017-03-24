---
title: "Procédures récursives (Visual Basic) | Documents Microsoft"
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
- Visual Basic code, procedures
- procedures, that call themselves
- procedures, recursive
- procedures, calling
- recursive procedures
- functions [Visual Basic], calling recursively
- recursion
ms.assetid: ba1d3962-b4c3-48d3-875e-96fdb4198327
caps.latest.revision: 13
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
ms.openlocfilehash: 9fc95cd5f7cfd5637f6282c6ef571eb81bac1816
ms.lasthandoff: 03/13/2017

---
# <a name="recursive-procedures-visual-basic"></a>Procédures récursives (Visual Basic)
A *récursive* procédure est celle qui s’appelle elle-même. En général, cela n’est pas le moyen le plus efficace pour écrire [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] code.  
  
 La procédure suivante utilise la récursivité pour calculer la factorielle de son argument d’origine.  
  
 [!code-vb[VbVbcnProcedures&#51;](./codesnippet/VisualBasic/recursive-procedures_1.vb)]  
  
## <a name="considerations-with-recursive-procedures"></a>Considérations sur les procédures récursives  
 **Conditions de limitation**. Vous devez concevoir une procédure récursive à tester au moins une condition qui peut mettre fin à la récurrence, et vous devez également gérer le cas où aucune de ces conditions n’est satisfaite un nombre raisonnable d’appels récursifs. Au moins une condition qui peut être satisfaite sans erreur, votre procédure s’exécute à un risque élevé d’exécution dans une boucle infinie.  
  
 **Utilisation de la mémoire**. Votre application dispose d’une quantité limitée d’espace pour les variables locales. Chaque fois qu’une procédure appelle elle-même, elle davantage d’espace utilise des copies supplémentaires de ses variables locales. Si ce processus se poursuit indéfiniment, il provoque finalement un <xref:System.StackOverflowException>erreur.</xref:System.StackOverflowException>  
  
 **L’efficacité**. Vous pouvez presque toujours remplacer une boucle de récurrence. Une boucle n’a pas la surcharge de passer des arguments, initialiser le stockage supplémentaire et retourner des valeurs. Votre performance peut être considérablement améliorée sans appels récurrents.  
  
 **Récurrence mutuelle**. Vous pouvez observer une performance médiocre ou même une boucle infinie, si deux procédures s’appellent mutuellement. Ce type de conception présente les mêmes problèmes qu’une procédure récursive simple, mais il peut être difficile à détecter et à déboguer.  
  
 **Appel avec parenthèses**. Lorsqu’un `Function` procédure appelle de manière récursive, vous devez suivre le nom de la procédure de parenthèses, même s’il n’existe aucune liste d’arguments. Dans le cas contraire, le nom de fonction est utilisé en tant que représentant la valeur de retour de la fonction.  
  
 **Test**. Si vous écrivez une procédure récursive, vous devez la tester soigneusement pour vous assurer qu’il répond toujours à certaines conditions de limitation. Vous devez également vous assurer que vous ne pouvez pas manquer de mémoire en raison d’un trop grand nombre d’appels récursive.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.StackOverflowException></xref:System.StackOverflowException>   
 [Procédures](./index.md)   
 [Procédures Sub](./sub-procedures.md)   
 [Procédures Function](./function-procedures.md)   
 [Procédures de propriété](./property-procedures.md)   
 [Procédures d’opérateur](./operator-procedures.md)   
 [Arguments et paramètres de procédure](./procedure-parameters-and-arguments.md)   
 [Surcharge de procédure](./procedure-overloading.md)   
 [Procédures de dépannage](./troubleshooting-procedures.md)   
 [Structures de boucle](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Dépannage des exceptions : System.StackOverflowException](http://msdn.microsoft.com/library/51b71217-c507-4f5b-bc35-0236180d7968)
