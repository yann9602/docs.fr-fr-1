---
title: Exemples de lignes de commande de compilation (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- command line [Visual Basic], compilers
- compilation [Visual Basic], command-line
- command-line compilers
- compiling source code [Visual Basic], from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e168d40a22ca3737bee18f966df95988a2736a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="sample-compilation-command-lines-visual-basic"></a>Exemples de lignes de commande de compilation (Visual Basic)
En guise d’alternative à la compilation [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] programmes depuis [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], vous pouvez les compiler depuis la ligne de commande pour produire des fichiers exécutables (.exe) ou des fichiers de bibliothèque de liens dynamiques (.dll).  
  
 Le [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compilateur de ligne de commande prend en charge un jeu complet d’options qui contrôlent les fichiers d’entrée et de sortie, assemblys et de débogage et du préprocesseur. Chaque option est disponible sous deux formes interchangeables : `-``option` et `/``option`. Cette documentation ne décrit que le `/``option` formulaire.  
  
 Le tableau suivant répertorie certains exemples de lignes de commande que vous pouvez modifier pour votre usage personnel.  
  
|Pour|Utilisez|  
|--------|---------|  
|Compilez le fichier.vb et créer File.exe|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|Compilez le fichier.vb et créer File.dll|`vbc /target:library File.vb`|  
|Compilez le fichier.vb et créer My.exe|`vbc /out:My.exe File.vb`|  
|Compiler tous les [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sur les fichiers dans le répertoire actif, avec les optimisations et les `DEBUG` symbole défini, afin de produire File2.exe|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|Compilez tous les [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fichiers dans le répertoire actif, produisant une version debug de File2.dll sans afficher le logo ou les avertissements|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|Compilez tous les [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fichiers dans le répertoire en cours en Something.dll|`vbc /target:library /out:Something.dll *.vb`|  
  
 Lors de la compilation à partir de la ligne de commande, vous devez explicitement référencer le Microsoft [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] bibliothèque d’exécution via le `/reference` option du compilateur.  
  
> [!TIP]
>  Lorsque vous générez un projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher les informations associé **vbc** commande avec les options du compilateur dans la fenêtre Sortie. Pour afficher ces informations, ouvrez le [boîte de dialogue Options, projets et Solutions, générer et exécuter](/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez le **détail de sortie de génération du projet MSBuild** à **Normal** ou augmenter le niveau de détail. Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
