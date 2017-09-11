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
# <a name="how-to-read-from-a-text-file-c-programming-guide"></a><span data-ttu-id="3d710-102">Guide pratique pour lire un fichier texte (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3d710-102">How to: Read From a Text File (C# Programming Guide)</span></span>
<span data-ttu-id="3d710-103">Cet exemple lit le contenu d’un fichier texte à l’aide des méthodes statiques <xref:System.IO.File.ReadAllText%2A> et <xref:System.IO.File.ReadAllLines%2A> de la classe <xref:System.IO.File?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="3d710-103">This example reads the contents of a text file by using the static methods <xref:System.IO.File.ReadAllText%2A> and <xref:System.IO.File.ReadAllLines%2A> from the <xref:System.IO.File?displayProperty=fullName> class.</span></span>  
  
 <span data-ttu-id="3d710-104">Pour obtenir un exemple qui utilise <xref:System.IO.StreamReader>, consultez [Guide pratique pour lire un fichier texte ligne par ligne](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span><span class="sxs-lookup"><span data-stu-id="3d710-104">For an example that uses <xref:System.IO.StreamReader>, see [How to: Read a Text File One Line at a Time](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d710-105">Les fichiers qui sont utilisés dans cet exemple sont créés dans la rubrique [Guide pratique pour écrire dans un fichier texte](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span><span class="sxs-lookup"><span data-stu-id="3d710-105">The files that are used in this example are created in the topic [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d710-106">Exemple</span><span class="sxs-lookup"><span data-stu-id="3d710-106">Example</span></span>  
 <span data-ttu-id="3d710-107">[!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="3d710-107">[!code-cs[csFilesandFolders#4](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-read-from-a-text-file_1.cs)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3d710-108">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="3d710-108">Compiling the Code</span></span>  
 <span data-ttu-id="3d710-109">Copiez le code et collez-le dans une application console C#.</span><span class="sxs-lookup"><span data-stu-id="3d710-109">Copy the code and paste it into a C# console application.</span></span>  
  
 <span data-ttu-id="3d710-110">Si vous n’utilisez pas les fichiers texte de la rubrique [Guide pratique pour écrire dans un fichier texte](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), remplacez l’argument par `ReadAllText` et `ReadAllLines`, en fournissant le chemin et le nom correspondants sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="3d710-110">If you are not using the text files from [How to: Write to a Text File](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md), replace the argument to `ReadAllText` and `ReadAllLines` with the appropriate path and file name on your computer.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3d710-111">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="3d710-111">Robust Programming</span></span>  
 <span data-ttu-id="3d710-112">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="3d710-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3d710-113">Le fichier n’existe pas ou ne se trouve pas à l’emplacement spécifié.</span><span class="sxs-lookup"><span data-stu-id="3d710-113">The file doesn't exist or doesn't exist at the specified location.</span></span> <span data-ttu-id="3d710-114">Vérifiez le chemin et l’orthographe du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="3d710-114">Check the path and the spelling of the file name.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="3d710-115">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3d710-115">.NET Framework Security</span></span>  
 <span data-ttu-id="3d710-116">Ne comptez pas sur le nom d’un fichier pour en déduire le contenu.</span><span class="sxs-lookup"><span data-stu-id="3d710-116">Do not rely on the name of a file to determine the contents of the file.</span></span> <span data-ttu-id="3d710-117">Par exemple, le fichier `myFile.cs` peut ne pas être un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="3d710-117">For example, the file `myFile.cs` might not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d710-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3d710-118">See Also</span></span>  
 <span data-ttu-id="3d710-119"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="3d710-119"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="3d710-120">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="3d710-120">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="3d710-121">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="3d710-121">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)

