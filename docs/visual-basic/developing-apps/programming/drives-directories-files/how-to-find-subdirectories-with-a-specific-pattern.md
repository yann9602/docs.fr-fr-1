---
title: "How to: Find Subdirectories with a Specific Pattern in Visual Basic | Microsoft Docs"
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
  - "pattern matching"
  - "folders, finding"
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Find Subdirectories with a Specific Pattern in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> retourne une collection en lecture seule de chaînes représentant les noms de chemin des sous\-répertoires d'un répertoire.  Vous pouvez utiliser le paramètre `wildCards` pour spécifier un modèle spécifique.  Si vous souhaitez inclure le contenu des sous\-répertoires dans la recherche, affectez le paramètre `searchType` à `SearchOption.SearchAllSubDirectories`.  
  
 Une collection vide est retournée si aucun répertoire correspondant au modèle spécifié n'est trouvé.  
  
### Pour rechercher des sous\-répertoires d'un modèle spécifique  
  
-   Utilisez la méthode `GetDirectories` en fournissant le nom et le chemin d'accès du répertoire à rechercher.  L'exemple suivant retourne tous les répertoires de la structure de répertoire qui contiennent le mot « Logs » dans leur nom et les ajoute à `ListBox1`.  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-find-subdirectori_1.vb)]  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le chemin d'accès n'est pas valide pour l'une des raisons suivantes : il correspond à une chaîne de longueur nulle, ne contient que des espaces blancs, comporte des caractères non valides ou représente un chemin d'accès de périphérique \(commençant par \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   Un ou plusieurs des caractères génériques spécifiés ont une valeur `Nothing`, constituent une chaîne vide ou contiennent uniquement des espaces \(<xref:System.ArgumentNullException>\).  
  
-   `directory` n'existe pas \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   `directory` pointe sur un fichier existant \(<xref:System.IO.IOException>\).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système \(<xref:System.IO.PathTooLongException>\).  
  
-   Un nom de fichier ou de dossier du chemin d'accès contient un signe deux\-points \(:\) ou n'a pas un format correct \(<xref:System.NotSupportedException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin d'accès \(<xref:System.Security.SecurityException>\).  
  
-   L'utilisateur n'a pas les autorisations nécessaires \(<xref:System.UnauthorizedAccessException>\).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>   
 [How to: Find Files with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)