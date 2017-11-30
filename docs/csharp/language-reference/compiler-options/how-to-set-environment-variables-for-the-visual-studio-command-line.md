---
title: "Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio"
ms.date: 09-29-2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: cs.build.commandline
helpviewer_keywords:
- csc.exe, command-line builds
- Visual C#, command-line builds
- command-line compilers, Visual C#
- Vsvars32.bat
- builds [C#], command-line
- compilers, invoking from command line
- Vcvars32.bat file
- command line [C#], building from
- Visual C# compiler, enabling
- compiling source code, from command line
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8012e310bb04ec3acef0790f9cd50ed42dd9286a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio

Le fichier VsDevCmd.bat définit les variables d’environnement appropriées pour permettre des générations en ligne de commande. Pour plus d’informations sur VsDevCmd.bat, consultez [l’article Q248802 de la Base de connaissances](http://go.microsoft.com/fwlink/?LinkId=225042).  

> [!NOTE]
> Le fichier VsDevCmd.bat est un nouveau fichier fourni avec Visual Studio 2017. Visual Studio 2015 et versions antérieures utilisé VSVARS32.bat dans le même but. Ce fichier a été stocké dans Visual Studio de \Program Files\Microsoft\\*Version*\Common7\Tools ou Program Files (x86) \Microsoft Visual Studio\\*Version*\Common7\Tools.
  
Si la version actuelle de Visual Studio est installée sur un ordinateur qui possède également une version antérieure de Visual Studio, vous ne devez pas exécuter VsDevCmd.bat et VSVARS32. BAT à partir de versions différentes dans la même fenêtre d’invite de commandes. Au lieu de cela, vous devez exécuter la commande pour chaque version dans sa propre fenêtre.
  
### <a name="to-run-vsdevcmdbat"></a>Pour exécuter VsDevCmd.BAT  
  
1.  À partir de la **Démarrer** menu, ouvrir le **invite de commandes développeur pour VS 2017**.  Il se trouve dans le **Visual Studio 2017** dossier.
  
2.  Modifier à Visual Studio \Program Files\Microsoft\\*Version*\\*offre*\Common7\Tools ou \Program fichiers (x86) \Microsoft Visual Studio\\ *Version*\\*offre*sous-répertoire \Common7\Tools de votre installation.  (*Version* est *2017* pour la version actuelle. *Offre* est un des *Enterprise*, *Professionnel* ou *Communauté*.)
  
3.  Exécutez VsDevCmd.bat en tapant **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat peut varier d’un ordinateur à l’autre. Ne remplacez pas un fichier VsDevCmd.bat manquant ou endommagé avec un VsDevCmd.bat à partir d’un autre ordinateur. À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération à partir de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
