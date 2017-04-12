---
title: "Comment : créer des assemblys Friend non signés (Visual Basic) | Documents Microsoft"
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
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ceddb35c306f72c8927deda326d9fcca6c75d786
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a>Comment : créer des assemblys Friend non signés (Visual Basic)
Cet exemple montre comment utiliser des assemblys friend avec les assemblys qui ne sont pas signés.  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a>Pour créer un assembly et un assembly friend  
  
1.  Ouvrez une invite de commandes.  
  
2.  Créez un fichier Visual Basic nommé `friend_signed_A.` qui contient le code suivant. Le code utilise le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut pour déclarer friend_signed_B comme assembly friend.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
    ```vb  
    ' friend_unsigned_A.vb  
    ' Compile with:   
    ' Vbc /target:library friend_unsigned_A.vb  
    Imports System.Runtime.CompilerServices  
    Imports System  
  
    <Assembly: InternalsVisibleTo("friend_unsigned_B")>   
  
    ' Friend type.  
    Friend Class Class1  
        Public Sub Test()  
            Console.WriteLine("Class1.Test")  
        End Sub  
    End Class  
  
    ' Public type with Friend member.  
    Public Class Class2  
        Friend Sub Test()  
            Console.WriteLine("Class2.Test")  
        End Sub  
    End Class  
    ```  
  
3.  Compilez et signez friend_signed_A à l’aide de la commande suivante.  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  Créez un fichier Visual Basic nommé `friend_unsigned_B` qui contient le code suivant. Étant donné que friend_unsigned_A spécifie friend_unsigned_B comme assembly friend, le code de friend_unsigned_B peut accéder aux `Friend` types et membres à partir de friend_unsigned_A.  
  
    ```vb  
    ' friend_unsigned_B.vb  
    ' Compile with:   
    ' Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    Module Module1  
        Sub Main()  
            ' Access a Friend type.  
            Dim inst1 As New Class1()  
            inst1.Test()  
  
            Dim inst2 As New Class2()  
            ' Access a Friend member of a public type.  
            inst2.Test()  
  
            System.Console.ReadLine()  
        End Sub  
    End Module  
    ```  
  
5.  Compilez friend_signed_B à l’aide de la commande suivante.  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     Le nom de l’assembly qui est généré par le compilateur doit correspondre le nom de l’assembly friend qui est passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Vous pouvez définir explicitement l’assembly à l’aide de la `/out` option du compilateur.  
  
6.  Exécutez le fichier friend_signed_B.exe.  
  
     Le programme imprime deux chaînes : « Class1.Test » et « Class2.Test ».  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Il existe des similitudes entre l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut et la <xref:System.Security.Permissions.StrongNameIdentityPermission>classe.</xref:System.Security.Permissions.StrongNameIdentityPermission> </xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission>peut demander des autorisations de sécurité pour exécuter une section particulière de code, tandis que le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut contrôle la visibilité de `Friend` types et membres.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Assemblys friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Comment : créer des assemblys Friend signés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Concepts de Guide de programmation](../../../../visual-basic/programming-guide/concepts/index.md)
