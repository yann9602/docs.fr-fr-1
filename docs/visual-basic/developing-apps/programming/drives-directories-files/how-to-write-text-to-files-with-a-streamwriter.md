---
title: "How to: Write Text to Files with a StreamWriter in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "files, writing to"
  - "text, writing to files"
  - "writing to files, StreamWriter"
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write Text to Files with a StreamWriter in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Cet exemple ouvre un objet <xref:System.IO.StreamWriter> avec la méthode `My.Computer.FileSystem.OpenTextFileWriter` et l'utilise pour écrire une chaîne dans un fichier texte à l'aide de la méthode <xref:System.IO.TextWriter.WriteLine%2A> de la classe <xref:System.IO.StreamWriter>.  
  
## Exemple  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le fichier existe déjà et est en lecture seule \(<xref:System.IO.IOException>\).  
  
-   Le disque est saturé \(<xref:System.IO.IOException>\).  
  
-   Le nom de chemin d'accès est trop long \(<xref:System.IO.PathTooLongException>  
  
## Sécurité .NET Framework  
 Cet exemple crée un fichier s'il n'existe pas.  Si une application doit créer un fichier, elle doit disposer de l'accès `Create` pour le dossier.  Si le fichier existe déjà, l'application n'a besoin que d'un accès `Write`, un privilège moins important.  Dans la mesure du possible, et pour des raisons de sécurité, il est préférable de créer le fichier au moment du déploiement et d'accorder uniquement un accès `Read` à un seul fichier plutôt qu'un accès `Create` à l'ensemble du dossier.  
  
## Voir aussi  
 <xref:System.IO.StreamWriter>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>   
 [How to: Read from Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)   
 [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)