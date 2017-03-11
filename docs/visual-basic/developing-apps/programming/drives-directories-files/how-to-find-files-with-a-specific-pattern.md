---
title: "How to: Find Files with a Specific Pattern in Visual Basic | Microsoft Docs"
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
  - "files, finding"
  - "pattern matching"
  - "patterns, matching"
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# How to: Find Files with a Specific Pattern in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> retourne une collection en lecture seule de chaînes représentant les noms de chemin des fichiers.  Vous pouvez utiliser le paramètre `wildCards` pour spécifier un modèle spécifique.  Si vous souhaitez inclure des sous\-répertoires dans la recherche, affectez le paramètre `searchType` à `SearchOption.SearchAllSubDirectories`.  
  
 Une collection vide est retournée si aucun fichier correspondant au modèle spécifié n'est trouvé.  
  
> [!NOTE]
>  Pour plus d'informations sur retourner une liste des fichiers à l'aide de la classe d' `DirectoryInfo` de l'espace de noms d' `System.IO` , consultez l' <xref:System.IO.DirectoryInfo.GetFiles%2A>.  
  
### Pour rechercher des fichiers avec un modèle spécifié  
  
-   Utilisez la méthode `GetFiles` en fournissant le nom et le chemin d'accès du répertoire que vous souhaitez rechercher et en spécifiant le modèle.  L'exemple suivant retourne tous les fichiers avec l'extension `.dll` dans le répertoire et les ajoute à `ListBox1`.  
  
     [!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-find-files-with-a_1.vb)]  
  
## Sécurité .NET Framework  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le chemin d'accès n'est pas valide pour l'une des raisons suivantes : il correspond à une chaîne de longueur nulle, ne contient que des espaces blancs, comporte des caractères non valides ou représente un chemin d'accès de périphérique \(commençant par \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `directory` n'existe pas \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   `directory` pointe sur un fichier existant \(<xref:System.IO.IOException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de dossier du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires \(<xref:System.UnauthorizedAccessException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>   
 [How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)