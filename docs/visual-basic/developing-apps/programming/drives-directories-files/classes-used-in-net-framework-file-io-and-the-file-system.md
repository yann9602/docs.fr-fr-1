---
title: "Classes Used in .NET Framework File I/O and the File System (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "file I/O classes"
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Classes Used in .NET Framework File I/O and the File System (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Les tableaux suivants répertorient les classes couramment utilisées pour l'E\/S de fichier du .NET Framework, les classes par catégorie dans l'E\/S de fichier, les classes utilisées pour créer des flux et les classes utilisées pour lire et écrire dans les flux.  
  
 Pour accéder à la documentation du [!INCLUDE[dnprdnlong](../../../../csharp/programming-guide/events/includes/dnprdnlong_md.md)] et obtenir une liste plus complète, consultez [Vue d'ensemble de la bibliothèque de classes](../Topic/.NET%20Framework%20Class%20Library%20Overview.md).  
  
## Classes E\/S de base pour les fichiers, les lecteurs et les répertoires  
 Le tableau suivant répertorie et décrit les classes principales utilisées pour l'E\/S de fichier.  
  
|Classe|Description|  
|------------|-----------------|  
|<xref:System.IO.Directory?displayProperty=fullName>|Fournit des méthodes statiques pour la création, le déplacement et l'énumération dans les répertoires et les sous\-répertoires.|  
|<xref:System.IO.DirectoryInfo?displayProperty=fullName>|Fournit des méthodes d'instance pour la création, le déplacement et l'énumération dans les répertoires et les sous\-répertoires.|  
|<xref:System.IO.DriveInfo?displayProperty=fullName>|Fournit des méthodes d'instance pour la création, le déplacement et l'énumération dans les lecteurs.|  
|<xref:System.IO.File?displayProperty=fullName>|Fournit des méthodes statiques pour la création, la copie, la suppression, le déplacement et l'ouverture de fichiers et permet de créer un `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=fullName>|Définit des constantes pour un accès en lecture, en écriture ou en lecture\/écriture à un fichier.|  
|<xref:System.IO.FileAttributes?displayProperty=fullName>|Fournit des attributs pour les fichiers et les répertoires tels que `Archive`, `Hidden` et `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=fullName>|Fournit des méthodes statiques pour la création, la copie, la suppression, le déplacement et l'ouverture de fichiers et permet de créer un `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=fullName>|Contrôle comment un fichier est ouvert.  Ce paramètre est spécifié dans de nombreux constructeurs pour `FileStream` et `IsolatedStorageFileStream` ainsi que pour les méthodes `Open` de <xref:System.IO.File> et de <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=fullName>|Définit des constantes pour le contrôle du type d'accès que d'autres flux de fichiers peuvent avoir sur le même fichier.|  
|<xref:System.IO.Path?displayProperty=fullName>|Fournit des méthodes et des propriétés pour le traitement des chaînes de répertoire.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>|Contrôle l'accès des fichiers et des dossiers en définissant les autorisations <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> et <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>.|  
  
## Classes utilisées pour créer des flux  
 Le tableau suivant répertorie et décrit les classes principales utilisées pour créer des flux.  
  
|Classe|Description|  
|------------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=fullName>|Ajoute une couche de mise en mémoire tampon aux opérations de lecture et d'écriture sur un autre flux.|  
|<xref:System.IO.FileStream?displayProperty=fullName>|Prend en charge l'accès aléatoire aux fichiers via la méthode <xref:System.IO.FileStream.Seek%2A>.  <xref:System.IO.FileStream> ouvre par défaut les fichiers de façon synchrone, mais prend également en charge les opérations asynchrones.|  
|<xref:System.IO.MemoryStream?displayProperty=fullName>|Crée un flux dont le magasin de stockage est une mémoire et non un fichier.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=fullName>|Fournit le flux de données sous\-jacent pour l'accès réseau.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=fullName>|Définit un flux qui lie les flux de données aux transformations de chiffrement.|  
  
## Classes utilisées pour lire et écrire dans des flux  
 Le tableau suivant affiche les classes spécifiques utilisées pour lire et écrire dans des fichiers avec des flux.  
  
|**Classe**|**Description**|  
|----------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=fullName>|Lit des chaînes encodées et des types de données primitifs à partir d'un <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=fullName>|Écrit des chaînes encodées et des types de données primitifs dans un <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=fullName>|Lit les caractères d'un <xref:System.IO.FileStream>, en utilisant <xref:System.IO.StreamReader.CurrentEncoding%2A> pour les convertir vers et depuis des octets.  <xref:System.IO.StreamReader> comporte un constructeur qui tente de déterminer le <xref:System.IO.StreamReader.CurrentEncoding%2A> approprié pour un flux donné, selon la présence d'un préambule spécifique à <xref:System.IO.StreamReader.CurrentEncoding%2A>, tel qu'une marque d'ordre d'octet.|  
|<xref:System.IO.StreamWriter?displayProperty=fullName>|Écrit des caractères dans un `FileStream`, à l'aide de <xref:System.IO.StreamWriter.Encoding%2A> pour convertir des caractères en octets.|  
|<xref:System.IO.StringReader?displayProperty=fullName>|Lit des caractères dans `String`.  La sortie peut être un flux de n'importe quel encodage ou un `String`.|  
|<xref:System.IO.StringWriter?displayProperty=fullName>|Écrit des caractères dans un `String`.  La sortie peut être un flux de n'importe quel encodage ou un `String`.|  
  
## Voir aussi  
 [Composition de flux](../Topic/Composing%20Streams.md)   
 [Fichier et flux de données E\/S](../Topic/File%20and%20Stream%20I-O.md)   
 [E\/S sur fichier asynchrones](../Topic/Asynchronous%20File%20I-O.md)   
 [Concepts de base du système de fichiers et des E\/S de fichier du .NET Framework \(Visual Basic\)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)