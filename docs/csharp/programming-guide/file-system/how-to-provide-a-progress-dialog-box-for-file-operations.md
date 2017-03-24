---
title: "Comment&#160;: fournir une bo&#238;te de dialogue de progression pour les op&#233;rations sur les fichiers (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "boîte de dialogue d'avancement (C#)"
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# Comment&#160;: fournir une bo&#238;te de dialogue de progression pour les op&#233;rations sur les fichiers (Guide de programmation&#160;C#)
Vous pouvez fournir une boîte de dialogue standard qui indique la progression des opérations de fichiers dans Windows si vous utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> dans l'espace de noms <xref:Microsoft.VisualBasic?displayProperty=fullName>.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour ajouter une référence dans Visual Studio  
  
1.  Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.  
  
     La boîte de dialogue **Gestionnaire de références** s'affiche.  
  
2.  Dans la zone **Assemblies**, choisissez **Framework** si cette option n'est pas déjà sélectionnée.  
  
3.  Dans la liste des noms, activez la case à cocher **Microsoft.VisualBasic**, puis choisissez le bouton **OK** pour fermer la boîte de dialogue.  
  
## Exemple  
 Le code suivant copie le répertoire spécifié par `sourcePath` dans celui spécifié par `destinationPath`.  Ce code fournit également une boîte de dialogue standard qui affiche la quantité de temps estimée restante avant la fin de l'opération.  
  
 [!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## Voir aussi  
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)