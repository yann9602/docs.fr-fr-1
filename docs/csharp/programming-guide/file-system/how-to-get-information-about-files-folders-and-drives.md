---
title: "Comment&#160;: obtenir des informations sur les fichiers, dossiers et lecteurs (Guide de programmation&#160;C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "fichiers (C#), obtenir des informations sur"
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: 30
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 30
---
# Comment&#160;: obtenir des informations sur les fichiers, dossiers et lecteurs (Guide de programmation&#160;C#)
Dans le .NET Framework, vous pouvez accéder aux informations de système de fichiers à l'aide des classes suivantes :  
  
-   <xref:System.IO.FileInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DriveInfo?displayProperty=fullName>  
  
-   <xref:System.IO.Directory?displayProperty=fullName>  
  
-   <xref:System.IO.File?displayProperty=fullName>  
  
 Les classes <xref:System.IO.FileInfo> et <xref:System.IO.DirectoryInfo> représentent un fichier ou un répertoire et contiennent des propriétés qui exposent nombre des attributs de fichier pris en charge par le système de fichiers NTFS.  Elles contiennent également des méthodes pour ouvrir, fermer, déplacer et supprimer des fichiers et des dossiers.  Vous pouvez créer des instances de ces classes en passant une chaîne qui représente le nom du fichier, du dossier ou du lecteur au constructeur :  
  
```c#  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Vous pouvez également obtenir les noms des fichiers, des dossiers ou des lecteurs en appelant <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=fullName>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=fullName> et <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=fullName>.  
  
 Les classes <xref:System.IO.Directory?displayProperty=fullName> et <xref:System.IO.File?displayProperty=fullName> fournissent des méthodes statiques permettant d'extraire des informations sur des répertoires et des fichiers.  
  
## Exemple  
 L'exemple suivant montre diverses manières d'accéder aux informations relatives aux fichiers et aux dossiers.  
  
 [!code-cs[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## Programmation fiable  
 Lorsque vous traitez des chaînes de chemin d'accès spécifiées par l'utilisateur, vous devez également gérer les exceptions levées dans les cas suivants :  
  
-   Le nom de fichier est incorrect.  Il contient par exemple des caractères non valides ou se compose uniquement d'un espace blanc.  
  
-   Le nom de fichier est null.  
  
-   Le nom de fichier dépasse la longueur maximale définie par le système.  
  
-   Le nom de fichier comporte le signe deux\-points \(:\).  
  
 Si l'application ne dispose pas des autorisations nécessaires pour lire le fichier spécifié, la méthode `Exists` retourne `false`, qu'il existe ou non un chemin d'accès, mais ne lève pas d'exception.  
  
## Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)