---
title: "How to: Read Text from Files with a StreamReader (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "reading files, text"
  - "text, reading from files"
  - "reading text from files"
  - "files, reading"
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Read Text from Files with a StreamReader (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

L'objet `My.Computer.FileSystem` fournit des méthodes pour ouvrir un <xref:System.IO.TextReader> et un <xref:System.IO.TextWriter>.  Ces méthodes, `OpenTextFileWriter` et `OpenTextFileReader`, sont des méthodes avancées qui n'apparaissent pas dans IntelliSense tant que vous ne sélectionnez pas l'onglet **Tout**.  
  
### Pour lire une ligne d'un fichier à l'aide d'un lecteur de texte  
  
-   Utilisez la méthode `OpenTextFileReader` pour ouvrir le <xref:System.IO.TextReader> en spécifiant le fichier.  Cet exemple ouvre le fichier nommé `testfile.txt`, en lit une ligne et affiche cette dernière dans un message.  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-text-from-files-with-a-streamreader_1.vb)]  
  
## Programmation fiable  
 Le fichier lu doit être un fichier texte.  
  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.  Par exemple, il se peut qu'un fichier nommé Form1.vb ne soit pas un fichier source Visual Basic.  
  
 Vérifiez toutes les entrées avant d'utiliser les données dans votre application.  Le fichier n'a peut\-être pas le contenu attendu, et les méthodes utilisées pour lire le fichier peuvent échouer.  
  
## Sécurité .NET Framework  
 Pour lire un fichier, votre assembly requiert un niveau de privilège accordé par la classe <xref:System.Security.Permissions.FileIOPermission>.  Si vous exécutez le programme dans un contexte partiellement fiable, le code peut lever une exception en raison de privilèges insuffisants.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../Topic/Code%20Access%20Security%20Basics.md).  L'utilisateur doit également avoir accès au fichier.  Pour plus d'informations, consultez [ACL Technology Overview](http://msdn.microsoft.com/fr-fr/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## Voir aussi  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:System.Windows.Forms.OpenFileDialog>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>   
 [SaveFileDialog, composant](../Topic/SaveFileDialog%20Component%20\(Windows%20Forms\).md)   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)