---
title: Exemples de lignes de commande de Compilation (Visual Basic) | Documents Microsoft
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
- command line, compilers
- compilation, command-line
- command-line compilers
- compiling source code, from command line
- Visual Basic compiler, sample command lines
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 918787b3377f2e5a636a6b098046ac2f455efcdd
ms.lasthandoff: 03/13/2017

---
# <a name="sample-compilation-command-lines-visual-basic"></a>Exemples de lignes de commande de compilation (Visual Basic)
Comme alternative à la compilation de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] programmes depuis [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], vous pouvez les compiler depuis la ligne de commande pour produire des fichiers exécutables (.exe) ou des fichiers de bibliothèque de liens dynamiques (.dll).  
  
 Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur de ligne de commande prend en charge un ensemble complet d’options qui contrôlent les fichiers d’entrée et de sortie, assemblys et de débogage et les options de préprocesseur. Chaque option est disponible sous deux formes interchangeables : `-``option` et `/``option`. Cette documentation ne décrit que le `/``option` formulaire.  
  
 Le tableau suivant répertorie certains exemples de ligne de commande que vous pouvez modifier pour votre usage personnel.  
  
|Pour|Utilisez|  
|--------|---------|  
|Compiler File.vb et créer File.exe|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|Compiler File.vb et créer File.dll|`vbc /target:library File.vb`|  
|Compiler File.vb et créer My.exe|`vbc /out:My.exe File.vb`|  
|Compilez tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] sur les fichiers dans le répertoire actif, avec les optimisations et `DEBUG` symbole est défini, afin de produire File2.exe|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|Compilez tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] les fichiers dans le répertoire en cours, en produisant une version debug de File2.dll sans afficher le logo ou les avertissements|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|Compilez tous les [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] fichiers dans le répertoire en cours en Something.dll|`vbc /target:library /out:Something.dll *.vb`|  
  
 Lors de la compilation à partir de la ligne de commande, vous devez explicitement référencer Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] bibliothèque d’exécution via la `/reference` option du compilateur.  
  
> [!TIP]
>  Lorsque vous générez un projet à l’aide de l’IDE de Visual Studio, vous pouvez afficher des informations sur les **vbc** commande avec les options du compilateur dans la fenêtre Sortie. Pour afficher ces informations, ouvrez le [boîte de dialogue Options, projets et Solutions, générer et exécuter](https://docs.microsoft.com/visualstudio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis définissez la **niveau de détail de sortie de génération du projet MSBuild** à **Normal** ou un niveau supérieur de détail. Pour plus d’informations, consultez l’article [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](http://msdn.microsoft.com/library/75d38b76-26d6-4f43-bbe7-cbacd7cc81e7).  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
