---
title: "How to: Invoke the Command-Line Compiler (Visual Basic) | Microsoft Docs"
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
  - "command-line arguments"
  - "vbc.exe"
  - "Visual Basic compiler, starting"
  - "command line, arguments"
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 28
---
# How to: Invoke the Command-Line Compiler (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez appeler le compilateur de ligne de commande en tapant le nom de son fichier exécutable sur la ligne de commande, également appelée invite de commande MS\-DOS.  Si vous compilez à partir de l'invite de commande Windows par défaut, vous devez entrer le chemin qualifié complet dans le fichier exécutable.  Pour remplacer ce comportement par défaut, vous pouvez utiliser l'invite de commande [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] ou modifier la variable d'environnement PATH.  Ces deux méthodes vous permettent d'effectuer une compilation à partir d'un répertoire en entrant simplement le nom du compilateur.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour appeler le compilateur à l'aide de l'invite de commande Visual Studio  
  
1.  Ouvrez le dossier de programme Visual Studio Tools dans le groupe de programmes Microsoft Visual Studio.  
  
2.  Vous pouvez utiliser l'invite de commandes de [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] pour accéder au compilateur à partir de n'importe quel répertoire sur votre ordinateur, si Visual Studio est installé.  
  
3.  Appelez l'invite de commande [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)].  
  
4.  Au niveau de la ligne de commande, tapez le `vbc.exe` *sourceFileName*, puis appuyez sur Entrée.  
  
     Par exemple, si vous avez stocké votre code source dans un répertoire appelé `SourceFiles`, vous devriez ouvrir l'invite de commande et entrer `cd SourceFiles` pour le remplacer par ce répertoire.  Si le répertoire contenait un fichier source nommé `Source.vb`, vous pouvez le compiler en tapant `vbc.exe Source.vb`.  
  
### Pour affecter le compilateur à la variable d'environnement PATH pour l'invite de commande Windows  
  
1.  Utilisez la fonction de recherche de Windows pour rechercher Vbc.exe sur votre disque local.  
  
     Le nom exact du répertoire où se trouve le compilateur dépend de l'emplacement du répertoire Windows et de la version de [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] installée sur l'ordinateur.  Si plusieurs versions du [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact-md.md)] sont installées sur votre ordinateur, vous devez déterminer celle qui doit être utilisée \(en général, il s'agit de la plus récente\).  
  
2.  Dans le menu **Démarrer** de votre ordinateur, cliquez avec le bouton droit sur **Poste de travail**, puis cliquez sur **Propriétés** dans le menu contextuel.  
  
3.  Cliquez sur l'onglet **Avancé**, puis sur **Variables d'environnement**.  
  
4.  Dans le volet **Variables système**, sélectionnez **Chemin d'accès** dans la liste et cliquez sur **Modifier**.  
  
5.  Dans la boîte de dialogue **Modifier la variable système**, déplacez le point d'insertion à la fin de la chaîne figurant dans le champ **Valeur de la variable** et tapez un point\-virgule \(;\) suivi du nom complet du répertoire que vous avez trouvé à l'étape 1.  
  
6.  Cliquez sur **OK** pour confirmer vos modifications et fermez les boîtes de dialogue.  
  
     Après avoir modifié la variable d'environnement PATH, vous pouvez exécuter le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] à l'invite de commande Windows à partir de n'importe quel répertoire sur l'ordinateur.  
  
### Pour appeler le compilateur à l'aide de l'invite de commande Windows  
  
1.  Dans le menu **Démarrer**, cliquez sur le dossier **Accessoires**, puis ouvrez **Invite de commande Windows**.  
  
2.  Au niveau de la ligne de commande, tapez `vbc.exe` *sourceFileName*, puis appuyez sur Entrée.  
  
     Par exemple, si vous avez stocké votre code source dans un répertoire appelé `SourceFiles`, vous devriez ouvrir l'invite de commande et entrer `cd SourceFiles` pour le remplacer par ce répertoire.  Si le répertoire contenait un fichier source nommé `Source.vb`, vous pouvez le compiler en tapant `vbc.exe Source.vb`.  
  
## Voir aussi  
 [Visual Basic Command\-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Conditional Compilation](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)