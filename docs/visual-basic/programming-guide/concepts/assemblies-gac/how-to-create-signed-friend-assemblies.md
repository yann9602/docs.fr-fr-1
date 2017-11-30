---
title: "Comment : créer des assemblys Friend signés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2afd83d-b044-484b-a56d-56d0a8a40647
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f87f816992bdfa9ed347c35ba651c59187551772
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-signed-friend-assemblies-visual-basic"></a><span data-ttu-id="18425-102">Comment : créer des assemblys Friend signés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18425-102">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="18425-103">Cet exemple montre comment utiliser des assemblys friend avec des assemblys ayant des noms forts.</span><span class="sxs-lookup"><span data-stu-id="18425-103">This example shows how to use friend assemblies with assemblies that have strong names.</span></span> <span data-ttu-id="18425-104">Les deux assemblys doivent avoir des noms forts.</span><span class="sxs-lookup"><span data-stu-id="18425-104">Both assemblies must be strong named.</span></span> <span data-ttu-id="18425-105">Bien que les deux assemblys dans cet exemple utilisent les mêmes clés, vous pouvez utiliser des clés différentes pour deux assemblys.</span><span class="sxs-lookup"><span data-stu-id="18425-105">Although both assemblies in this example use the same keys, you could use different keys for two assemblies.</span></span>  
  
### <a name="to-create-a-signed-assembly-and-a-friend-assembly"></a><span data-ttu-id="18425-106">Pour créer un assembly signé et un assembly friend</span><span class="sxs-lookup"><span data-stu-id="18425-106">To create a signed assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="18425-107">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="18425-107">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="18425-108">Utilisez la séquence de commandes suivante avec l’outil Strong Name Tool pour générer un fichier de clé et afficher sa clé publique.</span><span class="sxs-lookup"><span data-stu-id="18425-108">Use the following sequence of commands with the Strong Name tool to generate a keyfile and to display its public key.</span></span> <span data-ttu-id="18425-109">Pour plus d’informations, consultez [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="18425-109">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
    1.  <span data-ttu-id="18425-110">Générez une clé de nom fort pour cet exemple et stockez-la dans le fichier FriendAssemblies.snk :</span><span class="sxs-lookup"><span data-stu-id="18425-110">Generate a strong-name key for this example and store it in the file FriendAssemblies.snk:</span></span>  
  
         `sn -k FriendAssemblies.snk`  
  
    2.  <span data-ttu-id="18425-111">Extrayez la clé publique de FriendAssemblies.snk et mettez-la dans FriendAssemblies.publickey :</span><span class="sxs-lookup"><span data-stu-id="18425-111">Extract the public key from FriendAssemblies.snk and put it into FriendAssemblies.publickey:</span></span>  
  
         `sn -p FriendAssemblies.snk FriendAssemblies.publickey`  
  
    3.  <span data-ttu-id="18425-112">Affichez la clé publique stockée dans le fichier FriendAssemblies.publickey :</span><span class="sxs-lookup"><span data-stu-id="18425-112">Display the public key stored in the file FriendAssemblies.publickey:</span></span>  
  
         `sn -tp FriendAssemblies.publickey`  
  
3.  <span data-ttu-id="18425-113">Créez un fichier Visual Basic nommé `friend_signed_A` qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="18425-113">Create a Visual Basic file named `friend_signed_A` that contains the following code.</span></span> <span data-ttu-id="18425-114">Le code utilise l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour déclarer friend_signed_B comme assembly friend.</span><span class="sxs-lookup"><span data-stu-id="18425-114">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
     <span data-ttu-id="18425-115">L’outil Strong Name Tool génère une nouvelle clé publique chaque fois qu’il s’exécute.</span><span class="sxs-lookup"><span data-stu-id="18425-115">The Strong Name tool generates a new public key every time it runs.</span></span> <span data-ttu-id="18425-116">Vous devez donc remplacer la clé publique dans le code suivant par la clé publique que vous venez de générer, comme illustré dans l’exemple suivant.</span><span class="sxs-lookup"><span data-stu-id="18425-116">Therefore, you must replace the public key in the following code with the public key you just generated, as shown in the following example.</span></span>  
  
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
  
4.  <span data-ttu-id="18425-117">Compilez et signez friend_signed_A à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="18425-117">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library /keyfile:FriendAssemblies.snk friend_signed_A.vb  
    ```  
  
5.  <span data-ttu-id="18425-118">Créer un fichier Visual Basic nommé `friend_signed_B` et contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="18425-118">Create a Visual Basic file that is named `friend_signed_B` and contains the following code.</span></span> <span data-ttu-id="18425-119">Étant donné que friend_signed_A spécifie friend_signed_B comme assembly friend, le code de friend_signed_B peut accéder aux membres et aux types `Friend` de friend_signed_A.</span><span class="sxs-lookup"><span data-stu-id="18425-119">Because friend_signed_A specifies friend_signed_B as a friend assembly, the code in friend_signed_B can access `Friend` types and members from friend_signed_A.</span></span> <span data-ttu-id="18425-120">Le fichier contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="18425-120">The file contains the following code.</span></span>  
  
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
  
6.  <span data-ttu-id="18425-121">Compilez et signez friend_signed_B à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="18425-121">Compile and sign friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /keyfile:FriendAssemblies.snk /r:friend_signed_A.dll friend_signed_B.vb  
    ```  
  
     <span data-ttu-id="18425-122">Le nom de l’assembly généré par le compilateur doit correspondre au nom de l’assembly friend passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="18425-122">The name of the assembly generated by the compiler must match the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="18425-123">Vous pouvez définir explicitement l’assembly à l’aide de la `/out` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="18425-123">You can explicitly set the assembly by using the `/out` compiler option.</span></span> <span data-ttu-id="18425-124">Pour plus d’informations, consultez [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="18425-124">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
7.  <span data-ttu-id="18425-125">Exécutez le fichier friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="18425-125">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="18425-126">Le programme imprime la chaîne « Class1.Test ».</span><span class="sxs-lookup"><span data-stu-id="18425-126">The program prints the string "Class1.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="18425-127">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="18425-127">.NET Framework Security</span></span>  
 <span data-ttu-id="18425-128">Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="18425-128">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="18425-129">La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, tandis que l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> contrôle la visibilité des membres et types `Friend`.</span><span class="sxs-lookup"><span data-stu-id="18425-129">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18425-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="18425-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="18425-131">Assemblys et le Global Assembly Cache (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18425-131">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="18425-132">Assemblys friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18425-132">Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="18425-133">Comment : créer des assemblys Friend non signés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18425-133">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [<span data-ttu-id="18425-134">/keyfile</span><span class="sxs-lookup"><span data-stu-id="18425-134">/keyfile</span></span>](../../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [<span data-ttu-id="18425-135">Sn.exe (outil Strong Name)</span><span class="sxs-lookup"><span data-stu-id="18425-135">Sn.exe (Strong Name Tool)</span></span>](https://msdn.microsoft.com/library/k5b5tt23)  
 [<span data-ttu-id="18425-136">Création et utilisation d’assemblys avec nom fort</span><span class="sxs-lookup"><span data-stu-id="18425-136">Creating and Using Strong-Named Assemblies</span></span>](https://msdn.microsoft.com/library/xwb8f617)  
 [<span data-ttu-id="18425-137">Concepts de programmation</span><span class="sxs-lookup"><span data-stu-id="18425-137">Programming Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
