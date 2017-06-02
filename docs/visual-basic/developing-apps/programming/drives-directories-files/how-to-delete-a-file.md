---
title: Guide pratique pour supprimer un fichier en Visual Basic | Microsoft Docs
ms.custom: 
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
- Delete method
- files, deleting
- files, manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f6cf3192d6983b6222815c5c77a3dfd0b3845650
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-delete-a-file-in-visual-basic"></a>Comment : supprimer un fichier dans Visual Basic
La méthode `DeleteFile` de l’objet `My.Computer.FileSystem` vous permet de supprimer un fichier. Elle offre entre autres les options suivantes : envoyer ou non le fichier supprimé à la **Corbeille**, demander ou non à l’utilisateur de confirmer que le fichier doit être supprimé et l’action à effectuer quand l’utilisateur annule l’opération.  
  
### <a name="to-delete-a-text-file"></a>Pour supprimer un fichier texte  
  
-   Utilisez la méthode `DeleteFile` pour supprimer le fichier. Le code suivant illustre comment supprimer le fichier nommé `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>Pour supprimer un fichier texte et demander à l’utilisateur de confirmer que le fichier doit être supprimé  
  
-   Utilisez la méthode `DeleteFile` pour supprimer le fichier en affectant `showUI` à `AllDialogs`. Le code suivant illustre comment supprimer le fichier nommé `test.txt` et permettre à l’utilisateur de confirmer que le fichier doit être supprimé.  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>Pour supprimer un fichier texte et l’envoyer à la Corbeille  
  
-   Utilisez la méthode `DeleteFile` pour supprimer le fichier en spécifiant `SendToRecycleBin` pour le paramètre `recycle`. Le code suivant illustre comment supprimer le fichier nommé `test.txt` et l’envoyer à la **Corbeille**.  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (commençant par \\\\.\\) (<xref:System.ArgumentException>).  
  
-   Le chemin n’est pas valide, car il est `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
-   Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou son format n’est pas valide (<xref:System.NotSupportedException>).  
  
-   Le fichier est en cours d’utilisation (<xref:System.IO.IOException>).  
  
-   L’utilisateur ne dispose pas des autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
-   Le fichier n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
-   L’utilisateur n’a pas l’autorisation nécessaire pour supprimer le fichier, ou le fichier est en lecture seule (<xref:System.UnauthorizedAccessException>).  
  
-   Il existe une situation de niveau de confiance partiel où l’utilisateur n’a pas les autorisations suffisantes (<xref:System.Security.SecurityException>).  
  
-   L’utilisateur a annulé l’opération et `onUserCancel` a la valeur `ThrowException` (<xref:System.OperationCanceledException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.UIOption>   
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>   
 [Guide pratique pour placer la collection de fichiers dans un répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
