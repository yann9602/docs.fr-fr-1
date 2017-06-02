---
title: "T&#226;ches d&#39;E/S courantes | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "E/S, tâches courantes"
ms.assetid: bf00c380-706a-4e38-b829-454a480629fc
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
---
# T&#226;ches d&#39;E/S courantes
L'espace de noms <xref:System.IO> fournit plusieurs classes qui permettent d'exécuter différentes actions, telles que la lecture et l'écriture, sur des fichiers, des répertoires et des flux de données.  Pour plus d'informations, consultez [Fichier et flux de données E\/S](../../../docs/standard/io/index.md).  
  
## Tâches de fichier courantes  
  
|Pour...|Consultez l'exemple décrit dans cette rubrique...|  
|-------------|-------------------------------------------------------|  
|Créer un fichier texte|Méthode <xref:System.IO.File.CreateText%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.FileInfo.CreateText%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.File.Create%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.FileInfo.Create%2A?displayProperty=fullName>|  
|Écrire dans un fichier texte|[Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)<br /><br /> [Comment : écrire un fichier texte](../Topic/How%20to:%20Write%20a%20Text%20File%20\(C++-CLI\).md)|  
|Lire à partir d'un fichier texte|[Comment : lire du texte dans un fichier](../../../docs/standard/io/how-to-read-text-from-a-file.md)|  
|Ajouter du texte dans un fichier|[Comment : ouvrir un fichier journal et y ajouter des éléments](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)<br /><br /> Méthode <xref:System.IO.File.AppendText%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.FileInfo.AppendText%2A?displayProperty=fullName>|  
|Renommer ou déplacer un fichier|Méthode <xref:System.IO.File.Move%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.FileInfo.MoveTo%2A?displayProperty=fullName>|  
|Supprimer un fichier|Méthode <xref:System.IO.File.Delete%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.FileInfo.Delete%2A?displayProperty=fullName>|  
|Copier un fichier|Méthode <xref:System.IO.File.Copy%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.FileInfo.CopyTo%2A?displayProperty=fullName>|  
|Obtenir la taille d'un fichier|Propriété <xref:System.IO.FileInfo.Length%2A?displayProperty=fullName>|  
|Obtenir les attributs d'un fichier|Méthode <xref:System.IO.File.GetAttributes%2A?displayProperty=fullName>|  
|Définir les attributs d'un fichier|Méthode <xref:System.IO.File.SetAttributes%2A?displayProperty=fullName>|  
|Déterminer si un fichier existe|Méthode <xref:System.IO.File.Exists%2A?displayProperty=fullName>|  
|Lire à partir d'un fichier binaire|[Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Écrire dans un fichier binaire|[Comment : lire et écrire dans un fichier de données créé récemment](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)|  
|Récupérer une extension de nom de fichier|Méthode <xref:System.IO.Path.GetExtension%2A?displayProperty=fullName>|  
|Récupérer le chemin d'accès qualifié complet d'un fichier|Méthode <xref:System.IO.Path.GetFullPath%2A?displayProperty=fullName>|  
|Récupérer le nom de fichier et son extension à partir d'un chemin d'accès|Méthode <xref:System.IO.Path.GetFileName%2A?displayProperty=fullName>|  
|Modifier l'extension d'un fichier|Méthode <xref:System.IO.Path.ChangeExtension%2A?displayProperty=fullName>|  
  
## Tâches de répertoire courantes  
  
|Pour...|Consultez l'exemple décrit dans cette rubrique...|  
|-------------|-------------------------------------------------------|  
|Accéder à un fichier dans un dossier spécial comme Mes documents|[Comment : écrire du texte dans un fichier](../../../docs/standard/io/how-to-write-text-to-a-file.md)|  
|Créer un répertoire|Méthode <xref:System.IO.Directory.CreateDirectory%2A?displayProperty=fullName><br /><br /> Propriété <xref:System.IO.FileInfo.Directory%2A?displayProperty=fullName>|  
|Créer un sous\-répertoire|Méthode <xref:System.IO.DirectoryInfo.CreateSubdirectory%2A?displayProperty=fullName>|  
|Renommer ou déplacer un répertoire|Méthode <xref:System.IO.Directory.Move%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.DirectoryInfo.MoveTo%2A?displayProperty=fullName>|  
|Copier un répertoire|[Comment : copier des répertoires](../../../docs/standard/io/how-to-copy-directories.md)|  
|Supprimer un répertoire|Méthode <xref:System.IO.Directory.Delete%2A?displayProperty=fullName><br /><br /> Méthode <xref:System.IO.DirectoryInfo.Delete%2A?displayProperty=fullName>|  
|Afficher les fichiers et les sous\-répertoires d'un répertoire|[Comment : énumérer des répertoires et des fichiers](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)|  
|Rechercher la taille d'un répertoire|Classe <xref:System.IO.Directory?displayProperty=fullName>|  
|Déterminer si un répertoire existe|Méthode <xref:System.IO.Directory.Exists%2A?displayProperty=fullName>|  
  
## Voir aussi  
 [Fichier et flux de données E\/S](../../../docs/standard/io/index.md)   
 [Composition de flux](../../../docs/standard/io/composing-streams.md)   
 [E\/S sur fichier asynchrones](../../../docs/standard/io/e-s-sur-fichier-asynchrones.md)