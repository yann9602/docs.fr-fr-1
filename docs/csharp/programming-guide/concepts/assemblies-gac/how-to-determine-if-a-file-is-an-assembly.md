---
title: "Guide pratique pour déterminer si un fichier est un assembly (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ea5186bb-5bff-4dcb-bde9-d6ba4e2edd00
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ee402e28374040ab22173788dce421345b2ef3b5
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a><span data-ttu-id="feaaf-102">Guide pratique pour déterminer si un fichier est un assembly (C#)</span><span class="sxs-lookup"><span data-stu-id="feaaf-102">How to: Determine If a File Is an Assembly (C#)</span></span>
<span data-ttu-id="feaaf-103">Un fichier est un assembly si et seulement s’il est managé et s’il contient une entrée d’assembly dans ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="feaaf-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="feaaf-104">Pour plus d’informations sur les assemblys et les métadonnées, consultez la rubrique [Manifeste d’assembly](https://msdn.microsoft.com/library/1w45z383).</span><span class="sxs-lookup"><span data-stu-id="feaaf-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="feaaf-105">Comment déterminer manuellement si un fichier est un assembly</span><span class="sxs-lookup"><span data-stu-id="feaaf-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="feaaf-106">Démarrez [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span><span class="sxs-lookup"><span data-stu-id="feaaf-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="feaaf-107">Chargez le fichier que vous souhaitez tester.</span><span class="sxs-lookup"><span data-stu-id="feaaf-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="feaaf-108">Si **ILDASM** indique que le fichier n’est pas un fichier exécutable portable (PE), alors il ne s’agit pas d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="feaaf-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="feaaf-109">Pour plus d’informations, consultez la rubrique [Guide pratique pour afficher le contenu d’un assembly](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span><span class="sxs-lookup"><span data-stu-id="feaaf-109">For more information, see the topic [How to: View Assembly Contents](../../../../framework/app-domains/how-to-view-assembly-contents.md).</span></span>  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="feaaf-110">Comment déterminer par programmation si un fichier est un assembly</span><span class="sxs-lookup"><span data-stu-id="feaaf-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="feaaf-111">Appelez la méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> en passant le chemin complet et le nom du fichier que vous testez.</span><span class="sxs-lookup"><span data-stu-id="feaaf-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="feaaf-112">Si une exception <xref:System.BadImageFormatException> est levée, le fichier n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="feaaf-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="feaaf-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="feaaf-113">Example</span></span>  
 <span data-ttu-id="feaaf-114">Cet exemple teste une DLL pour voir s’il s’agit d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="feaaf-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```  
class TestAssembly  
{  
    static void Main()  
    {  
  
        try  
        {  
            System.Reflection.AssemblyName testAssembly =  
                System.Reflection.AssemblyName.GetAssemblyName(@"C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll");  
  
            System.Console.WriteLine("Yes, the file is an assembly.");  
        }  
  
        catch (System.IO.FileNotFoundException)  
        {  
            System.Console.WriteLine("The file cannot be found.");  
        }  
  
        catch (System.BadImageFormatException)  
        {  
            System.Console.WriteLine("The file is not an assembly.");  
        }  
  
        catch (System.IO.FileLoadException)  
        {  
            System.Console.WriteLine("The assembly has already been loaded.");  
        }  
    }  
}  
/* Output (with .NET Framework 3.5 installed):  
    Yes, the file is an assembly.  
*/  
```  
  
 <span data-ttu-id="feaaf-115">La méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> charge le fichier de test, puis le libère une fois que les informations sont lues.</span><span class="sxs-lookup"><span data-stu-id="feaaf-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feaaf-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="feaaf-116">See Also</span></span>  
 <span data-ttu-id="feaaf-117"><xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="feaaf-117"><xref:System.Reflection.AssemblyName></span></span>   
 <span data-ttu-id="feaaf-118">[Guide de programmation C#](../../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="feaaf-118">[C# Programming Guide](../../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="feaaf-119">Assemblys et le Global Assembly Cache (C#)</span><span class="sxs-lookup"><span data-stu-id="feaaf-119">Assemblies and the Global Assembly Cache (C#)</span></span>](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)

