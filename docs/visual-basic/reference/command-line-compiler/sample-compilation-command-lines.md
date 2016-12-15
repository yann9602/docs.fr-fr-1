---
title: "Exemples de lignes de commande de compilation (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "ligne de commande, compilateurs"
  - "compilation, ligne de commande"
  - "compilateurs de ligne de commande"
  - "compiler le code source, à partir de la ligne de commande"
  - "compilateur Visual Basic, exemples de lignes de commande"
ms.assetid: 5bfbb487-5f47-4267-969a-39dfb917beeb
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Exemples de lignes de commande de compilation (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Au lieu de compiler les programmes [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] à partir de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)], vous pouvez les compiler depuis la ligne de commande pour produire des fichiers exécutables \(.exe\) ou des fichiers de bibliothèques de liens dynamiques \(.dll\).  
  
 Le compilateur de ligne de commande [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] prend en charge un ensemble complet d'options permettant de contrôler les fichiers d'entrée et de sortie, les assemblys, ainsi que les options de débogage et du préprocesseur.  Chaque option est disponible sous deux formes interchangeables : `-``option` et `/``option`.  Cette documentation ne présente que la forme `/``option`.  
  
 Le tableau suivant répertorie certains exemples de lignes de commande que vous pouvez adapter à vos besoins.  
  
|Pour|Utilisation|  
|----------|-----------------|  
|Compiler File.vb et créer File.exe|`vbc /reference:Microsoft.VisualBasic.dll File.vb`|  
|Compiler File.vb et créer File.dll|`vbc /target:library File.vb`|  
|Compiler File.vb et créer My.exe|`vbc /out:My.exe File.vb`|  
|Compiler tous les fichiers [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] du répertoire en cours, en activant les optimisations et en définissant le symbole `DEBUG`, afin de produire File2.exe|`vbc /define:DEBUG=1 /optimize /out:File2.exe *.vb`|  
|Compiler tous les fichiers [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] du répertoire en cours, en produisant une version debug de File2.dll sans afficher le logo ou les avertissements|`vbc /target:library /out:File2.dll /nowarn /nologo /debug *.vb`|  
|Compiler tous les fichiers [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] du répertoire en cours en Something.dll|`vbc /target:library /out:Something.dll *.vb`|  
  
 Lorsque la compilation est effectuée à partir de la ligne de commande, vous devez faire référence de manière explicite à la bibliothèque Runtime Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] par l'intermédiaire de l'option du compilateur `/reference`.  
  
> [!TIP]
>  Lorsque vous générez un projet à l'aide de l'IDE de Visual Studio, vous pouvez afficher des informations sur la commande associée d' **vbc** avec ses options du compilateur dans la fenêtre Sortie.  Pour afficher ces informations, ouvrez [Options \(boîte de dialogue\), Projets et solutions, Générer et exécuter](/visual-studio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis affectez **Commentaires de sortie de génération du projet MSBuild** à **Normal** ou un niveau supérieur de commentaires.  Pour plus d'informations, consultez [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md).  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)