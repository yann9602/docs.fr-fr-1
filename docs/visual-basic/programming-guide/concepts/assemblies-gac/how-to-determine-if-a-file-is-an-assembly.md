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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2e58363369ae4420879310bf09ed89cdd4f5b5cc
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-visual-basic"></a>Comment : déterminer si un fichier est un Assembly (Visual Basic)
Un fichier est un assembly si et seulement si elle est gérée et contient une entrée d’assembly dans ses métadonnées. Pour plus d’informations sur les assemblys et les métadonnées, consultez la rubrique [manifeste d’Assembly](https://msdn.microsoft.com/library/1w45z383).  
  
## <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Comment déterminer manuellement si un fichier est un assembly  
  
1.  Démarrer le [Ildasm.exe (désassembleur IL)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Charger le fichier que vous souhaitez tester.  
  
3.  Si **ILDASM** rapports que le fichier n’est pas un fichier exécutable portable (PE), puis il n’est pas un assembly. Pour plus d’informations, consultez la rubrique [Comment : afficher le contenu Assembly](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).  
  
## <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Comment déterminer par programme si un fichier est un assembly  
  
1.  Appelez le <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>méthode, en passant le chemin d’accès complet et le nom du fichier que vous testez.</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>  
  
2.  Si un <xref:System.BadImageFormatException>exception est levée, le fichier n’est pas un assembly.</xref:System.BadImageFormatException>  
  
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
  
 Le <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>méthode charge le fichier de test, puis le libère une fois les informations sont lues.</xref:System.Reflection.AssemblyName.GetAssemblyName%2A>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection.AssemblyName></xref:System.Reflection.AssemblyName>   
 [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)   
 [Assemblys et le Global Assembly Cache (Visual Basic)](index.md)
