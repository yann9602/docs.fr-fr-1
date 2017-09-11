---
title: Assemblys friend (Visual Basic) | Documents Microsoft
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
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
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
ms.openlocfilehash: 23c9167bf6a632b53202bdc56aebb2248065e967
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="friend-assemblies-visual-basic"></a><span data-ttu-id="24f60-102">Assemblys friend (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24f60-102">Friend Assemblies (Visual Basic)</span></span>
<span data-ttu-id="24f60-103">A *assembly friend* est un assembly qui est accessible d’un autre assembly [ami](../../../../visual-basic/language-reference/modifiers/friend.md) types et membres.</span><span class="sxs-lookup"><span data-stu-id="24f60-103">A *friend assembly* is an assembly that can access another assembly's [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) types and members.</span></span> <span data-ttu-id="24f60-104">Si vous identifiez un assembly en tant qu’assembly friend, vous n’avez plus marquer des types et membres publics pour qu’ils accessibles par d’autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="24f60-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="24f60-105">Ceci est particulièrement pratique dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="24f60-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="24f60-106">Pendant le test unitaire, lorsque le code de test s’exécute dans un assembly séparé, mais requiert l’accès aux membres de l’assembly en cours de test qui sont marqués comme `Friend`.</span><span class="sxs-lookup"><span data-stu-id="24f60-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `Friend`.</span></span>  
  
-   <span data-ttu-id="24f60-107">Lorsque vous développez une bibliothèque de classes et ajouts à la bibliothèque sont contenus dans des assemblys séparés, mais nécessitent l’accès aux membres des assemblys existants qui sont marqués comme `Friend`.</span><span class="sxs-lookup"><span data-stu-id="24f60-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `Friend`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24f60-108">Notes</span><span class="sxs-lookup"><span data-stu-id="24f60-108">Remarks</span></span>  
 <span data-ttu-id="24f60-109">Vous pouvez utiliser la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut pour identifier un ou plusieurs assemblys friend pour un assembly donné.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="24f60-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="24f60-110">L’exemple suivant utilise le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>d’attribut dans l’assembly A et spécifie l’assembly `AssemblyB` comme assembly friend.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="24f60-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="24f60-111">Cela donne l’assembly `AssemblyB` accès à tous les types et membres de l’assembly A qui sont marqués comme `Friend`.</span><span class="sxs-lookup"><span data-stu-id="24f60-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `Friend`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24f60-112">Lorsque vous compilez un assembly (assembly `AssemblyB`) qui accédera aux types ou membres internes d’un autre assembly (assembly *A*), vous devez spécifier explicitement le nom du fichier de sortie (.exe ou .dll) à l’aide de la **/out** option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="24f60-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="24f60-113">Cela est nécessaire, car le compilateur n’a pas encore généré le nom de l’assembly qu’il génère au moment où qu'il est lié aux références externes.</span><span class="sxs-lookup"><span data-stu-id="24f60-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="24f60-114">Pour plus d’informations, consultez [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span><span class="sxs-lookup"><span data-stu-id="24f60-114">For more information, see [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).</span></span>  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports System  
<Assembly: InternalsVisibleTo("AssemblyB")>   
  
' Friend class.  
Friend Class FriendClass  
    Public Sub Test()  
        Console.WriteLine("Sample Class")  
    End Sub  
End Class  
  
' Public class with a Friend method.  
Public Class ClassWithFriendMethod  
    Friend Sub Test()  
        Console.WriteLine("Sample Method")  
    End Sub  
End Class  
  
```  
  
 <span data-ttu-id="24f60-115">Seuls les assemblys que vous spécifiez explicitement comme Friend peuvent accéder aux `Friend` types et membres.</span><span class="sxs-lookup"><span data-stu-id="24f60-115">Only assemblies that you explicitly specify as friends can access `Friend` types and members.</span></span> <span data-ttu-id="24f60-116">Par exemple, si l’assembly B est un ami de l’assembly A et assembly C référence l’assembly B, C n’a pas accès à `Friend` types dans A.</span><span class="sxs-lookup"><span data-stu-id="24f60-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `Friend` types in A.</span></span>  
  
 <span data-ttu-id="24f60-117">Le compilateur effectue une validation de base du nom de l’assembly friend passé à le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="24f60-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="24f60-118">Si assembly *A* déclare *B* comme assembly friend, les règles de validation sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="24f60-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="24f60-119">Si assembly *A* porte un nom, assembly fort *B* doit également être un nom fort.</span><span class="sxs-lookup"><span data-stu-id="24f60-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="24f60-120">Le nom de l’assembly friend qui est passé à l’attribut doit être composé du nom de l’assembly et la clé publique de la clé de nom fort qui est utilisée pour signer l’assembly *B*.</span><span class="sxs-lookup"><span data-stu-id="24f60-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="24f60-121">Le nom de l’assembly friend qui est passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut ne peut pas être le nom fort de l’assembly *B*: n’incluent pas la version de l’assembly, culture, architecture ou jeton de clé publique.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="24f60-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="24f60-122">Si assembly *A* n’est pas fort nommé, le nom de l’assembly friend doit se composer d’uniquement le nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="24f60-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="24f60-123">Pour plus d’informations, consultez [Comment : créer des assemblys non signés Friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="24f60-123">For more information, see [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="24f60-124">Si assembly *B* porte un nom fort, vous devez spécifier la clé de nom fort pour l’assembly *B* en utilisant le paramètre du projet ou la ligne de commande `/keyfile` option du compilateur.</span><span class="sxs-lookup"><span data-stu-id="24f60-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="24f60-125">Pour plus d’informations, consultez [Comment : créer les assemblys signés du Friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="24f60-125">For more information, see [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="24f60-126">La <xref:System.Security.Permissions.StrongNameIdentityPermission>classe fournit également la possibilité de partager des types, avec les différences suivantes :</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="24f60-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="24f60-127"><xref:System.Security.Permissions.StrongNameIdentityPermission>s’applique à un type individuel, alors qu’un assembly friend s’applique à l’assembly entier.</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="24f60-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="24f60-128">S’il existe des centaines de types dans l’assembly *A* que vous souhaitez partager avec l’assembly *B*, vous devez ajouter <xref:System.Security.Permissions.StrongNameIdentityPermission>à chacun d’eux.</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="24f60-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="24f60-129">Si vous utilisez un assembly friend, vous devez seulement déclarer la relation « friend » qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="24f60-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="24f60-130">Si vous utilisez <xref:System.Security.Permissions.StrongNameIdentityPermission>, les types que vous voulez partager doivent être déclarés comme étant public.</xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="24f60-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="24f60-131">Si vous utilisez un assembly friend, les types partagés sont déclarés comme `Friend`.</span><span class="sxs-lookup"><span data-stu-id="24f60-131">If you use a friend assembly, the shared types are declared as `Friend`.</span></span>  
  
 <span data-ttu-id="24f60-132">Pour plus d’informations sur l’accès d’un assembly à `Friend` types et méthodes à partir d’un fichier de module (fichier avec l’extension .netmodule), consultez [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span><span class="sxs-lookup"><span data-stu-id="24f60-132">For information about how to access an assembly's `Friend` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24f60-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="24f60-133">See Also</span></span>  
 <span data-ttu-id="24f60-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="24f60-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
 <span data-ttu-id="24f60-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="24f60-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></span></span>   
<span data-ttu-id="24f60-136"> [Comment : créer des assemblys Friend non signés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="24f60-136"> [How to: Create Unsigned Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
<span data-ttu-id="24f60-137"> [Comment : créer des assemblys Friend signés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="24f60-137"> [How to: Create Signed Friend Assemblies (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span></span>  
<span data-ttu-id="24f60-138"> [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="24f60-138"> [Assemblies and the Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
<span data-ttu-id="24f60-139"> [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)</span><span class="sxs-lookup"><span data-stu-id="24f60-139"> [Programming Concepts](../../../../visual-basic/programming-guide/concepts/index.md)</span></span>
