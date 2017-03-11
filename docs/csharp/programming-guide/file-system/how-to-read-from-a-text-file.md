---
title: "Comment&#160;: lire un fichier texte (Guide de programmation C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "StreamReader.ReadToEnd"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "lire des données, fichiers texte"
  - "lire des fichiers texte"
  - "fichiers texte, lire"
  - "fichiers texte, écrire dans"
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# Comment&#160;: lire un fichier texte (Guide de programmation C#)
Cet exemple lit le contenu d'un fichier texte à l'aide de les méthodes statiques <xref:System.IO.File.ReadAllText%2A> et <xref:System.IO.File.ReadAllLines%2A> de la classe d' <xref:System.IO.File?displayProperty=fullName> .  
  
 Pour obtenir un exemple qui utilise <xref:System.IO.StreamReader>, consultez [Comment : lire un fichier texte ligne par ligne](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Les fichiers utilisés dans cet exemple sont créés dans la rubrique [Comment : écrire dans un fichier texte](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).  
  
## Exemple  
 [!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/csharp/csFilesFolders/FileIteration.cs#4)]  
  
## Compilation du code  
 Copiez le code et collez \-le dans une application console C\#.  
  
 Si vous n'utilisez pas les fichiers texte de [Comment : écrire dans un fichier texte](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), remplacez l'argument en `ReadAllText` et à `ReadAllLines` par le chemin d'accès approprié et le nom de fichier sur votre ordinateur.  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le fichier n'existe pas ou n'existe pas à l'emplacement spécifié.  Vérifiez le chemin d'accès et l'orthographe du nom de fichier.  
  
## Sécurité .NET Framework  
 Ne comptez pas sur le nom d'un fichier pour en déterminer le contenu du fichier.  Par exemple, le fichier `myFile.cs` ne peut pas être un fichier source C\#.  
  
## Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)