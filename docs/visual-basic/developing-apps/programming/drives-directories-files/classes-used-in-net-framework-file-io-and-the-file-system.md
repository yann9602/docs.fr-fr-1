---
title: "Classes utilisées dans les E/S de fichier du .NET Framework et le système de fichiers (Visual Basic)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- file I/O classes
ms.assetid: 4a5ca924-eea8-4a95-a5f0-6ac10de276a3
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a87d2e6f87b92b5f66706095d3f485c080008e0f
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="classes-used-in-net-framework-file-io-and-the-file-system-visual-basic"></a>Classes utilisées dans les E/S de fichier du .NET Framework et le système de fichiers (Visual Basic)
Les tableaux suivants répertorient les classes couramment utilisées pour les E/S de fichier du .NET Framework. Ces classes sont réparties dans les catégories suivantes : classes d’E/S de fichier, classes utilisées pour créer des flux et classes utilisées pour lire et écrire dans les flux.  
  
 Pour accéder à la documentation du [!INCLUDE[dnprdnlong](~/includes/dnprdnlong-md.md)] et obtenir une liste plus complète, consultez [Vue d’ensemble de la bibliothèque de classes](https://msdn.microsoft.com/library/hfa3fa08).  
  
## <a name="basic-io-classes-for-files-drives-and-directories"></a>Classes d’E/S de base pour les fichiers, les lecteurs et les répertoires  
 Le tableau suivant répertorie et décrit les principales classes utilisées pour les E/S de fichier.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.IO.Directory?displayProperty=fullName>|Fournit des méthodes statiques pour la création, le déplacement et l’énumération dans les répertoires et les sous-répertoires.|  
|<xref:System.IO.DirectoryInfo?displayProperty=fullName>|Fournit des méthodes d’instance pour la création, le déplacement et l’énumération dans les répertoires et les sous-répertoires.|  
|<xref:System.IO.DriveInfo?displayProperty=fullName>|Fournit des méthodes d’instance pour la création, le déplacement et l’énumération dans les lecteurs.|  
|<xref:System.IO.File?displayProperty=fullName>|Fournit des méthodes statiques pour la création, la copie, la suppression, le déplacement et l’ouverture de fichiers, et facilite la création d’objets `FileStream`.|  
|<xref:System.IO.FileAccess?displayProperty=fullName>|Définit des constantes pour l’accès en lecture, en écriture ou en lecture/écriture à un fichier.|  
|<xref:System.IO.FileAttributes?displayProperty=fullName>|Fournit des attributs pour les fichiers et répertoires, tels que `Archive`, `Hidden` et `ReadOnly`.|  
|<xref:System.IO.FileInfo?displayProperty=fullName>|Fournit des méthodes statiques pour la création, la copie, la suppression, le déplacement et l’ouverture de fichiers, et facilite la création d’objets `FileStream`.|  
|<xref:System.IO.FileMode?displayProperty=fullName>|Contrôle l’ouverture d’un fichier. Ce paramètre est spécifié dans de nombreux constructeurs pour `FileStream` et `IsolatedStorageFileStream`, ainsi que pour les méthodes `Open` de <xref:System.IO.File> et <xref:System.IO.FileInfo>.|  
|<xref:System.IO.FileShare?displayProperty=fullName>|Définit des constantes pour le contrôle du type d’accès que d’autres flux de fichiers peuvent avoir sur le même fichier.|  
|<xref:System.IO.Path?displayProperty=fullName>|Fournit des méthodes et des propriétés pour le traitement des chaînes de répertoire.|  
|<xref:System.Security.Permissions.FileIOPermission?displayProperty=fullName>|Contrôle l’accès des fichiers et des dossiers en définissant les autorisations <xref:System.Security.Permissions.FileIOPermissionAttribute.Read%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Write%2A>, <xref:System.Security.Permissions.FileIOPermissionAttribute.Append%2A> et <xref:System.Security.Permissions.FileIOPermissionAttribute.PathDiscovery%2A>.|  
  
## <a name="classes-used-to-create-streams"></a>Classes utilisées pour créer des flux  
 Le tableau suivant répertorie et décrit les principales classes utilisées pour créer des flux.  
  
|Classe|Description|  
|-----------|-----------------|  
|<xref:System.IO.BufferedStream?displayProperty=fullName>|Ajoute une couche de mise en mémoire tampon aux opérations de lecture et d’écriture sur un autre flux.|  
|<xref:System.IO.FileStream?displayProperty=fullName>|Prend en charge l’accès aléatoire aux fichiers par le biais de sa méthode <xref:System.IO.FileStream.Seek%2A>. <xref:System.IO.FileStream> ouvre par défaut les fichiers de façon synchrone, mais prend également en charge les opérations asynchrones.|  
|<xref:System.IO.MemoryStream?displayProperty=fullName>|Crée un flux dont le magasin de stockage est une mémoire et non un fichier.|  
|<xref:System.Net.Sockets.NetworkStream?displayProperty=fullName>|Fournit le flux de données sous-jacent pour l’accès réseau.|  
|<xref:System.Security.Cryptography.CryptoStream?displayProperty=fullName>|Définit un flux qui lie les flux de données aux transformations par chiffrement.|  
  
## <a name="classes-used-to-read-from-and-write-to-streams"></a>Classes utilisées pour lire et écrire dans des flux  
 Le tableau suivant répertorie les classes spécifiques utilisées pour lire et écrire dans des fichiers avec des flux.  
  
|**Classe**|**Description**|  
|---------------|---------------------|  
|<xref:System.IO.BinaryReader?displayProperty=fullName>|Lit des chaînes encodées et des types de données primitifs à partir d’un <xref:System.IO.FileStream>.|  
|<xref:System.IO.BinaryWriter?displayProperty=fullName>|Écrit des chaînes encodées et des types de données primitifs dans un <xref:System.IO.FileStream>.|  
|<xref:System.IO.StreamReader?displayProperty=fullName>|Lit les caractères d’un <xref:System.IO.FileStream>, en utilisant <xref:System.IO.StreamReader.CurrentEncoding%2A> pour convertir des caractères en octets et des octets en caractères. <xref:System.IO.StreamReader> a un constructeur qui tente de déterminer le <xref:System.IO.StreamReader.CurrentEncoding%2A> correct pour un flux donné, en fonction de la présence d’un préambule propre à <xref:System.IO.StreamReader.CurrentEncoding%2A>, tel qu’une marque d’ordre d’octet.|  
|<xref:System.IO.StreamWriter?displayProperty=fullName>|Écrit des caractères dans un `FileStream`, en utilisant <xref:System.IO.StreamWriter.Encoding%2A> pour convertir des caractères en octets.|  
|<xref:System.IO.StringReader?displayProperty=fullName>|Lit des caractères dans un `String`. La sortie peut être un flux de n’importe quel encodage ou un `String`.|  
|<xref:System.IO.StringWriter?displayProperty=fullName>|Écrit des caractères dans un `String`. La sortie peut être un flux de n’importe quel encodage ou un `String`.|  
  
## <a name="see-also"></a>Voir aussi  
 [Composition de flux](https://msdn.microsoft.com/library/e4y2dch9)   
 [E/S de fichier et de flux](https://msdn.microsoft.com/library/k3352a4t)   
 [E/S sur fichier asynchrones](https://msdn.microsoft.com/library/kztecsys)   
 [Concepts de base du système de fichiers et des E/S de fichier du .NET Framework (Visual Basic)](../../../../visual-basic/developing-apps/programming/drives-directories-files/basics-of-net-framework-file-io-and-the-file-system.md)

