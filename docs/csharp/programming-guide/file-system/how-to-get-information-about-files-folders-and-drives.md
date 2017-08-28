---
title: "Guide pratique pour obtenir des informations sur les fichiers, dossiers et lecteurs (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- files [C#], getting information about
ms.assetid: 22fc2da6-5494-405b-995e-c0b99142a93e
caps.latest.revision: 30
author: BillWagner
ms.author: wiwagn
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
ms.openlocfilehash: 6067ea9d51c31c9398c7b1fcd83ca8fa3a4fec76
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-get-information-about-files-folders-and-drives--c-programming-guide"></a>Guide pratique pour obtenir des informations sur les fichiers, dossiers et lecteurs (Guide de programmation C#)
Dans le .NET Framework, vous pouvez accéder aux informations sur le système de fichiers en utilisant les classes suivantes :  
  
-   <xref:System.IO.FileInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DirectoryInfo?displayProperty=fullName>  
  
-   <xref:System.IO.DriveInfo?displayProperty=fullName>  
  
-   <xref:System.IO.Directory?displayProperty=fullName>  
  
-   <xref:System.IO.File?displayProperty=fullName>  
  
 Les classes <xref:System.IO.FileInfo> et <xref:System.IO.DirectoryInfo> représentent un fichier ou un répertoire. Elles contiennent des propriétés qui exposent une grande partie des attributs de fichiers pris en charge par le système de fichiers NTFS. Elles contiennent également des méthodes pour ouvrir, fermer, déplacer et supprimer des fichiers et dossiers. Vous pouvez créer des instances de ces classes en passant une chaîne qui représente le nom du fichier, dossier ou lecteur dans le constructeur :  
  
```csharp  
System.IO.DriveInfo di = new System.IO.DriveInfo(@"C:\");  
```  
  
 Vous pouvez aussi obtenir les noms des fichiers, dossiers ou lecteurs en appelant <xref:System.IO.DirectoryInfo.GetDirectories%2A?displayProperty=fullName>, <xref:System.IO.DirectoryInfo.GetFiles%2A?displayProperty=fullName> et <xref:System.IO.DriveInfo.RootDirectory%2A?displayProperty=fullName>.  
  
 Les classes <xref:System.IO.Directory?displayProperty=fullName> et <xref:System.IO.File?displayProperty=fullName> fournissent des méthodes statiques pour récupérer des informations sur les répertoires et les fichiers.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant illustre différentes manières d’accéder aux informations sur les fichiers et dossiers.  
  
 [!code-cs[csFilesandFolders#6](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-get-information-about-files-folders-and-drives_1.cs)]  
  
## <a name="robust-programming"></a>Programmation fiable  
 Quand vous traitez des chaînes de chemin spécifiées par l’utilisateur, vous devez également gérer les exceptions dans les cas suivants :  
  
-   Le nom de fichier est mal formé. Par exemple, il contient des caractères non valides ou uniquement des espaces blancs.  
  
-   Le nom de fichier est null.  
  
-   Le nom de fichier est plus long que la longueur maximale définie par le système.  
  
-   Le nom de fichier contient un signe deux-points (:).  
  
 Si l’application ne dispose pas des autorisations suffisantes pour lire le fichier spécifié, la méthode `Exists` retourne `false` indépendamment de l’existence d’un chemin. La méthode ne lève pas d’exception.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)

