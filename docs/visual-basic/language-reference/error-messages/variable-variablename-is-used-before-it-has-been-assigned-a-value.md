---
title: "Variable &quot;&lt;variablename&gt;&quot; est utilisée avant qu’il a reçu une valeur | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
dev_langs:
- VB
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: 10
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
ms.openlocfilehash: 7ad1f392fae2f90e366277b7b531d96011648866
ms.lasthandoff: 03/13/2017

---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>Variable '&lt;variablename&gt;' est utilisée avant qu’il a reçu une valeur
Variable '\<variablename >' est utilisée avant qu’il a reçu une valeur. Cela peut provoquer une exception de référence null au moment de l’exécution.  
  
 Une application a au moins un chemin d’accès possible via son code qui lit une variable avant toute valeur lui est attribuée.  
  
 Si aucune valeur n’a jamais été assignée à une variable, elle contient la valeur par défaut de son type de données. Pour un type de données de référence, cette valeur par défaut est [rien](../../../visual-basic/language-reference/nothing.md). Lecture d’une variable de référence qui a la valeur `Nothing` peut entraîner une <xref:System.NullReferenceException>dans certaines circonstances.</xref:System.NullReferenceException>  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements comme des erreurs, consultez la page [configuration d’avertissements en Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** compilation BC42104  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez votre logique de flux de contrôle et assurez-vous que la variable a une valeur valide avant que le contrôle passe à toute instruction qui le lit.  
  
-   Pour garantir que la variable a toujours une valeur valide doit initialiser dans le cadre de sa déclaration. Consultez « Initialisation » dans [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)   
 [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)   
 [Dépannage des variables](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
