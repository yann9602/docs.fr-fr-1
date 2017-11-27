---
title: "Variable &#39; &lt;variablename&gt;&#39; est utilisée avant qu’il a reçu une valeur"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords: BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 201667c250e15bb9af73e64e2d8c924c1952d1be
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>Variable &#39; &lt;variablename&gt;&#39; est utilisée avant qu’il a reçu une valeur
Variable '\<nom_variable >' est utilisée avant qu’il a reçu une valeur. Cela peut provoquer une exception de référence null au moment de l’exécution.  
  
 Une application possède au moins un chemin possible du code qui lit une variable avant de n’importe quelle valeur lui est attribuée.  
  
 Si aucune valeur n’a jamais été assignée à une variable, elle contient la valeur par défaut de son type de données. Pour un type de données de référence, cette valeur par défaut est [rien](../../../visual-basic/language-reference/nothing.md). La lecture d’une variable de référence qui a la valeur `Nothing` peut provoquer une <xref:System.NullReferenceException> dans certaines circonstances.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou le traitement des avertissements en tant qu’erreurs, consultez [configuration des avertissements en Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** compilation BC42104  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez votre logique de flux de contrôle et assurez-vous que la variable a une valeur valide avant que le contrôle passe à une instruction qui le lit.  
  
-   Pour garantir que la variable a toujours une valeur valide est pour l’initialisation dans le cadre de sa déclaration. Consultez « Initialisation » dans [Dim, instruction](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Dim (instruction)](../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Déclaration de variable](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Dépannage des variables](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
