---
title: "How to: Create a Copy of a File in the Same Directory in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "File.Copy"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]"
  - "files, copying"
  - "CopyFile method, copying files in Visual Basic"
  - "I/O [Visual Basic], copying files"
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# How to: Create a Copy of a File in the Same Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Utilisez la méthode `My.Computer.FileSystem.CopyFile` pour copier des fichiers.  Les paramètres vous permettent de remplacer des fichiers existants, de renommer le fichier, d'afficher la progression de l'opération et d'autoriser l'utilisateur à annuler l'opération.  
  
### Pour créer une copie d'un fichier dans le même dossier  
  
-   Utilisez la méthode `CopyFile` en fournissant le fichier cible et l'emplacement.  L'exemple suivant crée une copie de `test.txt` appelée `test2.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### Pour créer une copie d'un fichier dans le même dossier en remplaçant les fichiers existants  
  
-   Utilisez la méthode `CopyFile` en fournissant le fichier cible et l'emplacement et en affectant à `overwrite` la valeur `True`.  L'exemple suivant crée une copie de `test.txt` appelée `test2.txt` et remplace tous les fichiers existants par ce nom.  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent lever une exception :  
  
-   Le chemin d'accès n'est pas valide pour l'une des raisons suivantes : il correspond à une chaîne de longueur nulle, ne contient que des espaces blancs, comporte des caractères non valides ou représente un chemin d'accès de périphérique \(commençant par \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   Le système n'a pas pu récupérer le chemin d'accès absolu \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   Le fichier source n'est pas valide ou n'existe pas \(<xref:System.IO.FileNotFoundException>\).  
  
-   Le chemin d'accès combiné pointe sur un répertoire existant \(<xref:System.IO.IOException>\).  
  
-   Le fichier de destination existe et `overwrite` a la valeur `False` \(<xref:System.IO.IOException>\).  
  
-   L'utilisateur n'a pas les autorisations suffisantes pour accéder au fichier \(<xref:System.IO.IOException>\).  
  
-   Un fichier du dossier cible portant le même nom est en cours d'utilisation \(<xref:System.IO.IOException>\).  
  
-   Un nom de fichier ou de dossier du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   `ShowUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et l'utilisateur a annulé l'opération \(<xref:System.OperationCanceledException>\).  
  
-   `ShowUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et une erreur E\/S non spécifiée se produit \(<xref:System.OperationCanceledException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   L'utilisateur n'a pas l'autorisation requise \(<xref:System.UnauthorizedAccessException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [Comment : copier des fichiers avec un modèle spécifique dans un répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [How to: Copy a Directory to Another Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [How to: Rename a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)