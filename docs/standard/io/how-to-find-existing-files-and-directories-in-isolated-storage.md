---
title: "Comment&#160;: rechercher des fichiers et des r&#233;pertoires existants dans un stockage isol&#233; | Microsoft Docs"
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
  - "magasins, rechercher des fichiers et des répertoires"
  - "chercher des fichiers dans un fichier de stockage isolé"
  - "répertoires (.NET Framework), stockage isolé"
  - "stockage isolé, rechercher des fichiers et des répertoires"
  - "stockage de données à l’aide du stockage isolé, rechercher des fichiers et des répertoires"
  - "fichiers (.NET Framework), stockage isolé"
  - "magasins de données, rechercher des fichiers et des répertoires"
  - "chercher des répertoires dans un fichier de stockage isolé"
  - "stockage de données à l’aide du stockage isolé, rechercher des fichiers et des répertoires"
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
caps.latest.revision: 12
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 12
---
# Comment&#160;: rechercher des fichiers et des r&#233;pertoires existants dans un stockage isol&#233;
Pour rechercher un dossier dans le stockage d'isolation, utilisez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=fullName>.  Cette méthode accepte une chaîne qui représente un modèle de recherche.  Vous pouvez utiliser les caractères génériques à un caractère \(?\) et de plusieurs caractères \(\*\) dans le modèle de recherche, mais les caractères génériques doivent apparaître dans la dernière partie du nom.  Par exemple, `directory1/*ect*` est une chaîne valide, mais `*ect*/directory2` ne l'est pas.  
  
 Pour rechercher un fichier, utilisez la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=fullName>.  Les limites des caractères génériques des chaînes recherchées qui s'appliquent à <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> s'appliquent également à <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  
  
 Aucune de ces méthodes n'est récursive ; la classe <xref:System.IO.IsolatedStorage.IsolatedStorageFile> ne fournit aucune méthode pour répertorier tous les répertoires fichiers ou dans le magasin.  Toutefois, les méthodes récursives sont affichées dans l'exemple de code suivant.  
  
## Exemple  
 L'exemple de code suivant illustre la création de fichiers et de répertoires dans un magasin isolé.  Premièrement, un magasin isolé pour un utilisateur, domaine et assembly est extrait et placé dans la variable `isoStore`.  La méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> définit quelques répertoires distincts et le constructeur <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> crée quelques fichiers dans ces répertoires.  Le code parcourt ensuite les résultats de la méthode `GetAllDirectories`.  Cette méthode utilise <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> pour rechercher tous les noms de répertoire dans le répertoire en cours.  Ces noms sont stockés dans un tableau, puis `GetAllDirectories` s'appelle, en passant chacun des répertoires rencontrés.  Le resultat est que tous les noms de répertoire sont retournés dans un tableau.  Ensuite, le code appelle la méthode `GetAllFiles`.  Cette méthode appelle `GetAllDirectories` pour découvrir les noms de tous les répertoires, puis vérifie les fichiers de chacun de ces répertoires en utilisant la méthode <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.  Le résultat est retourné dans un tableau.  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>   
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)