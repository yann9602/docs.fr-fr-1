---
title: /optionexplicit | Documents Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
dev_langs:
- VB
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 16
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
ms.openlocfilehash: cfdad72c21b7886f9ea8a2d46e7c457087e7049d
ms.lasthandoff: 03/13/2017

---
# <a name="optionexplicit"></a>/optionexplicit
Indique au compilateur de signaler des erreurs si les variables ne sont pas déclarées avant leur utilisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Facultatif. Spécifiez `/optionexplicit+` pour requérir une déclaration explicite des variables. Le `/optionexplicit+` option est la valeur par défaut et est identique à `/optionexplicit`. La `/optionexplicit-` option permet une déclaration implicite des variables.  
  
## <a name="remarks"></a>Remarques  
 Si le fichier de code source contient une [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md), l’instruction substitue le `/optionexplicit` du paramètre de compilateur de ligne de commande.  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a>Pour définir /optionexplicit dans l’IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Sur le **projet** menu, cliquez sur **propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Cliquez sur l’onglet **Compiler**.  
  
3.  Modifiez la valeur dans la **Option Explicit** boîte.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile si `/optionexplicit-` est utilisé.  
  
 [!code-vb[VbVbalrCompiler n °&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Exemples de lignes de commande Compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
