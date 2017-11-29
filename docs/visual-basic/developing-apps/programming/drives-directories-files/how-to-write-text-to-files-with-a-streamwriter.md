---
title: "Guide pratique pour écrire du texte dans des fichiers à l'aide de Streamwriter dans Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 874bb9cb88bbf25cb6208a0a33858855a7b26a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>Guide pratique pour écrire du texte dans des fichiers à l'aide de Streamwriter dans Visual Basic
Cet exemple ouvre un objet <xref:System.IO.StreamWriter> avec la méthode `My.Computer.FileSystem.OpenTextFileWriter` et l’utilise pour écrire une chaîne dans un fichier texte avec la méthode <xref:System.IO.TextWriter.WriteLine%2A> de la classe <xref:System.IO.StreamWriter>.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le fichier existe et est en lecture seule (<xref:System.IO.IOException>).  
  
-   Le disque est plein (<xref:System.IO.IOException>).  
  
-   Le nom du chemin est trop long (<xref:System.IO.PathTooLongException>).  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Cet exemple crée un fichier s’il n’existe pas déjà. Si une application doit créer un fichier, elle doit disposer de l’autorisation `Create` pour accéder au dossier. Si le fichier existe déjà, l’application a uniquement besoin de l’autorisation `Write`, qui est une autorisation de niveau inférieur. Quand cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n’accorder l’autorisation `Read` que sur un seul fichier, plutôt que l’autorisation `Create` sur un dossier.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [Guide pratique : lire à partir de fichiers texte](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [Écriture dans des fichiers](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
