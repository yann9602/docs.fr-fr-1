---
title: "How to: Delete a File in Visual Basic | Microsoft Docs"
ms.custom: ""
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
  - "Delete method"
  - "files, deleting"
  - "files, manipulating"
  - "File object"
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# How to: Delete a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La méthode `DeleteFile` de l'objet `My.Computer.FileSystem` vous permet de supprimer un fichier.  Elle offre entre autres les options suivantes : envoyer ou non le fichier supprimé à la **Corbeille**, demander ou non à l'utilisateur de confirmer que le fichier doit être supprimé et ce qu'il faut faire lorsque l'utilisateur annule l'opération.  
  
### Pour supprimer un fichier texte  
  
-   Utilisez la méthode `DeleteFile` pour supprimer le fichier.  Le code suivant illustre comment supprimer le fichier nommé `test.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-delete-a-file_1.vb)]  
  
### Pour supprimer un fichier texte et demander à l'utilisateur de confirmer que le fichier doit être supprimé  
  
-   Utilisez la méthode `DeleteFile` pour supprimer le fichier, en affectant `showUI` à `AllDialogs`.  Le code suivant illustre comment supprimer le fichier nommé `test.txt` et permettre à l'utilisateur de confirmer que le fichier doit être supprimé.  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-delete-a-file_2.vb)]  
  
### Pour supprimer un fichier texte et l'envoyer à la Corbeille  
  
-   Utilisez la méthode `DeleteFile` pour supprimer le fichier, en spécifiant `SendToRecycleBin` pour le paramètre `recycle`.  Le code suivant illustre comment supprimer le fichier nommé `test.txt` et l'envoyer à la **Corbeille**.  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-delete-a-file_3.vb)]  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le chemin d'accès n'est pas valide pour l'une des raisons suivantes : il correspond à une chaîne de longueur nulle, ne contient que des espaces blancs, comporte des caractères non valides ou représente un chemin d'accès de périphérique \(commençant par \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de dossier du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   Le fichier est en cours d'utilisation \(<xref:System.IO.IOException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
-   Le fichier n'existe pas \(<xref:System.IO.FileNotFoundException>\).  
  
-   L'utilisateur n'a pas l'autorisation nécessaire pour supprimer le fichier, ou le fichier est en lecture seule \(<xref:System.UnauthorizedAccessException>\).  
  
-   Il existe une situation de niveau de confiance partiel où l'utilisateur n'a pas les autorisations suffisantes \(<xref:System.Security.SecurityException>\).  
  
-   L'utilisateur a annulé l'opération et `onUserCancel` a la valeur `ThrowException` \(<xref:System.OperationCanceledException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.UIOption>   
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)