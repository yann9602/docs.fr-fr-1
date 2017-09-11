---
title: "Comment : déterminer si un fichier est un Assembly (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 4bd3404cbdc3b79ff92290a53574080bf197fe9d
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a><span data-ttu-id="f3a35-102">Comment : déterminer si un fichier est un Assembly (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f3a35-102">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>
<span data-ttu-id="f3a35-103">Un fichier est un assembly si et seulement si elle est gérée et contient une entrée d’assembly dans ses métadonnées.</span><span class="sxs-lookup"><span data-stu-id="f3a35-103">A file is an assembly if and only if it is managed, and contains an assembly entry in its metadata.</span></span> <span data-ttu-id="f3a35-104">Pour plus d’informations sur les assemblys et les métadonnées, consultez la rubrique [manifeste d’Assembly](https://msdn.microsoft.com/library/1w45z383).</span><span class="sxs-lookup"><span data-stu-id="f3a35-104">For more information on assemblies and metadata, see the topic [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="f3a35-105">Comment déterminer manuellement si un fichier est un assembly</span><span class="sxs-lookup"><span data-stu-id="f3a35-105">How to manually determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="f3a35-106">Démarrer le [Ildasm.exe (désassembleur IL)](https://msdn.microsoft.com/library/f7dy01k1).</span><span class="sxs-lookup"><span data-stu-id="f3a35-106">Start the [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).</span></span>  
  
2.  <span data-ttu-id="f3a35-107">Charger le fichier que vous souhaitez tester.</span><span class="sxs-lookup"><span data-stu-id="f3a35-107">Load the file you wish to test.</span></span>  
  
3.  <span data-ttu-id="f3a35-108">Si **ILDASM** rapports que le fichier n’est pas un fichier exécutable portable (PE), puis il n’est pas un assembly.</span><span class="sxs-lookup"><span data-stu-id="f3a35-108">If **ILDASM** reports that the file is not a portable executable (PE) file, then it is not an assembly.</span></span> <span data-ttu-id="f3a35-109">Pour plus d’informations, consultez la rubrique [Comment : afficher le contenu Assembly](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).</span><span class="sxs-lookup"><span data-stu-id="f3a35-109">For more information, see the topic [How to: View Assembly Contents](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).</span></span>  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a><span data-ttu-id="f3a35-110">Comment déterminer par programme si un fichier est un assembly</span><span class="sxs-lookup"><span data-stu-id="f3a35-110">How to programmatically determine if a file is an assembly</span></span>  
  
1.  <span data-ttu-id="f3a35-111">Appelez le <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>méthode, en passant le chemin d’accès complet et le nom du fichier que vous testez.</xref:System.Reflection.AssemblyName.GetAssemblyName%2A></span><span class="sxs-lookup"><span data-stu-id="f3a35-111">Call the <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method, passing the full file path and name of the file you are testing.</span></span>  
  
2.  <span data-ttu-id="f3a35-112">Si un <xref:System.BadImageFormatException>exception est levée, le fichier n’est pas un assembly.</xref:System.BadImageFormatException></span><span class="sxs-lookup"><span data-stu-id="f3a35-112">If a <xref:System.BadImageFormatException> exception is thrown, the file is not an assembly.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3a35-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="f3a35-113">Example</span></span>  
 <span data-ttu-id="f3a35-114">Cet exemple teste une DLL pour voir s’il s’agit d’un assembly.</span><span class="sxs-lookup"><span data-stu-id="f3a35-114">This example tests a DLL to see if it is an assembly.</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Try  
            Dim testAssembly As Reflection.AssemblyName =  
                                Reflection.AssemblyName.GetAssemblyName("C:\Windows\Microsoft.NET\Framework\v3.5\System.Net.dll")  
            Console.WriteLine("Yes, the file is an Assembly.")  
        Catch ex As System.IO.FileNotFoundException  
            Console.WriteLine("The file cannot be found.")  
        Catch ex As System.BadImageFormatException  
            Console.WriteLine("The file is not an Assembly.")  
        Catch ex As System.IO.FileLoadException  
            Console.WriteLine("The Assembly has already been loaded.")  
        End Try  
        Console.ReadLine()  
    End Sub  
End Module  
' Output (with .NET Framework 3.5 installed):  
'        Yes, the file is an Assembly.  
```
  
 <span data-ttu-id="f3a35-115">Le <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>méthode charge le fichier de test, puis le libère une fois les informations sont lues.</xref:System.Reflection.AssemblyName.GetAssemblyName%2A></span><span class="sxs-lookup"><span data-stu-id="f3a35-115">The <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> method loads the test file, and then releases it once the information is read.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a35-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f3a35-116">See Also</span></span>  
 <span data-ttu-id="f3a35-117"><xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName></span><span class="sxs-lookup"><span data-stu-id="f3a35-117"><xref:System.Reflection.AssemblyName></span></span>   
<span data-ttu-id="f3a35-118"> [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md) </span><span class="sxs-lookup"><span data-stu-id="f3a35-118"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md) </span></span>  
<span data-ttu-id="f3a35-119"> [Assemblys et le Global Assembly Cache (Visual Basic)](index.md)</span><span class="sxs-lookup"><span data-stu-id="f3a35-119"> [Assemblies and the Global Assembly Cache (Visual Basic)](index.md)</span></span>
