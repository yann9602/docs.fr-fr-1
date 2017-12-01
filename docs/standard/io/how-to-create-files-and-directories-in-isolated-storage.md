---
title: "Comment : créer des fichiers et des répertoires dans un stockage isolé"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- directories [.NET Framework], isolated storage
- files [.NET Framework], isolated storage
- isolated storage, creating files and directories
- data stores, creating files and directories
- data storage using isolated storage, creating files and directories
- stores, creating files and directories
- storing data using isolated storage, creating files and directories
ms.assetid: 2ca4d2a4-809b-4f00-bc08-bf4a64d3a5c3
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8b8a48473bf9ac91b89657d00d27031255491353
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-files-and-directories-in-isolated-storage"></a>Comment : créer des fichiers et des répertoires dans un stockage isolé
Après avoir obtenu un magasin isolé, vous pouvez créer des répertoires et fichiers pour le stockage des données. Dans un magasin, les noms de fichiers et de répertoires sont spécifiés par rapport à la racine du système de fichiers virtuel.  
  
 Pour créer un répertoire, utilisez la <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A?displayProperty=nameWithType> méthode d’instance. Si vous spécifiez un sous-répertoire d’un répertoire qui n’existe pas, les deux répertoires sont créés. Si vous spécifiez un répertoire qui existe déjà, la méthode retourne sans création d’un répertoire, et aucune exception n’est levée. Toutefois, si vous spécifiez un nom de répertoire qui contient des caractères non valides, un <xref:System.IO.IsolatedStorage.IsolatedStorageException> exception est levée.  
  
 Pour créer un fichier, utilisez le <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateFile%2A?displayProperty=nameWithType> (méthode).  
  
 Dans le système d’exploitation Windows, un fichier de stockage isolé et le répertoire respectent pas la casse. Autrement dit, si vous créez un fichier nommé `ThisFile.txt`, puis créez un autre fichier nommé `THISFILE.TXT`, qu’un seul fichier est créé. Le nom de fichier conserve sa casse d’origine pour l’affichage.  
  
## <a name="example"></a>Exemple  
 L’exemple de code suivant illustre comment créer des fichiers et des répertoires dans un magasin isolé.  
  
 [!code-csharp[Conceptual.IsolatedStorage#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source.cs#1)]
 [!code-vb[Conceptual.IsolatedStorage#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source.vb#1)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream>  
 [Stockage isolé](../../../docs/standard/io/isolated-storage.md)
