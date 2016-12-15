---
title: "Comment&#160;: copier, supprimer et d&#233;placer des fichiers et dossiers (Guide de programmation&#160;C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "E/S (C#)"
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: copier, supprimer et d&#233;placer des fichiers et dossiers (Guide de programmation&#160;C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Les exemples suivants indiquent comment copier, déplacer et supprimer des fichiers et des dossiers de manière synchrone en utilisant les classes <xref:System.IO.File?displayProperty=fullName>, <xref:System.IO.Directory?displayProperty=fullName>, <xref:System.IO.FileInfo?displayProperty=fullName> et <xref:System.IO.DirectoryInfo?displayProperty=fullName> de l'espace de noms <xref:System.IO?displayProperty=fullName>.  Ces exemples ne fournissent pas de barre de progression ni d'autre interface utilisateur.  Si vous souhaitez fournir une boîte de dialogue de progression standard, consultez [Comment : fournir une boîte de dialogue de progression pour les opérations sur les fichiers](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Utilisez <xref:System.IO.FileSystemWatcher?displayProperty=fullName> pour fournir des événements qui vous permettront de calculer la progression si vous travaillez sur plusieurs fichiers.  Une autre approche est d'utiliser l'appel de code non managé pour appeler les méthodes relatives aux fichiers appropriées dans le shell Windows.  Pour plus d'informations sur la façon d'effectuer ces opérations sur les fichiers de manière asynchrone, consultez [E\/S sur fichier asynchrones](../Topic/Asynchronous%20File%20I-O.md).  
  
## Exemple  
 L'exemple suivant montre comment copier des fichiers et des répertoires.  
  
 [!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## Exemple  
 L'exemple suivant montre comment déplacer des fichiers et des répertoires.  
  
 [!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## Exemple  
 L'exemple suivant montre comment supprimer des fichiers et des répertoires.  
  
 [!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [Comment : fournir une boîte de dialogue de progression pour les opérations sur les fichiers](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)   
 [Fichier et flux de données E\/S](../Topic/File%20and%20Stream%20I-O.md)   
 [Tâches d'E\/S courantes](../Topic/Common%20I-O%20Tasks.md)