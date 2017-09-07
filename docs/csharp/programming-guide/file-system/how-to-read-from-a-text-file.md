---
title: Guide pratique pour lire un fichier texte (Guide de programmation C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- StreamReader.ReadToEnd
dev_langs:
- CSharp
helpviewer_keywords:
- text files, writing to
- reading text files
- reading data, text files
- text files, reading
ms.assetid: 92246c5b-e819-4eea-9370-1a9460e12de3
caps.latest.revision: 17
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
ms.openlocfilehash: bd0ad3e062c4d4b32fb6140cacba9a4a32674759
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a>Guide pratique pour lire un fichier texte (Guide de programmation C#)
Cet exemple lit le contenu d’un fichier texte à l’aide des méthodes statiques <xref:System.IO.File.ReadAllText%2A> et <xref:System.IO.File.ReadAllLines%2A> de la classe <xref:System.IO.File?displayProperty=fullName>.  
  
 Pour obtenir un exemple qui utilise <xref:System.IO.StreamReader>, consultez [Guide pratique pour lire un fichier texte ligne par ligne](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).  
  
> [!NOTE]
>  Les fichiers qui sont utilisés dans cet exemple sont créés dans la rubrique [Guide pratique pour écrire dans un fichier texte](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).  
  
## <a name="example"></a>Exemple  
 [!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez le code et collez-le dans une application console C#.  
  
 Si vous n’utilisez pas les fichiers texte de la rubrique [Guide pratique pour écrire dans un fichier texte](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), remplacez l’argument par `ReadAllText` et `ReadAllLines`, en fournissant le chemin et le nom correspondants sur votre ordinateur.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   Le fichier n’existe pas ou ne se trouve pas à l’emplacement spécifié. Vérifiez le chemin et l’orthographe du nom de fichier.  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Ne comptez pas sur le nom d’un fichier pour en déduire le contenu. Par exemple, le fichier `myFile.cs` peut ne pas être un fichier source C#.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.IO?displayProperty=fullName>   
 [Guide de programmation C#](../../../csharp/programming-guide/index.md)   
 [Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md)

