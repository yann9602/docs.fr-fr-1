---
title: "Guide pratique pour déterminer si un fichier est un assembly (C#) | Microsoft Docs"
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 4de303da9215fb07ecbb6bfff78d18dcd246aad3
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-determine-if-a-file-is-an-assembly-c"></a>Guide pratique pour déterminer si un fichier est un assembly (C#)
Un fichier est un assembly si et seulement s’il est managé et s’il contient une entrée d’assembly dans ses métadonnées. Pour plus d’informations sur les assemblys et les métadonnées, consultez la rubrique [Manifeste d’assembly](https://msdn.microsoft.com/library/1w45z383).  
  
### <a name="how-to-manually-determine-if-a-file-is-an-assembly"></a>Comment déterminer manuellement si un fichier est un assembly  
  
1.  Démarrez [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1).  
  
2.  Chargez le fichier que vous souhaitez tester.  
  
3.  Si **ILDASM** indique que le fichier n’est pas un fichier exécutable portable (PE), alors il ne s’agit pas d’un assembly. Pour plus d’informations, consultez la rubrique [Guide pratique pour afficher le contenu d’un assembly](http://msdn.microsoft.com/library/fb7baaab-4c0d-47ad-8fd3-4591cf834709).  
  
### <a name="how-to-programmatically-determine-if-a-file-is-an-assembly"></a>Comment déterminer par programmation si un fichier est un assembly  
  
1.  Appelez la méthode <xref:System.Reflection.AssemblyName.GetAssemblyName%2A>, en passant le chemin complet et le nom du fichier que vous testez.  
  
2.  Si une exception <xref:System.BadImageFormatException> est levée, le fichier n’est pas un assembly.  
  
## <a name="example"></a>Exemple  
 Cet exemple teste une DLL pour voir s’il s’agit d’un assembly.  
  
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
  
 La méthode xref:System.Reflection.AssemblyName.GetAssemblyName%2A> charge le fichier de test, puis le libère une fois les informations lues.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Reflection.AssemblyName>   
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)   
 [Assemblys et le Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)
