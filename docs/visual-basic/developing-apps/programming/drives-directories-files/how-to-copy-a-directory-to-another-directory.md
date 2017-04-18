---
title: "Guide pratique pour copier un répertoire vers un autre répertoire en Visual Basic | Microsoft Docs"
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
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: 19
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
ms.openlocfilehash: 0b2d59f347df075e3f8c4f952b62e8ad7fa1643f
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>Guide pratique pour copier un répertoire vers un autre répertoire en Visual Basic
Pour copier un répertoire vers un autre répertoire, utilisez la méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>. Cette méthode copie le contenu du répertoire, ainsi que le répertoire lui-même. Si le répertoire cible n’existe pas, il est créé. Si un répertoire portant le même nom existe à l’emplacement cible et que `overwrite` a la valeur `False`, le contenu des deux répertoires est fusionné. Vous pouvez spécifier un nouveau nom pour le répertoire pendant l’opération.  
  
 Lors de la copie des fichiers dans un répertoire, des exceptions provoquées par un fichier spécifique peuvent être levées, par exemple si un fichier existe au cours d’une fusion alors que `overwrite` a la valeur `False`. Quand ces exceptions sont levées, elles sont consolidées en une exception unique dont la propriété `Data` contient des entrées dans lesquelles le chemin du fichier ou répertoire est la clé et le message d’exception spécifique est contenu dans la valeur correspondante.  
  
### <a name="to-copy-a-directory-to-another-directory"></a>Pour copier un répertoire vers un autre répertoire  
  
-   Utilisez la méthode `CopyDirectory`, en spécifiant les noms des répertoires source et de destination. L’exemple suivant copie le répertoire nommé `TestDirectory1` dans `TestDirectory2`, en remplaçant les fichiers existants.  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     Cet exemple de code est également disponible sous la forme d’un extrait de code IntelliSense. Dans le sélecteur d’extraits de code, il se trouve dans **Système de fichiers - Traitement des lecteurs, dossiers et fichiers**. Pour plus d’informations, consultez [Extraits de code](https://docs.microsoft.com/visualstudio/ide/code-snippets).  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le nouveau nom spécifié pour le répertoire contient un signe deux-points ( :) ou une barre oblique (\ ou /) (<xref:System.ArgumentException>).  
  
-   Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (commençant par \\\\.\\) (<xref:System.ArgumentException>).  
  
-   Le chemin n’est pas valide, car il est `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `destinationDirectoryName` est `Nothing` ou une chaîne vide (<xref:System.ArgumentNullException>).  
  
-   Le répertoire source n’existe pas (<xref:System.IO.DirectoryNotFoundException>).  
  
-   Le répertoire source est un répertoire racine (<xref:System.IO.IOException>).  
  
-   Le chemin combiné pointe vers un fichier existant (<xref:System.IO.IOException>).  
  
-   Le chemin source et le chemin cible sont identiques (<xref:System.IO.IOException>).  
  
-   `ShowUI` a la valeur `UIOption.AllDialogs` et l’utilisateur annule l’opération, ou un ou plusieurs fichiers dans le répertoire ne peuvent pas être copiés (<xref:System.OperationCanceledException>).  
  
-   L’opération est cyclique (<xref:System.InvalidOperationException>).  
  
-   Le chemin contient un signe deux-points (:) (<xref:System.NotSupportedException>).  
  
-   Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
-   Un nom de fichier ou de dossier dans le chemin contient un signe deux-points (:) ou son format n’est pas valide (<xref:System.NotSupportedException>).  
  
-   L’utilisateur ne dispose pas des autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
-   Un fichier de destination existe mais n’est pas accessible (<xref:System.UnauthorizedAccessException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>   
 [Guide pratique pour rechercher des sous-répertoires avec un modèle spécifique](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [Guide pratique pour placer la collection de fichiers dans un répertoire](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
