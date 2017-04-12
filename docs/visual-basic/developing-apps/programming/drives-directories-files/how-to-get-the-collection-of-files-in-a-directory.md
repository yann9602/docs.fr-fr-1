---
title: "Guide pratique pour obtenir la collection de fichiers dans un répertoire en Visual Basic | Microsoft Docs"
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
- folders, working with
- files, accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: 23
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d5b36baee302db0214844e0553473a05603090f1
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>Guide pratique pour obtenir la collection de fichiers dans un répertoire en Visual Basic
Les surcharges de la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> retournent une collection en lecture seule de chaînes représentant les noms des fichiers dans un répertoire :  
  
-   Utilisez la surcharge <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> pour une recherche de fichier simple dans un répertoire spécifié, sans rechercher dans les sous-répertoires.  
  
-   Utilisez la surcharge <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> pour spécifier des options supplémentaires pour votre recherche. Vous pouvez utiliser le paramètre `wildCards` pour spécifier un modèle de recherche. Pour inclure les sous-répertoires dans la recherche, affectez la valeur `searchType` au paramètre <xref:Microsoft.VisualBasic.FileIO.SearchOption?displayProperty=fullName>.  
  
 Une collection vide est retournée si aucun fichier correspondant au modèle spécifié n’est détecté.  
  
### <a name="to-list-files-in-a-directory"></a>Pour énumérer les fichiers contenus dans un répertoire  
  
-   Utilisez l’une des surcharges de méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName>, en spécifiant le nom et le chemin du répertoire où rechercher dans le paramètre `directory`. L’exemple suivant retourne tous les fichiers contenus dans le répertoire et les ajoute à `ListBox1`.  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (commençant par \\\\.\\) (<xref:System.ArgumentException>).  
  
-   Le chemin n’est pas valide, car il est `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `directory` n’existe pas (<xref:System.IO.DirectoryNotFoundException>).  
  
-   `directory` pointe vers un fichier existant (<xref:System.IO.IOException>).  
  
-   Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
-   Un nom de fichier ou de répertoire dans le chemin contient un signe deux-points (:) ou son format n’est pas valide (<xref:System.NotSupportedException>).  
  
-   L’utilisateur ne dispose pas des autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
-   L’utilisateur ne dispose pas des autorisations nécessaires (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>   
 [Guide pratique pour rechercher des fichiers avec un modèle spécifique](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)   
 [Guide pratique pour rechercher des sous-répertoires avec un modèle spécifique](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)

