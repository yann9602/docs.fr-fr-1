---
title: Guide pratique pour lire des fichiers texte dans Visual Basic | Microsoft Docs
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
- extended characters, reading
- reading text files
- reading data, text files
- examples [Visual Basic], reading text files
- text files, reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: 27
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 362745101d1a8f7dd61b5e3aabe1c27190c46c07
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>Guide pratique pour lire des fichiers texte dans Visual Basic
La méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> de l’objet `My.Computer.FileSystem` permet de lire un fichier texte. L'encodage du fichier peut être spécifié si le contenu de ce dernier utilise l'encodage ASCII ou UTF-8.  
  
 Si vous lisez un fichier avec des caractères étendus, vous devez spécifier son encodage.  
  
> [!NOTE]
>  Pour lire un fichier ligne par ligne, utilisez la méthode <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> de l’objet `My.Computer.FileSystem`. La méthode `OpenTextFileReader` retourne un objet <xref:System.IO.StreamReader>. Vous pouvez utiliser la méthode <xref:System.IO.StreamReader.ReadLine%2A> de l’objet `StreamReader` pour lire un fichier ligne par ligne. Vous pouvez tester la fin du fichier avec la méthode <xref:System.IO.StreamReader.EndOfStream%2A> de l’objet `StreamReader`.  
  
### <a name="to-read-from-a-text-file"></a>Pour lire un fichier texte  
  
-   Utilisez la méthode `ReadAllText` de l'objet `My.Computer.FileSystem` pour lire le contenu d'un fichier texte dans une chaîne en fournissant le chemin d'accès. L'exemple suivant lit le contenu du fichier test.txt dans une chaîne puis l'affiche dans un message.  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a>Pour lire un fichier texte encodé  
  
-   Utilisez la méthode `ReadAllText` de l'objet `My.Computer.FileSystem` pour lire le contenu d'un fichier texte dans une chaîne en fournissant le chemin d'accès et le type d'encodage du fichier. L'exemple suivant lit le contenu du fichier UTF32 test.txt dans une chaîne puis l'affiche dans un message.  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs, il contient des caractères non valides ou il s’agit d’un chemin d’appareil (<xref:System.ArgumentException>).  
  
-   Le chemin n’est pas valide, car il est `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Le fichier n’existe pas (<xref:System.IO.FileNotFoundException>).  
  
-   Le fichier est utilisé par un autre processus ou une erreur d’E/S s’est produite (<xref:System.IO.IOException>).  
  
-   Le chemin dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
-   Un nom de fichier ou de répertoire dans le chemin contient un signe deux-points (:) ou son format n’est pas valide (<xref:System.NotSupportedException>).  
  
-   Il n’y a pas assez de mémoire pour écrire la chaîne dans la mémoire tampon (<xref:System.OutOfMemoryException>).  
  
-   L’utilisateur ne dispose pas des autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu. Par exemple, il se peut que le fichier nommé Form1.vb ne soit pas un fichier source [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
 Vérifiez toutes les entrées avant d'utiliser les données dans votre application. Le fichier n'a peut-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>   
 [Lecture à partir de fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Guide pratique pour lire des fichiers texte délimités par des virgules](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [Guide pratique pour lire des fichiers texte de largeur fixe](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [Guide pratique pour lire des fichiers texte avec plusieurs formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Dépannage : lecture et écriture dans des fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Procédure pas à pas : manipulation de fichiers et de répertoires en Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Codages de fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
