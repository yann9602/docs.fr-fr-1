---
title: "How to: Create a File in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "text files, creating"
  - "files, creating"
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 15
---
# How to: Create a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Cet exemple crée un fichier texte vide dans le chemin d'accès spécifié à l'aide de la méthode <xref:System.IO.File.Create%2A> de la classe <xref:System.IO.File>.  
  
## Exemple  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## Compilation du code  
 Utilisez la variable `file` pour écrire dans le fichier.  
  
## Programmation fiable  
 Si le fichier existe déjà, il est remplacé.  
  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le nom du chemin d'accès est incorrect.  Il contient par exemple des caractères non valides ou se compose uniquement d'un espace blanc \(<xref:System.ArgumentException>\).  
  
-   Le chemin d'accès est en lecture seule \(classe <xref:System.IO.IOException>\).  
  
-   Le nom du chemin d'accès est `Nothing` \(<xref:System.ArgumentNullException>\).  
  
-   Le nom du chemin d'accès est trop long \(<xref:System.IO.PathTooLongException>\).  
  
-   Le chemin d'accès n'est pas valide \(<xref:System.IO.DirectoryNotFoundException>\).  
  
-   Le chemin d'accès se compose uniquement du signe deux\-points « : » \(<xref:System.NotSupportedException>\).  
  
## Sécurité .NET Framework  
 Une <xref:System.Security.SecurityException> peut être levée dans des environnements où le niveau de confiance n'est pas total.  
  
 L'appel à la méthode <xref:System.IO.File.Create%2A> requiert <xref:System.Security.Permissions.FileIOPermission>.  
  
 Une exception <xref:System.UnauthorizedAccessException> est levée si l'utilisateur n'a pas l'autorisation de créer le fichier.  
  
## Voir aussi  
 <xref:System.IO>   
 <xref:System.IO.File.Create%2A>   
 [Utilisation de bibliothèques à partir de code d'un niveau de confiance partiel](../Topic/Using%20Libraries%20from%20Partially%20Trusted%20Code.md)   
 [Notions fondamentales de la sécurité d'accès du code](../Topic/Code%20Access%20Security%20Basics.md)