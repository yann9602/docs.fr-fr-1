---
title: "Comment&#160;: cr&#233;er des fichiers et des r&#233;pertoires dans un stockage isol&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "répertoires (.NET Framework), stockage isolé"
  - "fichiers (.NET Framework), stockage isolé"
  - "stockage isolé, création de fichiers et de répertoires"
  - "magasins de données, création de fichiers et de répertoires"
  - "stockage de données avec le stockage isolé, création de fichiers et de répertoires"
  - "magasins, création de fichiers et de répertoires"
  - "stockage de données avec le stockage isolé, création de fichiers et de répertoires"
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: cr&#233;er des fichiers et des r&#233;pertoires dans un stockage isol&#233;
Après avoir obtenu un magasin isolé, vous pouvez créer des répertoires et des fichiers pour stocker des données.  Dans un magasin, les noms de fichier et de répertoire sont spécifiés par rapport à la racine du système de fichiers virtuel.  
  
 Pour créer un répertoire, utilisez la méthode d'instance <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=fullName>.  Si vous spécifiez un sous\-répertoire d'un répertoire qui n'existe pas, ces deux répertoires sont créés.  Si vous spécifiez un dossier qui existe déjà, la méthode renvoie le résultat sans créer un répertoire, et aucune exception n'est levée.  Toutefois, si vous spécifiez un nom de répertoire qui contient des caractères non valides, une exception <xref:System.IO.IsolatedStorage.IsolatedStorageException> est levée.  
  
 Pour créer un fichier, utilisez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=fullName>.  
  
 Dans le système d'exploitation Windows, le fichier et le répertoire d'isolement de stockage ne respectent pas la casse.  Ainsi, si vous créez un fichier intitulé `ThisFile.txt`, et que vous ouvrez ensuite un autre fichier intitulé `THISFILE.TXT`, un seul fichier est créé.  Le nom de fichier est affiché selon sa casse d'origine.  
  
## Exemple  
 L'exemple de code suivant illustre la création de fichiers et de répertoires dans un magasin isolé.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>   
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)