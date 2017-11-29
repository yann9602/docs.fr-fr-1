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
# <a name="how-to-write-to-a-text-file-c-programming-guide"></a><span data-ttu-id="a4ec9-102">Guide pratique pour écrire dans un fichier texte (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a4ec9-102">How to: Write to a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="a4ec9-103">Ces exemples montrent différentes manières d'écrire du texte dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-103">These examples show various ways to write text to a file.</span></span>  <span data-ttu-id="a4ec9-104">Les deux premiers exemples utilisent des méthodes pratiques statiques au niveau de la classe <xref:System.IO.File?displayProperty=nameWithType> pour écrire chaque élément de tout IEnumerable\<string> et une chaîne dans un fichier texte.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-104">The first two examples use static convenience methods on the <xref:System.IO.File?displayProperty=nameWithType> class to write each element of any IEnumerable\<string> and a string to a text file.</span></span>  <span data-ttu-id="a4ec9-105">L'exemple 3 indique comment ajouter du texte à un fichier quand vous devez traiter chaque ligne individuellement pendant que vous écrivez dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-105">Example 3 shows how to add text to a file when you have to process each line individually as you write to the file.</span></span>  <span data-ttu-id="a4ec9-106">Les exemples 1 à 3 remplacent tout le contenu existant dans le fichier, alors que l'exemple 4 montre comment ajouter du texte à un fichier existant.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-106">Examples 1-3 overwrite all existing content in the file, but example 4 shows you how to append text to an existing file.</span></span>  
  
 <span data-ttu-id="a4ec9-107">Ces exemples écrivent tous des littéraux de chaîne dans les fichiers, mais il est plus probable que vous utilisiez la méthode <xref:System.String.Format%2A>, qui possède de nombreux contrôles pour écrire des types de valeurs différents justifiés à droite ou à gauche dans un champ, avec ou sans le remplissage, etc.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-107">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="a4ec9-108">Vous pouvez également utiliser la fonctionnalité C# d’[interpolation de chaîne](../../../csharp/language-reference/keywords/interpolated-strings.md).</span><span class="sxs-lookup"><span data-stu-id="a4ec9-108">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4ec9-109">Exemple</span><span class="sxs-lookup"><span data-stu-id="a4ec9-109">Example</span></span>  
 [!code-csharp[csFilesandFolders#3](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-write-to-a-text-file_1.cs)]  
  
 <span data-ttu-id="a4ec9-110">Ces exemples écrivent tous des littéraux de chaîne dans les fichiers, mais il est plus probable que vous utilisiez la méthode <xref:System.String.Format%2A>, qui possède de nombreux contrôles pour écrire des types de valeurs différents justifiés à droite ou à gauche dans un champ, avec ou sans le remplissage, etc.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-110">These examples all write string literals to files, but more likely you will want to use the <xref:System.String.Format%2A> method, which has many controls for writing different types of values  right or left justified in a field, with or without padding, and so on.</span></span>  <span data-ttu-id="a4ec9-111">Vous pouvez également utiliser la fonctionnalité C# d’[interpolation de chaîne](../../../csharp/language-reference/keywords/interpolated-strings.md).</span><span class="sxs-lookup"><span data-stu-id="a4ec9-111">You can also use the C# [string interpolation](../../../csharp/language-reference/keywords/interpolated-strings.md) feature.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="a4ec9-112">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="a4ec9-112">Robust Programming</span></span>  
 <span data-ttu-id="a4ec9-113">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="a4ec9-114">Le fichier existe déjà et est en lecture seule.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-114">The file exists and is read-only.</span></span>  
  
-   <span data-ttu-id="a4ec9-115">Le nom du chemin d'accès peut s'avérer trop long.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-115">The path name may be too long.</span></span>  
  
-   <span data-ttu-id="a4ec9-116">Le disque est peut-être plein.</span><span class="sxs-lookup"><span data-stu-id="a4ec9-116">The disk may be full.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ec9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4ec9-117">See Also</span></span>  
 [<span data-ttu-id="a4ec9-118">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="a4ec9-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a4ec9-119">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="a4ec9-119">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)  
 [<span data-ttu-id="a4ec9-120">Exemple : Enregistrer une collection sur un emplacement de stockage d’application</span><span class="sxs-lookup"><span data-stu-id="a4ec9-120">Sample: Save a collection to Application Storage</span></span>](http://code.msdn.microsoft.com/CSWinStoreAppSaveCollection-bed5d6e6)
