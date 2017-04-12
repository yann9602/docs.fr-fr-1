---
title: /define (Visual Basic) | Documents Microsoft
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
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
caps.latest.revision: 15
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
ms.openlocfilehash: 48c3bae1c6cf5831f95ce86dbcf6adadab9d5db8
ms.lasthandoff: 03/13/2017

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
|`value`|Facultatif. Valeur à affecter au `symbol`. Si `value` est une chaîne, elle doit être entourée par des séquences de barre oblique inverse/guillemets (\\») au lieu de guillemets. Si aucune valeur n'est spécifiée, il prend la valeur True.|  
  
## <a name="remarks"></a>Notes  
 Le `/define` option a un effet semblable à l’aide un `#Const` directive de préprocesseur dans votre fichier source, excepté que les constantes définies avec `/define` sont publiques et s’appliquent à tous les fichiers dans le projet.  
  
 Vous pouvez utiliser les symboles créés par cette option avec la directive `#If`...`Then`...`#Else` pour effectuer une compilation conditionnelle des fichiers sources.  
  
 `/d` est la forme abrégée de `/define`.  
  
 Vous pouvez définir plusieurs symboles avec `/define` en utilisant une virgule pour séparer les définitions de symbole.  
  
|Pour définir /define dans l'environnement de développement intégré Visual Studio|  
|---|  
|1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Cliquez sur **Avancé**.<br />4.  Modifiez la valeur dans la **constantes personnalisées** boîte.|  
  
## <a name="example"></a>Exemple  
 Le code suivant définit deux constantes de compilation conditionnelle, puis les utilise.  
  
 [!code-vb[VbVbalrCompiler n °&45;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/define_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [#If... Then... #Else, Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [#Const, Directive](../../../visual-basic/language-reference/directives/const-directive.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
