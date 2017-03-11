---
title: "Comment&#160;: cr&#233;er une cl&#233; dans le Registre (Visual C#) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "clés, créer dans registre"
  - "clés de Registre, créer (C#)"
  - "Registre, ajouter des clés et des valeurs (C#)"
ms.assetid: 8fa475b0-e01f-483a-9327-fd03488fdf5d
caps.latest.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 14
---
# Comment&#160;: cr&#233;er une cl&#233; dans le Registre (Visual C#)
Cet exemple ajoute la paire de valeurs "Name" et "Isabella" au Registre de l'utilisateur en cours, sous la clé "Names".  
  
## Exemple  
  
```  
Microsoft.Win32.RegistryKey key;  
key = Microsoft.Win32.Registry.CurrentUser.CreateSubKey("Names");  
key.SetValue("Name", "Isabella");  
key.Close();  
```  
  
## Compilation du code  
  
-   Copiez le code et collez\-le dans la méthode `Main` d'une application console.  
  
-   Remplacez le paramètre `Names` par le nom d'une clé située immédiatement au\-dessous du nœud HKEY\_CURRENT\_USER du Registre.  
  
-   Remplacez le paramètre `Nam`e par le nom d'une valeur située immédiatement au\-dessous du nœud Names.  
  
## Programmation fiable  
 Examinez la structure du Registre afin de trouver un emplacement approprié pour votre clé.  Vous pouvez par exemple ouvrir la clé Software de l'utilisateur en cours et créer une clé avec le nom de votre société.  Vous pouvez ensuite ajouter les valeurs du Registre à la clé de votre société.  
  
 Les conditions ci\-dessous peuvent générer une exception :  
  
-   Le nom de la clé est null.  
  
-   L'utilisateur n'a pas l'autorisation de créer des clés de Registre.  
  
-   Le nom de la clé dépasse la limite de 255 caractères.  
  
-   La clé est fermée.  
  
-   La clé de Registre est en lecture seule.  
  
## Sécurité .NET Framework  
 Pour des raisons de sécurité, il est préférable d'écrire des données dans le dossier utilisateur \(`Microsoft.Win32.Registry.CurrentUser`\) plutôt que sur l'ordinateur local \(`Microsoft.Win32.Registry.LocalMachine`\).  
  
 Lorsque vous créez une valeur de Registre, vous devez déterminer la marche à suivre si cette valeur existe déjà.  Il est possible qu'un autre processus, peut\-être nuisible, ait déjà créé la valeur et puisse y accéder.  Lorsque vous placez des données dans la valeur du Registre, elles sont disponibles pour les autres processus.  Pour empêcher cela, utilisez la méthode `Overload:Microsoft.Win32.RegistryKey.GetValue`.  Elle retourne null si la clé n'existe pas.  
  
 Pour des raisons de sécurité, il est déconseillé de stocker des données confidentielles, telles que des mots de passe, en texte brut dans le Registre, même si la clé de Registre est protégée par des listes de contrôle d'accès \(ACL, Access Control Lists\).  
  
## Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C\#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre](../../../csharp/programming-guide/file-system/file-system-and-the-registry.md)   
 [Lire, écrire et effectuer des suppressions dans le Registre en C\#](http://www.codeproject.com/Articles/3389/Read-write-and-delete-from-registry-with-C)