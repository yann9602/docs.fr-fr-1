---
title: "Comment : fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0ac68b5aa6014db87b4f7a269ef73d0608371bd8
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/18/2017
---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Comment : fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#)
Vous pouvez fournir une boîte de dialogue standard qui montre la progression des opérations sur les fichiers dans Windows si vous utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> de l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=nameWithType>.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Pour ajouter une référence dans Visual Studio  
  
1.  Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.  
  
     La boîte de dialogue **Gestionnaire de références** s’affiche.  
  
2.  Dans la zone **Assemblys**, choisissez **Framework** si ce n’est pas sélectionné.  
  
3.  Dans la liste des noms, cochez la case **Microsoft.VisualBasic**, puis choisissez le bouton **OK** pour fermer la boîte de dialogue.  
  
## <a name="example"></a>Exemple  
 Le code suivant copie le répertoire spécifié par `sourcePath` dans le répertoire spécifié par `destinationPath`. Ce code fournit également une boîte de dialogue standard qui affiche une estimation du temps restant avant la fin de l’opération.  
  
 [!code-csharp[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)
