---
title: "Comment : déterminer si un fichier est un Assembly (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de26f410-9bd1-4b55-a343-cc82f81684be
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0930b6504306efd7dfaf019e090a6d1212c65657
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Comment : déterminer si un fichier est un Assembly (Visual Basic)
Un fichier est un assembly si et seulement s’il est managé et s’il contient une entrée d’assembly dans ses métadonnées. Pour plus d’informations sur les assemblys et les métadonnées, consultez la rubrique [Manifeste d’assembly](../../../../framework/app-domains/assembly-manifest.md).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Comment déterminer manuellement si un fichier est un assembly  
  
1.  Démarrez [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Chargez le fichier que vous souhaitez tester.  
  
3.  Si **ILDASM** indique que le fichier n’est pas un fichier exécutable portable (PE), alors il ne s’agit pas d’un assembly. Pour plus d’informations, consultez la rubrique [Guide pratique pour afficher le contenu d’un assembly](../../../../framework/app-domains/how-to-view-assembly-contents.md).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Comment déterminer par programmation si un fichier est un assembly  
  
1.  Appelez la méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> en passant le chemin complet et le nom du fichier que vous testez.  
  
2.  Si une exception <xref:System.BadImageFormatException> est levée, le fichier n’est pas un assembly.  
  
## <a name="example"></a>Exemple  
 Cet exemple teste une DLL pour voir s’il s’agit d’un assembly.  
  
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
  
 La méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A> charge le fichier de test, puis le libère une fois que les informations sont lues.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection.AssemblyName>  
 [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)  
 [Assemblys et le Global Assembly Cache (Visual Basic)](index.md)
