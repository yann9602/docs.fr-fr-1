---
title: "How to: Write Text to Files in the My Documents Directory in Visual Basic | Microsoft Docs"
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
  - "files, writing to"
  - "text, writing to files"
  - "examples [Visual Basic], text files"
  - "writing to files, in My Documents"
ms.assetid: 1c726124-781d-4976-9baa-ed46814ff3fe
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Write Text to Files in the My Documents Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

L'objet `My.Computer.FileSystem.SpecialDirectories` vous permet d'accéder aux répertoires spéciaux, tels que le répertoire **Mes documents**.  
  
## Procédure  
  
#### Pour écrire de nouveaux fichiers texte dans le répertoire Mes documents  
  
1.  Utilisez la propriété `My.Computer.FileSystem.SpecialDirectories.MyDocuments` pour fournir le chemin d'accès.  
  
     [!code-vb[VbFileIOWrite#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_1.vb)]  
  
2.  Utilisez la méthode `WriteAllText` pour écrire du texte dans le fichier spécifié.  
  
     [!code-vb[VbVbcnMyFileSystem#14](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_2.vb)]  
  
## Exemple  
 [!code-vb[VbFileIOWrite#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-in-the-my-documents-directory_3.vb)]  
  
## Compilation du code  
 Remplacez `test.txt` par le nom du fichier dans lequel vous souhaitez écrire.  
  
## Programmation fiable  
 Ce code lève de nouveau toutes les exceptions qui peuvent se produire lorsque vous écrivez du texte dans le fichier.  Vous pouvez réduire la probabilité d'exceptions en utilisant les contrôles Windows Forms, tels que les composants [OpenFileDialog](../Topic/OpenFileDialog%20Component%20\(Windows%20Forms\).md) et [SaveFileDialog](../Topic/SaveFileDialog%20Component%20\(Windows%20Forms\).md) qui limitent les choix de l'utilisateur aux noms de fichiers valides.  Toutefois, l'utilisation de ces contrôles n'est pas sans poser de problèmes.  Le système de fichiers peut changer entre le moment où l'utilisateur sélectionne un fichier et le moment où le code s'exécute.  La gestion des exceptions est donc presque toujours nécessaire lors de l'utilisation de fichiers.  
  
## Sécurité .NET Framework  
 Si vous exécutez le programme dans un contexte partiellement fiable, le code peut lever une exception en raison de privilèges insuffisants.  Pour plus d'informations, consultez [Notions fondamentales de la sécurité d'accès du code](../Topic/Code%20Access%20Security%20Basics.md).  
  
 Cet exemple crée un fichier.  Si une application doit créer un fichier, elle doit disposer de l'autorisation Créer pour le dossier.  Les autorisations sont définies à l'aide de listes de contrôle d'accès.  Si le fichier existe déjà, l'application a uniquement besoin de l'autorisation Écrire, ce qui représente un privilège inférieur.  Lorsque cela est possible, il est plus sûr de créer le fichier au cours du déploiement et de n'accorder les privilèges Lire que sur un seul fichier \(plutôt que les privilèges Créer sur un dossier\).  En outre, il est plus sûr d'écrire les données dans des dossiers utilisateur que dans le dossier racine ou le dossier **Program Files**.  Pour plus d'informations, consultez [ACL Technology Overview](http://msdn.microsoft.com/fr-fr/06fbf66d-6f02-4378-b863-b2f12e349045).  
  
## Voir aussi  
 <xref:System.IO.Path.Combine%2A?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Computer>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.SpecialDirectories>