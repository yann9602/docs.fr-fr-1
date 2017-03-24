---
title: "How to: Get the Collection of Files in a Directory in Visual Basic | Microsoft Docs"
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
  - "folders, working with"
  - "files, accessing"
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# How to: Get the Collection of Files in a Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Les surcharges de la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> retournent une collection en lecture seule de chaînes représentant les noms des fichiers contenus dans un répertoire :  
  
-   Utilisez la surcharge <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> pour effectuer une recherche de fichier simple dans un répertoire spécifié, sans rechercher dans les sous\-répertoires.  
  
-   Utilisez la surcharge [GetFiles\(String, SearchOption, String\<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%2CMicrosoft.VisualBasic.FileIO.SearchOption%2CSystem.String%5B%5D%29> pour spécifier des options supplémentaires pour votre recherche.  Vous pouvez utiliser le paramètre `wildCards` pour spécifier un modèle de recherche.  Pour inclure des sous\-répertoires dans la recherche, affectez la valeur <xref:Microsoft.VisualBasic.FileIO.SearchOption?displayProperty=fullName> au paramètre `searchType`.  
  
 Une collection vide est retournée si aucun fichier correspondant au modèle spécifié n'est détecté.  
  
### Pour énumérer les fichiers contenus dans un répertoire  
  
-   Utilisez l'une des surcharges de méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName>, en fournissant le nom et le chemin d'accès au répertoire dans lequel effectuer la recherche dans le paramètre `directory`.  L'exemple suivant retourne tous les fichiers contenus dans le répertoire et les ajoute à  `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le chemin d'accès n'est pas valide pour l'une des raisons suivantes : il s'agit d'une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s'agit d'un chemin d'accès de périphérique \(commence par \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   `directory` n'existe pas \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   `directory` pointe vers un fichier existant \(<xref:System.IO.IOException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
-   L'utilisateur ne dispose pas des autorisations nécessaires \(<xref:System.UnauthorizedAccessException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>   
 [How to: Find Files with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)   
 [How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)