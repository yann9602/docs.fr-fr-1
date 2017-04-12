---
title: "Comment : appeler le compilateur de ligne de commande (Visual Basic) | Documents Microsoft"
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
- command-line arguments
- vbc.exe
- Visual Basic compiler, starting
- command line, arguments
ms.assetid: 0fd9a8f6-f34e-4c35-a49d-9b9bbd8da4a9
caps.latest.revision: 28
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 69c95289f91f712bd3fda03a7f582d879141591a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-invoke-the-command-line-compiler-visual-basic"></a>Comment : appeler le compilateur de ligne de commande (Visual Basic)
Vous pouvez appeler le compilateur de ligne de commande en tapant le nom de son fichier exécutable dans la ligne de commande, également appelée invite de commande MS-DOS. Si vous compilez à partir de l’invite de commandes Windows par défaut, vous devez taper le chemin d’accès complet au fichier exécutable. Pour remplacer ce comportement par défaut, vous pouvez utiliser la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] invite de commandes, ou modifier la variable d’environnement PATH. Les deux vous permettent de compiler à partir de n’importe quel répertoire en tapant simplement le nom du compilateur.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-invoke-the-compiler-using-the-visual-studio-command-prompt"></a>Pour appeler le compilateur à l’aide de l’invite de commandes Visual Studio  
  
1.  Ouvrez le dossier de programme Visual Studio Tools dans le groupe de programmes Microsoft Visual Studio.  
  
2.  Vous pouvez utiliser la [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] invite de commandes pour accéder au compilateur à partir de n’importe quel répertoire sur votre ordinateur, si Visual Studio est installé.  
  
3.  Appeler le [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] invite de commandes.  
  
4.  À la ligne de commande, tapez `vbc.exe` *sourceFileName* puis appuyez sur ENTRÉE.  
  
     Par exemple, si vous avez stocké votre code source dans un répertoire appelé `SourceFiles`, vous exécuteriez l’invite de commandes et le type `cd SourceFiles` pour accéder à ce répertoire. Si le répertoire contenait un fichier source nommé `Source.vb`, vous pouvez le compiler en tapant `vbc.exe Source.vb`.  
  
### <a name="to-set-the-path-environment-variable-to-the-compiler-for-the-windows-command-prompt"></a>Pour définir la variable d’environnement PATH pour le compilateur de l’invite de commandes Windows.  
  
1.  Utilisez la fonctionnalité de recherche de Windows pour rechercher Vbc.exe sur votre disque local.  
  
     Le nom exact du répertoire où se trouve le compilateur dépend de l’emplacement du répertoire Windows et la version de le [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] installé. Si vous avez plusieurs versions de la [!INCLUDE[Compact](../../../visual-basic/reference/command-line-compiler/includes/compact_md.md)] , vous devez déterminer la version à utiliser (en général, la dernière version).  
  
2.  À partir de votre **Démarrer** Menu, avec le bouton droit **poste de travail**, puis cliquez sur **propriétés** dans le menu contextuel.  
  
3.  Cliquez sur le **avancé** onglet, puis cliquez sur **Variables d’environnement**.  
  
4.  Dans le **System** volet variables, sélectionnez **chemin d’accès** à partir de la liste et cliquez sur **modifier**.  
  
5.  Dans le **système modifier** boîte de dialogue Variable déplacer le point d’insertion à la fin de la chaîne dans le **valeur de la Variable** champ et tapez un point-virgule ( ;) suivi du nom complet du répertoire trouvé à l’étape 1.  
  
6.  Cliquez sur **OK** pour confirmer vos modifications et fermer les boîtes de dialogue.  
  
     Après avoir modifié la variable d’environnement PATH, vous pouvez exécuter la [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur à l’invite de commande Windows à partir de n’importe quel répertoire sur l’ordinateur.  
  
### <a name="to-invoke-the-compiler-using-the-windows-command-prompt"></a>Pour appeler le compilateur à l’aide de l’invite de commandes Windows  
  
1.  À partir de la **Démarrer** menu, cliquez sur le **Accessoires** dossier, puis ouvrez le **invite de commandes Windows**.  
  
2.  À la ligne de commande, tapez `vbc.exe` *sourceFileName* puis appuyez sur ENTRÉE.  
  
     Par exemple, si vous avez stocké votre code source dans un répertoire appelé `SourceFiles`, vous exécuteriez l’invite de commandes et le type `cd SourceFiles` pour accéder à ce répertoire. Si le répertoire contenait un fichier source nommé `Source.vb`, vous pouvez le compiler en tapant `vbc.exe Source.vb`.  
  
## <a name="see-also"></a>Voir aussi  
 [Compilateur de ligne de commande de Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Compilation conditionnelle](../../../visual-basic/programming-guide/program-structure/conditional-compilation.md)
