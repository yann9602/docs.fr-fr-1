---
title: /optionexplicit
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionexplicit
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1e701addb31b361e55f2761f441c23deaef7c10d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="optionexplicit"></a>/optionexplicit
Indique au compilateur de signaler des erreurs si les variables ne sont pas déclarées avant leur utilisation.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Facultatif. Spécifiez `/optionexplicit+` pour exiger la déclaration explicite des variables. Le `/optionexplicit+` option est la valeur par défaut et est identique à `/optionexplicit`. Le `/optionexplicit-` option permet une déclaration implicite des variables.  
  
## <a name="remarks"></a>Notes  
 Si le fichier de code source contient un [Option Explicit, instruction](../../../visual-basic/language-reference/statements/option-explicit-statement.md), l’instruction substitue le `/optionexplicit` paramètre du compilateur de ligne de commande.  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a>Pour définir /optionexplicit dans l’IDE de Visual Studio  
  
1.  Sélectionnez un projet dans l' **Explorateur de solutions**. Dans le menu **Projet**, cliquez sur **Propriétés**.   
  
2.  Cliquez sur l’onglet **Compiler**.  
  
3.  Modifiez la valeur dans la **Option Explicit** boîte.  
  
## <a name="example"></a>Exemple  
 Le code suivant compile si `/optionexplicit-` est utilisé.  
  
 [!code-vb[VbVbalrCompiler#5](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)  
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Explicit (instruction)](../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Valeurs par défaut Visual Basic, Projets, boîte de dialogue Options](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
