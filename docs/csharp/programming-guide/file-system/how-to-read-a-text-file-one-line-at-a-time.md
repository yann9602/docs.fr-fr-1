---
title: "Comment&#160;: lire un fichier texte ligne par ligne (Visual C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "lire des fichiers texte, ligne par ligne"
  - "ReadLine (méthode C#)"
  - "fichiers texte (C#)"
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Comment&#160;: lire un fichier texte ligne par ligne (Visual C#)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

Cet exemple lit le contenu d'un fichier texte, ligne par ligne, dans une chaîne à l'aide de la méthode `ReadLine` de la classe `StreamReader`.  Chaque ligne de texte est stockée dans la chaîne `line` et affichée à l'écran.  
  
## Exemple  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## Compilation du code  
 Copiez le code et collez\-le dans la méthode `Main` d'une application console.  
  
 Remplacez `"c:\test.txt"` par le nom du fichier réel.  
  
## Programmation fiable  
 Les conditions ci\-dessous peuvent générer une exception.  
  
-   Le fichier peut ne pas exister.  
  
## Sécurité .NET Framework  
 Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.  Par exemple, il se peut que le fichier `myFile.cs` ne soit pas un fichier source C\#.  
  
## Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)