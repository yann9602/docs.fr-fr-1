---
title: "Guide pratique pour créer des assemblys friend signés (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: bab62063-61e6-453f-905f-77673df9534e
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d3d9d4c549654341c0739cc8132d953623482d62
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2017
---
# <a name="how-to-create-signed-friend-assemblies-c"></a>Guide pratique pour créer des assemblys friend signés (C#)
Cet exemple montre comment utiliser des assemblys friend avec des assemblys ayant des noms forts. Les deux assemblys doivent avoir des noms forts. Bien que les deux assemblys dans cet exemple utilisent les mêmes clés, vous pouvez utiliser des clés différentes pour deux assemblys.  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a>Pour créer un assembly signé et un assembly friend  
  
1.  Ouvrez une invite de commandes.  
  
2.  Utilisez la séquence de commandes suivante avec l’outil Strong Name Tool pour générer un fichier de clé et afficher sa clé publique. Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).  
  
    1.  Générez une clé de nom fort pour cet exemple et stockez-la dans le fichier FriendAssemblies.snk :  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  Extrayez la clé publique de FriendAssemblies.snk et mettez-la dans FriendAssemblies.publickey :  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  Affichez la clé publique stockée dans le fichier FriendAssemblies.publickey :  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  Créez un fichier C# nommé `friend_signed_A` qui contient le code suivant. Le code utilise l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour déclarer friend_signed_B comme assembly friend.  
  
     L’outil Strong Name Tool génère une nouvelle clé publique chaque fois qu’il s’exécute. Vous devez donc remplacer la clé publique dans le code suivant par la clé publique que vous venez de générer, comme illustré dans l’exemple suivant.  
  
    ```csharp  
    // friend_signed_A.cs  
    // Compile with:   
    // csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    using System.Runtime.CompilerServices;  
  
    [assembly: InternalsVisibleTo("friend_signed_B, PublicKey=0024000004800000940000000602000000240000525341310004000001000100e3aedce99b7e10823920206f8e46cd5558b4ec7345bd1a5b201ffe71660625dcb8f9a08687d881c8f65a0dcf042f81475d2e88f3e3e273c8311ee40f952db306c02fbfc5d8bc6ee1e924e6ec8fe8c01932e0648a0d3e5695134af3bb7fab370d3012d083fa6b83179dd3d031053f72fc1f7da8459140b0af5afc4d2804deccb6")]  
    class Class1  
    {  
        public void Test()  
        {  
            System.Console.WriteLine("Class1.Test");  
            System.Console.ReadLine();  
        }  
    }  
    ```  
  
4.  Compilez et signez friend_signed_A à l’aide de la commande suivante.  
  
    ```csharp  
    csc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.cs  
    ```  
  
5.  Créez un fichier C# nommé `friend_signed_B` contenant le code suivant. Étant donné que friend_signed_A spécifie friend_signed_B comme assembly friend, le code de friend_signed_B peut accéder aux membres et aux types `internal` de friend_signed_A. Le fichier contient le code suivant.  
  
    ```csharp  
    // friend_signed_B.cs  
    // Compile with:   
    // csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    public class Program  
    {  
        static void Main()  
        {  
            Class1 inst = new Class1();  
            inst.Test();  
        }  
    }  
    ```  
  
6.  Compilez et signez friend_signed_B à l’aide de la commande suivante.  
  
    ```csharp  
    csc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll /out:friend_signed_B.exe friend_signed_B.cs  
    ```  
  
     Le nom de l’assembly généré par le compilateur doit correspondre au nom de l’assembly friend passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Vous devez spécifier explicitement le nom de l’assembly de sortie (.exe ou .dll) à l’aide de l’option du compilateur `/out`.  Pour plus d’informations, consultez l’article [/out (C# Compiler Options) (/out [Options du compilateur C#])](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
7.  Exécutez le fichier friend_signed_B.exe.  
  
     Le programme imprime la chaîne « Class1.Test ».  
  
## <a name="net-framework-security"></a>Sécurité .NET Framework  
 Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>. La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, tandis que l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> contrôle la visibilité des membres et types `internal`.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [Assemblys et le Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)  
 [Assemblys friend (C++)](../../../../csharp/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Guide pratique pour créer des assemblys friend non signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [/keyfile](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Sn.exe (outil Strong Name)](https://msdn.microsoft.com/library/k5b5tt23)  
 [Création et utilisation d’assemblys avec nom fort](../../../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)  
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)
