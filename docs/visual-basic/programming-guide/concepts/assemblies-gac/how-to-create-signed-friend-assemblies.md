---
title: "Comment : créer des assemblys Friend signés (Visual Basic) | Documents Microsoft"
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
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: 4
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 1a69f7e833800ec7417bc35fad763f1001b3e7f9
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a>Comment : créer des assemblys Friend signés (Visual Basic)
Cet exemple montre comment utiliser des assemblys friend avec les assemblys qui ont des noms forts. Les deux assemblys doivent être des noms forts. Bien que les deux assemblys dans cet exemple montre comment utilisent les mêmes clés, vous pouvez utiliser des clés différentes pour les deux assemblys.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Pour créer un assembly signé et un assembly friend  
  
1.  Ouvrez une invite de commandes.  
  
2.  Utilisez la séquence suivante de commandes avec l’outil Strong Name tool pour générer un fichier de clé et afficher sa clé publique. Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).  
  
    1.  Générer une clé de nom fort pour cet exemple et le stocker dans le fichier FriendAssemblies.snk :  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Extraire la clé publique de FriendAssemblies.snk et mettez-la dans FriendAssemblies.publickey :  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Afficher la clé publique stockée dans le fichier FriendAssemblies.publickey :  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Créez un fichier Visual Basic nommé `friend_signed_A` qui contient le code suivant. Le code utilise le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut pour déclarer friend_signed_B comme assembly friend.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
     L’outil Strong Name tool génère une nouvelle clé publique chaque fois qu’il exécute. Par conséquent, vous devez remplacer la clé publique dans le code suivant avec la clé publique que vous venez de générer, comme indiqué dans l’exemple suivant.  
  
    ```vb  
    ' friend_signed_A.vb  
    ' Compile with:   
    ' Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    Imports System.Runtime.CompilerServices  
  
    <Assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")>   
    Public Class Class1  
        Public Sub Test()  
            System.Console.WriteLine("Class1.Test")  
            System.Console.ReadLine()  
        End Sub  
    End Class  
    ```  
  
4.  Compilez et signez friend_signed_A à l’aide de la commande suivante.  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  Créez un fichier Visual Basic nommé `friend_signed_B` et contient le code suivant. Étant donné que friend_signed_A spécifie friend_signed_B comme assembly friend, le code de friend_signed_B peut accéder aux `Friend` types et membres à partir de friend_signed_A. Le fichier contient le code suivant.  
  
    ```vb  
    ' friend_signed_B.vb  
    ' Compile with:   
    ' Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    Module Sample  
        Public Sub Main()  
            Dim inst As New Class1  
            inst.Test()  
        End Sub  
    End Module  
    ```  
  
6.  Compilez et signez friend_signed_B à l’aide de la commande suivante.  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     Le nom de l’assembly généré par le compilateur doit correspondre au nom d’assembly friend passé à le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Vous pouvez définir explicitement l’assembly à l’aide de la `/out` option du compilateur. Pour plus d’informations, consultez [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
7.  Exécutez le fichier friend_signed_B.exe.  
  
     Le programme imprime la chaîne « Class1.Test ».  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Il existe des similitudes entre l' <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut et la <xref:System.Security.Permissions.StrongNameIdentityPermission>classe.</xref:System.Security.Permissions.StrongNameIdentityPermission> </xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission>peut demander des autorisations de sécurité pour exécuter une section particulière de code, tandis que le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut contrôle la visibilité de `Friend` types et membres.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> </xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Assemblys friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)   
 [Comment : créer des assemblys Friend non signés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [/ keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)   
 [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23)   
 [Création et utilisation d’assemblys avec nom fort](https://msdn.microsoft.com/library/xwb8f617)   
 [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)
