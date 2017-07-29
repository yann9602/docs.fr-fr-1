---
title: "Guide pratique pour créer un répertoire en Visual Basic"
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
- directories [Visual Basic], creating
- folders [Visual Basic], creating
ms.assetid: 0351a2ca-24d8-43b5-bb39-9b99e6401cff
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 1a45a785916b480dcee6e36fd295390266eaa0a0
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-create-a-directory-in-visual-basic"></a>Guide pratique pour créer un répertoire en Visual Basic
Utilisez la méthode `CreateDirectory` de l’objet `My.Computer.FileSystem` pour créer des répertoires.  
  
 Si le répertoire existe déjà, aucune exception n’est levée.  
  
### <a name="to-create-a-directory"></a>Pour créer un répertoire  
  
-   Utilisez la méthode `CreateDirectory`, en spécifiant le chemin complet de l’emplacement où le répertoire doit être créé. Cet exemple crée le répertoire `NewDirectory` dans `C:\Documents and Settings\All Users\Documents`.  
  
     [!code-vb[VbVbcnMyFileSystem#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-directory_1.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le format du nom du répertoire est incorrect. Par exemple, il contient des caractères non conformes ou uniquement des espaces blancs (<xref:System.ArgumentException>).  
  
-   Le répertoire parent du répertoire à créer est en lecture seule (<xref:System.IO.IOException>).  
  
-   Le nom du répertoire est `Nothing` (<xref:System.ArgumentNullException>).  
  
-   Le nom du répertoire est trop long (<xref:System.IO.PathTooLongException>).  
  
-   Le nom du répertoire est un signe deux-points (:) (<xref:System.NotSupportedException>).  
  
-   L’utilisateur n’a pas l’autorisation de créer le répertoire (<xref:System.UnauthorizedAccessException>).  
  
-   L’utilisateur ne dispose pas des autorisations dans une situation de confiance partielle (<xref:System.Security.SecurityException>).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CreateDirectory%2A>   
 [Création, suppression et déplacement de fichiers et de répertoires](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)

