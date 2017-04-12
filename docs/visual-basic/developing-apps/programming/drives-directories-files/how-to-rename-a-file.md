---
title: Guide pratique pour renommer un fichier en Visual Basic | Microsoft Docs
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
- I/O [Visual Basic], renaming files
- files, renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: 21
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
ms.openlocfilehash: a0a31353ce3ee0c48907f9550f6961260f92b64a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-rename-a-file-in-visual-basic"></a>Guide pratique pour renommer un fichier en Visual Basic
Utilisez la méthode `RenameFile` de l’objet `My.Computer.FileSystem` pour renommer un fichier en fournissant l’emplacement actuel, le nom actuel du fichier et le nouveau nom du fichier. Cette méthode ne peut pas être utilisée pour déplacer un fichier. Utilisez la méthode `MoveFile` pour déplacer et renommer le fichier.  
  
### <a name="to-rename-a-file"></a>Pour renommer un fichier  
  
-   Pour renommer un fichier, utilisez la méthode `My.Computer.FileSystem.RenameFile`. Dans cet exemple, le nom de fichier `Test.txt` est remplacé par `SecondTest.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Système de fichiers - Traitement des lecteurs, dossiers et fichiers**. Pour plus d’informations, consultez [Extraits de code](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (commençant par \\\\.\\) (<xref:System.ArgumentException>).  
  
-   `newName` contient des informations de chemin (<xref:System.ArgumentException>).  
  
-   Le chemin n’est pas valide, car il est `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `newName` est `Nothing` ou une chaîne vide (<xref:System.ArgumentNullException>).  
  
-   Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
-   Un fichier ou un répertoire porte déjà le nom spécifié dans `newName` (<xref:System.IO.IOException>).  
  
-   Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
-   Un nom de fichier ou de répertoire dans le chemin contient un signe deux-points (:) ou son format n’est pas valide (<xref:System.NotSupportedException>).  
  
-   L’utilisateur ne dispose pas des autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
-   L’utilisateur n’a pas l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>   
 [Guide pratique pour déplacer un fichier](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)   
 [Création, suppression et déplacement de fichiers et de répertoires](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)   
 [Guide pratique pour créer une copie d'un fichier dans le même répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [Guide pratique : créer une copie d'un fichier dans un autre répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
