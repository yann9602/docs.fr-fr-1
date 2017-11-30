---
title: /debug (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1c90b28f1df18e7e0a4f9e22730e1c3476fa650
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="debug-visual-basic"></a>/debug (Visual Basic)
Indique au compilateur de générer des informations de débogage et les placer dans les fichiers de sortie.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terme|Définition|  
|---|---|  
|`+` &#124; `-`|Facultatif. Spécification de `+` ou `/debug` indique au compilateur de générer des informations de débogage et les placer dans un fichier .pdb. Spécification de `-` a le même effet que de ne pas spécifier `/debug`.|  
|`full` &#124; `pdbonly`|Facultatif. Indique le type d'informations de débogage générées par le compilateur. Si vous ne spécifiez pas `/debug:pdbonly`, la valeur par défaut est `full`, ce qui vous permet d’associer un débogueur au programme en cours d’exécution. Le `pdbonly` argument permet le débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche du code en langage assembleur uniquement lorsque le programme en cours d’exécution est attaché au débogueur.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez cette option pour créer des versions Debug. Si vous ne spécifiez pas `/debug`, `/debug+`, ou `/debug:full`, vous ne pouvez pas déboguer le fichier de sortie de votre programme.  
  
 Par défaut, les informations de débogage ne sont pas émises (`/debug-`). Pour émettre des informations de débogage, spécifiez `/debug` ou `/debug+`.  
  
 Pour plus d’informations sur la configuration des performances de débogage d’une application, consultez [Simplification du débogage d’une image](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Pour définir /debug dans Visual Studio environnement de développement intégré|  
|---|  
|1.  Après avoir sélectionné un projet dans l’ **Explorateur de solutions**, dans le menu **Projet** , cliquez sur **Propriétés**. Pour plus d’informations, consultez [Introduction au Concepteur de projets](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l’onglet **Compiler**.<br />3.  Cliquez sur **Options avancées de compilation**.<br />4.  Modifiez la valeur dans la **générer des infos de débogage** boîte.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant place des informations de débogage dans le fichier de sortie `App.exe`.  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
