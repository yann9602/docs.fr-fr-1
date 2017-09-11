---
title: "Guide pratique pour écrire dans un fichier texte (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- TextWriter.WriteLine
- StreamWriter.Close
dev_langs:
- CSharp
helpviewer_keywords:
- files [C#], text files
- text, writing to files [C#]
ms.assetid: 2e99f184-d88b-4719-a7f1-d9ec482aa809
caps.latest.revision: 23
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
ms.openlocfilehash: 12a74a5664a8f514c89d9de3ce470c98319f84d2
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="e08b4-102">Guide pratique pour écrire dans un fichier texte (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e08b4-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="e08b4-103">Ces exemples montrent différentes manières d'écrire du texte dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="e08b4-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="e08b4-104">Les deux premiers exemples utilisent des méthodes pratiques statiques au niveau de la classe <xref:System.IO.File?displayProperty=fullName> pour écrire chaque élément de tout IEnumerable\<string> et une chaîne dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="e08b4-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=fullName> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="e08b4-105">L'exemple 3 indique comment ajouter du texte à un fichier quand vous devez traiter chaque ligne individuellement pendant que vous écrivez dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="e08b4-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="e08b4-106">Les exemples 1 à 3 remplacent tout le contenu existant dans le fichier, alors que l'exemple 4 montre comment ajouter du texte à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="e08b4-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="e08b4-107">Ces exemples écrivent tous des littéraux de chaîne dans les fichiers, mais il est plus probable que vous utilisiez la méthode <xref:System.String.Format%2A>, qui possède de nombreux contrôles pour écrire des types de valeurs différents justifiés à droite ou à gauche dans un champ, avec ou sans le remplissage, etc.</span><span class="sxs-lookup"><span data-stu-id="e08b4-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="e08b4-108">Vous pouvez également utiliser la fonctionnalité C# d’[interpolation de chaîne](../../../csharp/language-reference/keywords/interpolated-strings.md).</span><span class="sxs-lookup"><span data-stu-id="e08b4-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e08b4-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="e08b4-109">Example</span></span>  
 <span data-ttu-id="e08b4-110">[!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="e08b4-110">[!code-cs[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]</span></span>  
  
 <span data-ttu-id="e08b4-111">Ces exemples écrivent tous des littéraux de chaîne dans les fichiers, mais il est plus probable que vous utilisiez la méthode <xref:System.String.Format%2A>, qui possède de nombreux contrôles pour écrire des types de valeurs différents justifiés à droite ou à gauche dans un champ, avec ou sans le remplissage, etc.</span><span class="sxs-lookup"><span data-stu-id="e08b4-111">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="e08b4-112">Vous pouvez également utiliser la fonctionnalité C# d’[interpolation de chaîne](../../../csharp/language-reference/keywords/interpolated-strings.md).</span><span class="sxs-lookup"><span data-stu-id="e08b4-112">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e08b4-113">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e08b4-113">Robust Programming</span></span>  
 <span data-ttu-id="e08b4-114">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="e08b4-114">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e08b4-115">Le fichier existe déjà et est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="e08b4-115">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="e08b4-116">Le nom du chemin d'accès peut s'avérer trop long.</span><span class="sxs-lookup"><span data-stu-id="e08b4-116">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="e08b4-117">Le disque est peut-être plein.</span><span class="sxs-lookup"><span data-stu-id="e08b4-117">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e08b4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e08b4-118">See Also</span></span>  
 <span data-ttu-id="e08b4-119">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e08b4-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="e08b4-120">[Système de fichiers et Registre (Guide de programmation C#)](../../../csharp/programming-guide/file-system/index.md) </span><span class="sxs-lookup"><span data-stu-id="e08b4-120">[File System and the Registry (C# Programming Guide)](../../../csharp/programming-guide/file-system/index.md) </span></span>  
 [<span data-ttu-id="e08b4-121">Exemple : Enregistrer une collection sur un emplacement de stockage d’application</span><span class="sxs-lookup"><span data-stu-id="e08b4-121">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)

