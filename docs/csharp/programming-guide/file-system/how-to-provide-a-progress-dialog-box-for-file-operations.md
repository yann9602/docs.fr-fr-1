---
title: "Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- progress dialog [C#]
ms.assetid: 01b71fe7-8178-4dc8-aeb1-12053be7b51c
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 41da88526813e86748060bad844f13d1bf01e11f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#)
Vous pouvez fournir une boîte de dialogue standard qui affiche la progression sur des opérations de fichiers dans Windows si vous utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> dans l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=fullName>.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-add-a-reference-in-visual-studio"></a>Pour ajouter une référence dans Visual Studio  
  
1.  Dans la barre de menus, choisissez **Projet**, **Ajouter une référence**.  
  
     La boîte de dialogue **Gestionnaire de références** s’affiche.  
  
2.  Dans la zone **Assemblys**, choisissez **Framework** si ce n’est pas sélectionné.  
  
3.  Dans la liste des noms, cochez la case **Microsoft.VisualBasic**, puis choisissez le bouton **OK** pour fermer la boîte de dialogue.  
  
## <a name="example"></a>Exemple  
 Le code suivant copie le répertoire spécifié par `sourcePath` dans le répertoire spécifié par `destinationPath`. Ce code fournit également une boîte de dialogue standard qui affiche une estimation du temps restant avant la fin de l’opération.  
  
 [!code-cs[csFilesandFolders#11](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-provide-a-progress-dialog-box-for-file-operations_1.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)
