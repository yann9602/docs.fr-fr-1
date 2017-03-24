---
title: "How to: Rename a File in Visual Basic | Microsoft Docs"
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
  - "I/O [Visual Basic], renaming files"
  - "files, renaming"
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: 21
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 21
---
# How to: Rename a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Utilisez la méthode `RenameFile` de l'objet `My.Computer.FileSystem` pour renommer un fichier en fournissant l'emplacement actuel, le nom de fichier et le nouveau nom de fichier.  Cette méthode ne peut pas être utilisée pour déplacer un fichier ; utilisez plutôt la méthode `MoveFile` pour déplacer et renommer le fichier.  
  
### Pour renommer un fichier  
  
-   Utilisez la méthode `My.Computer.FileSystem.RenameFile` pour renommer un fichier.  Cet exemple renomme le fichier `Test.txt` dans `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 Cet exemple de code est également disponible sous forme d'extrait de code IntelliSense.  Dans le sélecteur d'extrait de code, l'extrait est localisé dans **Système de fichiers \- Traitement de lecteurs, de dossiers et de fichiers**.  Pour plus d'informations, consultez [Extraits de code](/visual-studio/ide/code-snippets).  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le chemin d'accès n'est pas valide pour l'une des raisons suivantes : il correspond à une chaîne de longueur nulle, ne contient que des espaces blancs, comporte des caractères non valides ou représente un chemin d'accès de périphérique \(commençant par \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   `newName` contient des informations relatives au chemin d'accès \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `newName` a la valeur `Nothing` ou est une chaîne vide \(<xref:System.ArgumentNullException>\).  
  
-   Le fichier source n'est pas valide ou n'existe pas \(<xref:System.IO.FileNotFoundException>\).  
  
-   Un fichier ou répertoire existe avec le nom spécifié dans `newName` \(<xref:System.IO.IOException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
-   L'utilisateur n'a pas l'autorisation requise \(<xref:System.UnauthorizedAccessException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>   
 [Comment : déplacer un fichier](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)   
 [Creating, Deleting, and Moving Files and Directories](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)   
 [How to: Create a Copy of a File in the Same Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)