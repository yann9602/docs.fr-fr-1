---
title: "How to: Set Environment Variables for the Visual Studio Command Line | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "cs.build.commandline"
dev_langs: 
  - "CSharp"
  - "CSharp"
helpviewer_keywords: 
  - "csc.exe, command-line builds"
  - "Visual C#, command-line builds"
  - "command-line compilers, Visual C#"
  - "Vsvars32.bat"
  - "builds [C#], command-line"
  - "compilers, invoking from command line"
  - "Vcvars32.bat file"
  - "command line [C#], building from"
  - "Visual C# compiler, enabling"
  - "compiling source code, from command line"
ms.assetid: 7ec09480-5612-4f6a-8d00-ad90ea9bca5d
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# How to: Set Environment Variables for the Visual Studio Command Line
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Le fichier vsvars32.bat définit les variables d'environnement appropriées pour permettre des générations à partir de la ligne de commande.  Pour plus d'informations sur vsvars32.bat, consultez l'[article Q248802 de la Base de connaissances](http://go.microsoft.com/fwlink/?LinkId=225042).  
  
 Si la version actuelle de Visual Studio est installée sur un ordinateur qui possède également une version antérieure de Visual Studio, vous ne devez pas exécuter vcvarsall.bat ni vcvars32.bat à partir de différentes versions dans la même fenêtre d'invite de commandes.  
  
### Pour exécuter VSVARS32.BAT  
  
1.  Dans le menu **Démarrer**, ouvrez l'**Invite de commandes développeur pour VS2012**.  
  
2.  Accédez au sous\-répertoire Program Files\\Microsoft Visual Studio *version*\\Common7\\Tools ou Program Files \(x86\)\\Microsoft Visual Studio *version*\\Common7\\Tools de votre installation.  
  
3.  Exécutez VSVARS32.bat en tapant VSVARS32.  
  
    > [!CAUTION]
    >  VSVARS32.bat peut varier d'un ordinateur à l'autre.  Ne remplacez pas un fichier VSVARS32.bat manquant ou endommagé par un fichier VSVARS32.bat d'un autre ordinateur.  À la place, réexécutez le programme d'installation pour remplacer le fichier manquant.  
  
## Voir aussi  
 [Command\-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)