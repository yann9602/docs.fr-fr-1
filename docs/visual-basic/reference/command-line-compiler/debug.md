---
title: "/debug (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "debug compiler switches"
  - "/debug compiler option [Visual Basic]"
  - "-debug compiler option [Visual Basic]"
  - "debug compiler option [Visual Basic]"
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# /debug (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Entraîne le compilateur à générer des informations de débogage et à les placer dans le ou les fichiers de sortie.  
  
## Syntaxe  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
```  
  
## Arguments  
  
|||  
|-|-|  
|Terme|Définition|  
|`+`  &#124; `-`|Facultatif.  Si vous spécifiez `+` ou `/debug`, le compilateur générera des informations de débogage et les placera dans un fichier .pdb.  Spécifier `-` équivaut à ne pas spécifier `/debug`.|  
|`full`  &#124; `pdbonly`|Facultatif.  Spécifie le type d'informations de débogage générées par le compilateur.  Si vous ne spécifiez pas `/debug:pdbonly`, la valeur par défaut est `full`, ce qui vous permet d'attacher un débogueur au programme en cours d'exécution.  L'argument `pdbonly` permet un débogage du code source lorsque le programme est démarré dans le débogueur, mais affiche du code en langage assembleur uniquement lorsque le programme en cours d'exécution est attaché au débogueur.|  
  
## Notes  
 Utilisez cette option pour créer des générations de débogage.  Si vous ne spécifiez pas `/debug`, `/debug+` ou `/debug:full`, vous ne pourrez pas déboguer le fichier de sortie de votre programme.  
  
 Par défaut, les informations de débogage ne sont pas émises \(`/debug-`\).  Pour émettre des informations de débogage, spécifiez `/debug` ou `/debug+`.  
  
 Pour plus d'informations sur la configuration des performances de débogage d'une application, consultez [Simplification du débogage d'une image](../Topic/Making%20an%20Image%20Easier%20to%20Debug.md).  
  
||  
|-|  
|Pour définir \/debug dans l'environnement de développement intégré Visual Studio|  
|1.  Un projet étant sélectionné dans l'**Explorateur de solutions**, cliquez dans le menu **Projet** sur **Propriétés**.  Pour plus d'informations, consultez [Introduction to the Project Designer](http://msdn.microsoft.com/fr-fr/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Cliquez sur l'onglet **Compiler**.<br />3.  Cliquez sur **Options avancées de compilation**.<br />4.  Modifiez la valeur dans la zone **Générer des infos de débogage**.|  
  
## Exemple  
 L'exemple suivant place des informations de débogage dans le fichier de sortie `App.exe`.  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [\/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)   
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)