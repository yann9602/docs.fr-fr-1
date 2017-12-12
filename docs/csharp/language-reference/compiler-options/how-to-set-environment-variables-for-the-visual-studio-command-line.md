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
ms.openlocfilehash: afab503719f67cf7ad1762370ed3062e12ad88e9
ms.sourcegitcommit: 401c4427a3ec0d1263543033b3084039278509dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio

Le fichier VsDevCmd.bat définit les variables d’environnement appropriées pour les générations à partir de la ligne de commande. Pour plus d’informations sur VsDevCmd.bat, consultez [l’article Q248802 de la Base de connaissances](https://support.microsoft.com/help/248802/you-receive-the-out-of-environment-space-error-message-when-you-execut).  

> [!NOTE]
> Le fichier VsDevCmd.bat est un nouveau fichier fourni avec Visual Studio 2017. Visual Studio 2015 et versions antérieures utilisaient VSVARS32.bat dans le même but. Ce fichier était stocké dans \Program Files\Microsoft Visual Studio\\*Version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio\\*Version*\Common7\Tools.
  
Si la version actuelle de Visual Studio est installée sur un ordinateur qui exécute également une version antérieure de Visual Studio, vous ne devez pas exécuter VsDevCmd.bat et VSVARS32.BAT à partir de différentes versions dans la même fenêtre d’invite de commandes. Exécutez plutôt la commande pour chaque version dans sa propre fenêtre.
  
### <a name="to-run-vsdevcmdbat"></a>Pour exécuter VsDevCmd.BAT  
  
1.  Dans le menu **Démarrer**, ouvrez **l’invite de commandes développeur pour VS2017**.  Elle se trouve dans le dossier **Visual Studio 2017**.
  
2.  Accédez au sous-répertoire \Program Files\Microsoft Visual Studio\\*Version*\\*Offre*\Common7\Tools ou \Program Files (x86)\Microsoft Visual Studio\\*Version*\\*Offre*\Common7\Tools de votre installation.  (*Version* correspond à *2017* pour la version actuelle. *Offre* correspond à *Enterprise*, *Professional* ou *Community*.)
  
3.  Exécutez VsDevCmd.bat en tapant **VsDevCmd**.  
  
    > [!CAUTION]
    >  VsDevCmd.bat peut varier d’un ordinateur à l’autre. Ne remplacez pas un fichier VsDevCmd.bat manquant ou endommagé par un fichier VsDevCmd.bat d’un autre ordinateur. À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération à partir de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
