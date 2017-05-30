---
title: "Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.build.commandline
dev_langs:
- CSharp
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
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a780a11d8dd238187eb82933359bbb151bb3c333
ms.openlocfilehash: e2cc644bb3b2c51615fe763224505b07e113ad62
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-set-environment-variables-for-the-visual-studio-command-line"></a>Guide pratique pour définir des variables d’environnement pour la ligne de commande Visual Studio
Le fichier vsvars32.bat définit les variables d'environnement appropriées pour permettre des générations à partir de la ligne de commande. Pour plus d’informations sur vsvars32.bat, consultez l’[article Q248802 de la Base de connaissances](http://go.microsoft.com/fwlink/?LinkId=225042).  
  
 Si la version actuelle de Visual Studio est installée sur un ordinateur qui possède également une version antérieure de Visual Studio, vous ne devez pas exécuter vcvarsall.bat ni vcvars32.bat à partir de différentes versions dans la même fenêtre d'invite de commandes.  
  
### <a name="to-run-vsvars32bat"></a>Pour exécuter VSVARS32.BAT  
  
1.  Dans le menu **Démarrer**, ouvrez l’**Invite de commandes développeur pour VS2012**.  
  
2.  Accédez au sous-répertoire Program Files\Microsoft Visual Studio *version*\Common7\Tools ou Program Files (x86)\Microsoft Visual Studio *version*\Common7\Tools de votre installation.  
  
3.  Exécutez VSVARS32.bat en tapant **VSVARS32**.  
  
    > [!CAUTION]
    >  VSVARS32.bat peut varier d'un ordinateur à l'autre. Ne remplacez pas un fichier VSVARS32.bat manquant ou endommagé par un fichier VSVARS32.bat d'un autre ordinateur. À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération à partir de la ligne de commande avec csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
