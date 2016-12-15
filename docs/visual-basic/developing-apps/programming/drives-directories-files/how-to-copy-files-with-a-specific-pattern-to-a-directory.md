---
title: "Comment&#160;: copier des fichiers avec un mod&#232;le sp&#233;cifique dans un r&#233;pertoire dans Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Computer.FileSystem.CopyFile (méthode), copie de fichiers (Visual Basic)"
  - "fichiers, copie"
  - "CopyFile (méthode), copie de fichiers dans Visual Basic"
  - "E/S (Visual Basic), copie de fichiers"
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Comment&#160;: copier des fichiers avec un mod&#232;le sp&#233;cifique dans un r&#233;pertoire dans Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retourne une collection en lecture seule de chaînes représentant les noms de chemin des fichiers. Vous pouvez utiliser le paramètre `wildCards` pour indiquer un modèle spécifique.  
  
 Une collection vide est retournée si aucun fichier correspondant n’est trouvé.  
  
 Vous pouvez utiliser la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> pour copier les fichiers dans un répertoire.  
  
### Pour copier des fichiers avec un modèle spécifique dans un répertoire  
  
1.  Utilisez la méthode `GetFiles` pour retourner la liste des fichiers. Cet exemple retourne tous les fichiers .rtf qui se trouvent dans le répertoire spécifié.  
  
     [!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]  
  
2.  Utilisez la méthode `CopyFile` pour copier les fichiers. Cet exemple copie les fichiers dans le répertoire nommé `testdirectory`.  
  
     [!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]  
  
3.  Terminez l’instruction `For` par une instruction `Next`.  
  
     [!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]  
  
## Exemple  
 L’exemple suivant, qui présente les extraits de code ci\-dessus dans leur intégralité, copie tous les fichiers .rtf du répertoire spécifié dans le répertoire nommé `testdirectory`.  
  
 [!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]  
  
## Sécurité .NET Framework  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il contient uniquement des espaces blancs, il contient des caractères non valides ou c’est un chemin d’appareil \(commençant par \\\\.\\\) \(<xref:System.ArgumentException>\).  
  
-   Le chemin n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   Le répertoire n’existe pas \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   Le répertoire pointe vers un fichier existant \(<xref:System.IO.IOException>\).  
  
-   Le chemin dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de répertoire du chemin contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin \(<xref:System.Security.SecurityException>\). L'utilisateur ne dispose pas des autorisations nécessaires \(<xref:System.UnauthorizedAccessException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>   
 [How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)