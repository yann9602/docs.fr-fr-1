---
title: "How to: Create a Copy of a File in a Different Directory in Visual Basic | Microsoft Docs"
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
  - "My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]"
  - "files, copying"
  - "CopyFile method, copying files in Visual Basic"
  - "I/O [Visual Basic], copying files"
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Copy of a File in a Different Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

La méthode `My.Computer.FileSystem.CopyFile` vous permet de copier des fichiers.  Ses paramètres permettent de remplacer les fichiers existants, de renommer le fichier, d'afficher la progression de l'opération et d'autoriser l'utilisateur à annuler l'opération.  
  
### Pour copier un fichier texte dans un autre dossier  
  
-   Utilisez la méthode `CopyFile` pour copier un fichier en spécifiant un fichier source et le répertoire cible.  Le paramètre `overwrite` vous permet de spécifier s'il faut ou non remplacer les fichiers existants.  Les exemples de code suivants montrent comment utiliser `CopyFile`.  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
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
 [How to: Create a Copy of a File in the Same Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [How to: Copy a Directory to Another Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [How to: Rename a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)