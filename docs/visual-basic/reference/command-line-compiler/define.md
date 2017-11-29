---
title: /define (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8bc3056c3e2d7a4aad469d3bf2c404f5f5248384
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="define-visual-basic"></a>/define (Visual Basic)
Définit des constantes conditionnelles du compilateur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/define:["]symbol[=value][,symbol[=value]]["]  
' -or-  
/d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`symbol`|Requis. Symbole à définir.|  
|`value`|Facultatif. Valeur à affecter au `symbol`. Si `value` est une chaîne, elle doit être entourée par des séquences de barre oblique inverse/guillemets (\\») au lieu des guillemets doubles. Si aucune valeur n'est spécifiée, il prend la valeur True.|  
  
## <a name="remarks"></a>Remarques  
 Le `/define` option a un effet semblable à l’aide un `#Const` directive de préprocesseur dans votre fichier source, excepté que les constantes définies avec `/define` sont publiques et s’appliquent à tous les fichiers dans le projet.  
  
 Vous pouvez utiliser les symboles créés par cette option avec la directive `#If`...`Then`...`#Else` pour effectuer une compilation conditionnelle des fichiers sources.  
  
 `/d` est la forme abrégée de `/define`.  
  
 Vous pouvez définir plusieurs symboles avec `/define` en utilisant une virgule pour séparer les définitions de symbole.  
  
|Pour définir /define dans l'environnement de développement intégré Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Cliquez sur **Avancé**.<br />4.  Modifiez la valeur dans la **constantes personnalisées** boîte.|  
  
## <a name="example"></a>Exemple  
 Le code suivant définit deux constantes de compilation conditionnelle, puis les utilise.  
  
 [!code-vb[VbVbalrCompiler#45](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [#If...Then...#Else, directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)  
 [#Const (directive)](../../../visual-basic/language-reference/directives/const-directive.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
