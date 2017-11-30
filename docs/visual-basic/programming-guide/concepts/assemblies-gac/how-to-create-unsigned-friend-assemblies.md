---
title: "Comment : créer des assemblys Friend non signés (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5735eb79-9729-4c46-ac1f-537ada3acaa7
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a2b2667c60a07a2897a0934d210901042e2e43c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-unsigned-friend-assemblies-visual-basic"></a><span data-ttu-id="38d77-102">Comment : créer des assemblys Friend non signés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38d77-102">How to: Create Unsigned Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="38d77-103">Cet exemple montre comment utiliser des assemblys friend avec des assemblys qui ne sont pas signés.</span><span class="sxs-lookup"><span data-stu-id="38d77-103">This example shows how to use friend assemblies with assemblies that are unsigned.</span></span>  
  
### <a name="to-create-an-assembly-and-a-friend-assembly"></a><span data-ttu-id="38d77-104">Pour créer un assembly et un assembly friend</span><span class="sxs-lookup"><span data-stu-id="38d77-104">To create an assembly and a friend assembly</span></span>  
  
1.  <span data-ttu-id="38d77-105">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="38d77-105">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="38d77-106">Créez un fichier Visual Basic nommé `friend_signed_A.` qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38d77-106">Create a Visual Basic file named `friend_signed_A.` that contains the following code.</span></span> <span data-ttu-id="38d77-107">Le code utilise l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour déclarer friend_signed_B comme assembly friend.</span><span class="sxs-lookup"><span data-stu-id="38d77-107">The code uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to declare friend_signed_B as a friend assembly.</span></span>  
  
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
  
3.  <span data-ttu-id="38d77-108">Compilez et signez friend_signed_A à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="38d77-108">Compile and sign friend_signed_A by using the following command.</span></span>  
  
    ```vb  
    Vbc /target:library friend_unsigned_A.vb  
    ```  
  
4.  <span data-ttu-id="38d77-109">Créez un fichier Visual Basic nommé `friend_unsigned_B` qui contient le code suivant.</span><span class="sxs-lookup"><span data-stu-id="38d77-109">Create a Visual Basic file named `friend_unsigned_B` that contains the following code.</span></span> <span data-ttu-id="38d77-110">Étant donné que friend_unsigned_A spécifie friend_unsigned_B comme assembly friend, le code de friend_unsigned_B peut accéder aux membres et aux types `Friend` de friend_unsigned_A.</span><span class="sxs-lookup"><span data-stu-id="38d77-110">Because friend_unsigned_A specifies friend_unsigned_B as a friend assembly, the code in friend_unsigned_B can access `Friend` types and members from friend_unsigned_A.</span></span>  
  
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
  
5.  <span data-ttu-id="38d77-111">Compilez friend_signed_B à l’aide de la commande suivante.</span><span class="sxs-lookup"><span data-stu-id="38d77-111">Compile friend_signed_B by using the following command.</span></span>  
  
    ```vb  
    Vbc /r:friend_unsigned_A.dll friend_unsigned_B.vb  
    ```  
  
     <span data-ttu-id="38d77-112">Le nom de l’assembly qui est généré par le compilateur doit correspondre au nom de l’assembly friend qui est passé à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="38d77-112">The name of the assembly that is generated by the compiler must match the friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="38d77-113">Vous pouvez définir explicitement l’assembly à l’aide de la `/out` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="38d77-113">You can explicitly set the assembly by using the `/out` compiler option.</span></span>  
  
6.  <span data-ttu-id="38d77-114">Exécutez le fichier friend_signed_B.exe.</span><span class="sxs-lookup"><span data-stu-id="38d77-114">Run the friend_signed_B.exe file.</span></span>  
  
     <span data-ttu-id="38d77-115">Le programme imprime deux chaînes : « Class1.Test » et « Class2.Test ».</span><span class="sxs-lookup"><span data-stu-id="38d77-115">The program prints two strings: "Class1.Test" and "Class2.Test".</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="38d77-116">Sécurité .NET Framework</span><span class="sxs-lookup"><span data-stu-id="38d77-116">.NET Framework Security</span></span>  
 <span data-ttu-id="38d77-117">Il existe des similitudes entre l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> et la classe <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="38d77-117">There are similarities between the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute and the <xref:System.Security.Permissions.StrongNameIdentityPermission> class.</span></span> <span data-ttu-id="38d77-118">La principale différence est que <xref:System.Security.Permissions.StrongNameIdentityPermission> peut demander des autorisations de sécurité pour exécuter une section de code particulière, tandis que l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> contrôle la visibilité des membres et types `Friend`.</span><span class="sxs-lookup"><span data-stu-id="38d77-118">The main difference is that <xref:System.Security.Permissions.StrongNameIdentityPermission> can demand security permissions to run a particular section of code, whereas the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute controls the visibility of `Friend` types and members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38d77-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38d77-119">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 [<span data-ttu-id="38d77-120">Assemblys et le Global Assembly Cache (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38d77-120">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="38d77-121">Assemblys friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38d77-121">Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [<span data-ttu-id="38d77-122">Comment : créer des assemblys Friend signés (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="38d77-122">How to: Create Signed Friend Assemblies (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [<span data-ttu-id="38d77-123">Concepts de Guide de programmation</span><span class="sxs-lookup"><span data-stu-id="38d77-123">Programming Guide Concepts</span></span>](../../../../visual-basic/programming-guide/concepts/index.md)
