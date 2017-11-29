---
title: "Guide pratique pour écrire dans un fichier texte (Guide de programmation C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c576536947cdb4984d6e5ce67c8377fe23b354c7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a>Guide pratique pour écrire dans un fichier texte (Guide de programmation C#)
Ces exemples montrent différentes manières d'écrire du texte dans un fichier.  Les deux premiers exemples utilisent des méthodes pratiques statiques au niveau de la classe <xref:System.IO.File?displayProperty=nameWithType> pour écrire chaque élément de tout IEnumerable\<string> et une chaîne dans un fichier texte.  L'exemple 3 indique comment ajouter du texte à un fichier quand vous devez traiter chaque ligne individuellement pendant que vous écrivez dans le fichier.  Les exemples 1 à 3 remplacent tout le contenu existant dans le fichier, alors que l'exemple 4 montre comment ajouter du texte à un fichier existant.  
  
 Ces exemples écrivent tous des littéraux de chaîne dans les fichiers, mais il est plus probable que vous utilisiez la méthode <xref:System.String.Format%2A>, qui possède de nombreux contrôles pour écrire des types de valeurs différents justifiés à droite ou à gauche dans un champ, avec ou sans le remplissage, etc.  Vous pouvez également utiliser la fonctionnalité C# d’[interpolation de chaîne](../../../csharp/language-reference/keywords/interpolated-strings.md).  
  
## <a name="example"></a>Exemple  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 Ces exemples écrivent tous des littéraux de chaîne dans les fichiers, mais il est plus probable que vous utilisiez la méthode <xref:System.String.Format%2A>, qui possède de nombreux contrôles pour écrire des types de valeurs différents justifiés à droite ou à gauche dans un champ, avec ou sans le remplissage, etc.  Vous pouvez également utiliser la fonctionnalité C# d’[interpolation de chaîne](../../../csharp/language-reference/keywords/interpolated-strings.md).  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le fichier existe déjà et est en lecture seule.  
  
-   Le nom du chemin d'accès peut s'avérer trop long.  
  
-   Le disque est peut-être plein.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)  
 [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)  
 [Exemple : Enregistrer une collection sur un emplacement de stockage d’application](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
