---
title: "Guide pratique pour écrire dans des fichiers binaires en Visual Basic | Microsoft Docs"
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
- files, binary access
- WriteAllBytes method
- binary files, writing in Visual Basic
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0d86e39b7150b4ae8fc4de0498b0b786c5669bb4
ms.contentlocale: fr-fr
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-write-to-binary-files-in-visual-basic"></a>Guide pratique pour écrire dans des fichiers binaires en Visual Basic
La méthode <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> écrit des données dans un fichier binaire. Si le paramètre `append` est `True`, elle ajoute les données au fichier ; sinon, les données dans le fichier sont remplacées.  
  
 Si le chemin spécifié (nom de fichier exclu) n’est pas valide, une exception <xref:System.IO.DirectoryNotFoundException> est levée. Si le chemin est valide mais que le fichier n’existe pas, le fichier est créé.  
  
### <a name="to-write-to-a-binary-file"></a>Pour écrire dans un fichier binaire  
  
-   Utilisez la méthode `WriteAllBytes` en fournissant le chemin et le nom du fichier, ainsi que les octets à écrire. Cet exemple ajoute le tableau de données `CustomerData` au fichier nommé `CollectedData.dat`.  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-to-binary-files_1.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception :  
  
-   Le chemin n’est pas valide pour l’une des raisons suivantes : il s’agit d’une chaîne de longueur nulle, il ne contient que des espaces blancs ou il contient des caractères non valides. (<xref:System.ArgumentException>).  
  
-   Le chemin d'accès n'est pas valide, car il a la valeur `Nothing` (<xref:System.ArgumentNullException>).  
  
-   `File` pointe vers un chemin qui n’existe pas (<xref:System.IO.FileNotFoundException> ou <xref:System.IO.DirectoryNotFoundException>).  
  
-   Le fichier est utilisé par un autre processus, ou une erreur E/S se produit (<xref:System.IO.IOException>).  
  
-   Le chemin d'accès dépasse la longueur maximale définie par le système (<xref:System.IO.PathTooLongException>).  
  
-   Un nom de fichier ou de répertoire du chemin d'accès contient un signe deux-points (:) ou n'a pas un format correct (<xref:System.NotSupportedException>).  
  
-   L'utilisateur n'a pas les autorisations nécessaires pour afficher le chemin (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [Guide pratique : insérer du texte dans des fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)
