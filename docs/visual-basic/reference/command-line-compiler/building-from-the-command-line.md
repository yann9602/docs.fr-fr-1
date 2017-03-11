---
title: "G&#233;n&#233;ration &#224; partir de la ligne de commande (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "builds [Visual Basic], ligne de commande"
  - "compilateur Visual Basic, à propos du compilateur Visual Basic"
  - "ligne de commande [Visual Basic], compilateurs"
  - "ligne de commande [Visual Basic], génération à partir de"
  - "ligne de commande [Visual Basic], builds"
  - "compilateurs, appeler à partir de la ligne de commande"
  - "générations à partir de la ligne de commande"
  - "compiler le code source"
  - "compilateurs de ligne de commande, Visual Basic"
  - "ligne de commande [Visual Basic], Visual Basic"
ms.assetid: e61947e9-a42e-4717-a699-5f70a98cdd03
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# G&#233;n&#233;ration &#224; partir de la ligne de commande (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Un projet [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] est composé d'un ou plusieurs fichiers source séparés.  Durant le processus de compilation, ces fichiers sont rassemblés sous forme de package \(fichier exécutable unique permettant d'exécuter une application\).  
  
 Le compilateur de ligne de commande [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] fournit une alternative aux programmes de compilation dans l'environnement de développement intégré \(IDE\) de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].  Le compilateur de ligne de commande est prévu pour les situations où vous n'avez pas besoin de l'ensemble des fonctionnalités IDE; par exemple, lorsque vous utilisez ou écrivez du code pour des ordinateurs dont la mémoire système ou l'espace de stockage est limité.  
  
 Lorsque la compilation est effectuée à partir de la ligne de commande, vous devez faire référence de manière explicite à la bibliothèque Runtime Microsoft [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] par l'intermédiaire de l'option du compilateur `/reference`.  
  
 Pour compiler des fichiers sources à partir de l'IDE de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)], cliquez dans le menu **Générer** sur la commande **Générer**.  
  
> [!TIP]
>  Lorsque vous générez des fichiers projet à l'aide de l'IDE de Visual Studio, vous pouvez afficher des informations sur la commande associée d' **vbc** et ses commutateurs dans la fenêtre Sortie.  Pour afficher ces informations, ouvrez [Options \(boîte de dialogue\), Projets et solutions, Générer et exécuter](/visual-studio/ide/reference/options-dialog-box-projects-and-solutions-build-and-run), puis affectez **Commentaires de sortie de génération du projet MSBuild** à **Normal** ou un niveau supérieur de commentaires.  Pour plus d'informations, consultez [Comment : afficher, enregistrer et configurer des fichiers journaux de génération](../Topic/How%20to:%20View,%20Save,%20and%20Configure%20Build%20Log%20Files.md).  
  
 Vous pouvez compiler les fichiers du projet \(.vbproj\) à une invite de commandes à l'aide de MSBuild.  Pour plus d'informations, consultez [Command\-Line Reference](/visual-studio/msbuild/msbuild-command-line-reference) et [Walkthrough: Using MSBuild](../Topic/Walkthrough:%20Using%20MSBuild.md).  
  
## Dans cette section  
 [How to: Invoke the Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/how-to-invoke-the-command-line-compiler.md)  
 Explique comment appeler le compilateur de ligne de commande à l'invite de commande MS\-DOS ou à partir d'un sous\-répertoire spécifique.  
  
 [Exemples de lignes de commande de compilation](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 Fournit une liste d'exemples de lignes de commande que vous pouvez modifier pour vos besoins.  
  
## Rubriques connexes  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)  
 Fournit les listes d'options du compilateur, organisées de manière alphabétique ou selon les besoins.  
  
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)  
 Explique comment compiler des sections de code précises.  
  
 [Génération et nettoyage de solutions et de projets dans Visual Studio](/visual-studio/ide/building-and-cleaning-projects-and-solutions-in-visual-studio)  
 Explique comment organiser le contenu inclus dans les différentes générations, choisir les propriétés de projet et vérifier que les projets sont générés dans l'ordre approprié.