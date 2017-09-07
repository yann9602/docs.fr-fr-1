---
title: "Guide pratique pour copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 13
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
ms.openlocfilehash: a4cfec46e0af0056a0de20a1ed83a370cd010055
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a>Guide pratique pour copier, supprimer et déplacer des fichiers et dossiers (Guide de programmation C#)
Les exemples suivants montrent comment copier, déplacer et supprimer des fichiers et dossiers de manière synchrone à l’aide des classes <xref:System.IO.File?displayProperty=fullName>, <xref:System.IO.Directory?displayProperty=fullName>, <xref:System.IO.FileInfo?displayProperty=fullName> et <xref:System.IO.DirectoryInfo?displayProperty=fullName> à partir de l’espace de noms <xref:System.IO?displayProperty=fullName>. Ces exemples ne fournissent pas de barre de progression ou autre interface utilisateur. Si vous souhaitez fournir une boîte de dialogue de progression standard, consultez [Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers](how-to-provide-a-progress-dialog-box-for-file-operations.md).  
  
 Utilisez <xref:System.IO.FileSystemWatcher?displayProperty=fullName> pour fournir des événements qui vous permettent de calculer la progression quand vous travaillez sur plusieurs fichiers. Une autre approche consiste à utiliser l’appel de code non managé pour appeler les méthodes pertinentes relatives aux fichiers dans le shell Windows. Pour plus d’informations sur la façon d’effectuer ces opérations sur les fichiers de façon asynchrone, consultez [E/S de fichiers asynchrones](https://msdn.microsoft.com/library/kztecsys).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment copier des fichiers et des répertoires.  
  
 [!code-cs[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment déplacer des fichiers et des répertoires.  
  
 [!code-cs[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a>Exemple  
 L’exemple suivant montre comment supprimer des fichiers et des répertoires.  
  
 [!code-cs[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre (Guide de programmation C#)](index.md)   
 [Guide pratique pour fournir une boîte de dialogue de progression pour les opérations sur les fichiers](how-to-provide-a-progress-dialog-box-for-file-operations.md)   
 [E/S de fichier et de flux](https://msdn.microsoft.com/library/k3352a4t)   
 [Tâches d’E/S courantes](https://msdn.microsoft.com/library/ms404278)

