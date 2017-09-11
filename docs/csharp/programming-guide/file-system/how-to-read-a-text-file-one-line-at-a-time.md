---
title: Guide pratique pour lire un fichier texte ligne par ligne (Visual C#)
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ReadLine method [C#]
- reading text files, line by line
- text files [C#]
ms.assetid: d62e22c5-a13c-48db-af9b-f10c801b0cb1
caps.latest.revision: 11
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
ms.openlocfilehash: e9327181d82a97559c7be99bb76a2a93118d796b
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-read-a-text-file-one-line-at-a-time-visual-c"></a><span data-ttu-id="e1909-102">Guide pratique pour lire un fichier texte ligne par ligne (Visual C#)</span><span class="sxs-lookup"><span data-stu-id="e1909-102">How to: Read a Text File One Line at a Time (Visual C#)</span></span>
<span data-ttu-id="e1909-103">Cet exemple lit le contenu d’une chaîne d’un fichier texte, ligne par ligne, à l’aide de la méthode `ReadLine` de la classe `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="e1909-103">This example reads the contents of a text file, one line at a time, into a string using the `ReadLine` method of the `StreamReader` class.</span></span> <span data-ttu-id="e1909-104">Chaque ligne de texte est stockée dans la chaîne `line` et s’affiche à l’écran.</span><span class="sxs-lookup"><span data-stu-id="e1909-104">Each text line is stored into the string `line` and displayed on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1909-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="e1909-105">Example</span></span>  
  
```  
int counter = 0;  
string line;  
  
// Read the file and display it line by line.  
System.IO.StreamReader file =   
    new System.IO.StreamReader(@"c:\test.txt");  
while((line = file.ReadLine()) != null)  
{  
    System.Console.WriteLine (line);  
    counter++;  
}  
  
file.Close();  
System.Console.WriteLine("There were {0} lines.", counter);  
// Suspend the screen.  
System.Console.ReadLine();  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1909-106">Compilation du code</span><span class="sxs-lookup"><span data-stu-id="e1909-106">Compiling the Code</span></span>  
 <span data-ttu-id="e1909-107">Copiez le code et collez-le dans la méthode `Main` d’une application console.</span><span class="sxs-lookup"><span data-stu-id="e1909-107">Copy the code and paste it into the `Main` method of a console application.</span></span>  
  
 <span data-ttu-id="e1909-108">Remplacez `"c:\test.txt"` par le nom du fichier.</span><span class="sxs-lookup"><span data-stu-id="e1909-108">Replace `"c:\test.txt"` with the actual file name.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e1909-109">Programmation fiable</span><span class="sxs-lookup"><span data-stu-id="e1909-109">Robust Programming</span></span>  
 <span data-ttu-id="e1909-110">Les conditions ci-dessous peuvent générer une exception.</span><span class="sxs-lookup"><span data-stu-id="e1909-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="e1909-111">Le fichier n’existe pas.</span><span class="sxs-lookup"><span data-stu-id="e1909-111">The file may not exist.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="e1909-112">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e1909-112">.NET Framework Security</span></span>  
 <span data-ttu-id="e1909-113">Ne vous basez pas sur le nom d'un fichier pour en déterminer le contenu.</span><span class="sxs-lookup"><span data-stu-id="e1909-113">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e1909-114">Par exemple, le fichier `myFile.cs` peut ne pas être un fichier source C#.</span><span class="sxs-lookup"><span data-stu-id="e1909-114">For example, the file `myFile.cs` may not be a C# source file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1909-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1909-115">See Also</span></span>  
 <span data-ttu-id="e1909-116"><xref:System.IO?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="e1909-116"><xref:System.IO?displayProperty=fullName></span></span>   
 <span data-ttu-id="e1909-117">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="e1909-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="e1909-118">Système de fichiers et Registre (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="e1909-118">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)

