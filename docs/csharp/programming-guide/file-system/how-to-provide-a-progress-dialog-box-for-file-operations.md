---
title: "Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#)"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a43fb764e6a1ba0a2f1ad1645624c9d8a55bc858
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-provide-a-progress-dialog-box-for-file-operations-c-programming-guide"></a>Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers (Guide de programmation C#)
Vous pouvez fournir une boîte de dialogue standard qui montre la progression des opérations sur les fichiers dans Windows si vous utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%28System.String%2CSystem.String%2CMicrosoft.VisualBasic.FileIO.UIOption%29> de l’espace de noms <xref:Microsoft.VisualBasic?displayProperty=fullName>.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
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

