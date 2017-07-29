---
title: "Guide pratique pour créer une copie d'un fichier dans le même répertoire en Visual Basic"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- File.Copy
dev_langs:
- VB
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files, copying
- CopyFile method, copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7e15b85a72c9b2504551174f5b104bdbb01cf3f3
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a>Guide pratique pour créer une copie d'un fichier dans le même répertoire en Visual Basic
Utilisez la méthode `My.Computer.FileSystem.CopyFile` pour copier des fichiers. Les paramètres permettent de remplacer les fichiers existants, de renommer le fichier, d’afficher la progression de l’opération et d’autoriser l’utilisateur à annuler l’opération.  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a>Pour créer une copie d’un fichier dans le même dossier  
  
-   Utilisez la méthode `CopyFile`, en fournissant le fichier cible et l’emplacement. L’exemple suivant crée une copie de `test.txt` nommée `test2.txt`.  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a>Pour créer une copie d’un fichier dans le même dossier en remplaçant les fichiers existants  
  
-   Utilisez la méthode `CopyFile`, en fournissant le fichier cible et l’emplacement, et en affectant la valeur `True` à `overwrite`. L’exemple suivant crée une copie de `test.txt` nommée `test2.txt` et remplace les fichiers existants portant ce nom.  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception :  
  
-   Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (il commence par \\\\.\\) (<xref:System.ArgumentException>).  
  
-   Le système n’a pas pu récupérer le chemin absolu (<xref:System.ArgumentException>).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Le fichier source n’est pas valide ou n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
-   Le chemin combiné pointe vers un répertoire existant (<xref:System.IO.IOException>).  
  
-   Le fichier de destination existe et `overwrite` a la valeur `False` (<xref:System.IO.IOException>).  
  
-   L’utilisateur ne dispose pas des autorisations suffisantes pour accéder au fichier (<xref:System.IO.IOException>).  
  
-   Un fichier du même nom dans le dossier cible est en cours d’utilisation (<xref:System.IO.IOException>).  
  
-   Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou n’a pas un format correct (<xref:System.NotSupportedException>).  
  
-   `ShowUI` a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et l’utilisateur a annulé l’opération (<xref:System.OperationCanceledException>).  
  
-   `ShowUI`a la valeur `True`, `onUserCancel` a la valeur `ThrowException` et une erreur d’E/S non spécifiée se produit (<xref:System.OperationCanceledException>).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
-   L’utilisateur ne dispose pas de l’autorisation nécessaire (<xref:System.UnauthorizedAccessException>).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [Guide pratique pour copier des fichiers avec un modèle spécifique dans un répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [Guide pratique pour créer une copie d’un fichier dans un autre répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [Guide pratique pour copier un répertoire vers un autre répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [Guide pratique : renommer un fichier](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)

