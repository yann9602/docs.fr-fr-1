---
title: Assemblys friend (C#)
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
ms.assetid: b65ea7de-0801-477a-a39c-e914c2cc107c
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e2680b5799c552a063ff7c539a31a5dd00b90a75
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="friend-assemblies-c"></a><span data-ttu-id="7539c-102">Assemblys friend (C#)</span><span class="sxs-lookup"><span data-stu-id="7539c-102">Friend Assemblies (C#)</span></span>
<span data-ttu-id="7539c-103">Un *assembly friend* est un assembly qui peut accéder aux types et membres [internes](../../../../csharp/language-reference/keywords/internal.md) d'un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="7539c-103">A *friend assembly* is an assembly that can access another assembly's [internal](../../../../csharp/language-reference/keywords/internal.md) types and members.</span></span> <span data-ttu-id="7539c-104">Si vous identifiez un assembly comme étant un assembly friend, vous n’avez plus à marquer ses types et ses membres comme publics pour qu’ils soient accessibles aux autres assemblys.</span><span class="sxs-lookup"><span data-stu-id="7539c-104">If you identify an assembly as a friend assembly, you no longer have to mark types and members as public in order for them to be accessed by other assemblies.</span></span> <span data-ttu-id="7539c-105">Ceci est particulièrement utile dans les scénarios suivants :</span><span class="sxs-lookup"><span data-stu-id="7539c-105">This is especially convenient in the following scenarios:</span></span>  
  
-   <span data-ttu-id="7539c-106">Pendant un test unitaire, lorsque le code de test s’exécute dans un assembly séparé, mais nécessite l’accès aux membres de l’assembly actuellement testés qui sont marqués comme `internal`.</span><span class="sxs-lookup"><span data-stu-id="7539c-106">During unit testing, when test code runs in a separate assembly but requires access to members in the assembly being tested that are marked as `internal` .</span></span>  
  
-   <span data-ttu-id="7539c-107">Lorsque vous développez une bibliothèque de classes et que des ajouts à la bibliothèque sont contenus dans des assemblys séparés, mais nécessitent l’accès aux membres des assemblys existants qui sont marqués comme `internal`.</span><span class="sxs-lookup"><span data-stu-id="7539c-107">When you are developing a class library and additions to the library are contained in separate assemblies but require access to members in existing assemblies that are marked as `internal` .</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7539c-108">Remarques</span><span class="sxs-lookup"><span data-stu-id="7539c-108">Remarks</span></span>  
 <span data-ttu-id="7539c-109">Vous pouvez utiliser l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour identifier un ou plusieurs assemblys friend pour un assembly donné.</span><span class="sxs-lookup"><span data-stu-id="7539c-109">You can use the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute to identify one or more friend assemblies for a given assembly.</span></span> <span data-ttu-id="7539c-110">L’exemple suivant utilise l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> dans l’assembly A et spécifie l’assembly `AssemblyB` comme assembly friend.</span><span class="sxs-lookup"><span data-stu-id="7539c-110">The following example uses the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute in assembly A and specifies assembly `AssemblyB` as a friend assembly.</span></span> <span data-ttu-id="7539c-111">De cette façon, l’assembly `AssemblyB` a accès à tous les types et membres de l’assembly A qui sont marqués comme `internal`.</span><span class="sxs-lookup"><span data-stu-id="7539c-111">This gives assembly `AssemblyB` access to all types and members in assembly A that are marked as `internal`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7539c-112">Lorsque vous compilez un assembly (assembly `AssemblyB`) qui doit accéder aux types ou aux membres internes d’un autre assembly (assembly *A*), vous devez spécifier explicitement le nom du fichier de sortie (.exe ou .dll) à l’aide de l’option **/out** du compilateur.</span><span class="sxs-lookup"><span data-stu-id="7539c-112">When you compile an assembly (assembly `AssemblyB`) that will access internal types or internal members of another assembly (assembly *A*), you must explicitly specify the name of the output file (.exe or .dll) by using the **/out** compiler option.</span></span> <span data-ttu-id="7539c-113">Ceci est nécessaire, car le compilateur n’a pas encore généré le nom de l’assembly qu’il est en train de créer au moment où il effectue une liaison avec les références externes.</span><span class="sxs-lookup"><span data-stu-id="7539c-113">This is required because the compiler has not yet generated the name for the assembly it is building at the time it is binding to external references.</span></span> <span data-ttu-id="7539c-114">Pour plus d'informations, consultez [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7539c-114">For more information, see [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md) .</span></span>  
  
```csharp  
using System.Runtime.CompilerServices;  
using System;  
  
[assembly: InternalsVisibleTo("AssemblyB")]  
  
// The class is internal by default.  
class FriendClass  
{  
    public void Test()  
    {  
        Console.WriteLine("Sample Class");  
    }  
}  
  
// Public class that has an internal method.  
public class ClassWithFriendMethod  
{  
    internal void Test()  
    {  
        Console.WriteLine("Sample Method");  
    }  
  
}  
```  
  
 <span data-ttu-id="7539c-115">Seuls les assemblys que vous spécifiez explicitement, comme les assemblys friend, peuvent accéder aux types et aux membres `internal`.</span><span class="sxs-lookup"><span data-stu-id="7539c-115">Only assemblies that you explicitly specify as friends can access `internal` types and members.</span></span> <span data-ttu-id="7539c-116">Par exemple, si l’assembly B est un assembly friend de l’assembly A, et si l’assembly C référence l’assembly B, l’assembly C n’aura pas accès aux types `internal` de l’assembly A.</span><span class="sxs-lookup"><span data-stu-id="7539c-116">For example, if assembly B is a friend of assembly A and assembly C references assembly B, C does not have access to `internal` types in A.</span></span>  
  
 <span data-ttu-id="7539c-117">Le compilateur effectue une validation de base du nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="7539c-117">The compiler performs some basic validation of the friend assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute.</span></span> <span data-ttu-id="7539c-118">Si l’assembly *A* déclare l’assembly *B* comme étant un assembly friend, les règles de validation sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7539c-118">If assembly *A* declares *B* as a friend assembly, the validation rules are as follows:</span></span>  
  
-   <span data-ttu-id="7539c-119">Si l’assembly *A* porte un nom fort, l’assembly *B* doit également porter un nom fort.</span><span class="sxs-lookup"><span data-stu-id="7539c-119">If assembly *A* is strong named, assembly *B* must also be strong named.</span></span> <span data-ttu-id="7539c-120">Le nom de l’assembly friend qui est passé à l’attribut doit être composé du nom de l’assembly et de la clé publique de la clé de nom fort qui est utilisée pour signer l’assembly *B*.</span><span class="sxs-lookup"><span data-stu-id="7539c-120">The friend assembly name that is passed to the attribute must consist of the assembly name and the public key of the strong-name key that is used to sign assembly *B*.</span></span>  
  
     <span data-ttu-id="7539c-121">Le nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ne peut pas être le nom fort de l’assembly *B* : n’incluez ni la version de l’assembly, ni la culture, ni l’architecture, ni le jeton de clé publique.</span><span class="sxs-lookup"><span data-stu-id="7539c-121">The friend assembly name that is passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute cannot be the strong name of assembly *B*: do not include the assembly version, culture, architecture, or public key token.</span></span>  
  
-   <span data-ttu-id="7539c-122">Si l’assembly *A* n’a pas un nom fort, le nom de l’assembly friend doit être constitué uniquement du nom de l’assembly.</span><span class="sxs-lookup"><span data-stu-id="7539c-122">If assembly *A* is not strong named, the friend assembly name should consist of only the assembly name.</span></span> <span data-ttu-id="7539c-123">Pour plus d’informations, consultez [Guide pratique pour créer des assemblys friend non signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7539c-123">For more information, see [How to: Create Unsigned Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).</span></span>  
  
-   <span data-ttu-id="7539c-124">Si l’assembly *B* porte un nom fort, vous devez spécifier la clé de nom fort de l’assembly *B* en utilisant le paramètre de projet ou l’option de compilateur `/keyfile`.</span><span class="sxs-lookup"><span data-stu-id="7539c-124">If assembly *B* is strong named, you must specify the strong-name key for assembly *B* by using the project setting or the command-line `/keyfile` compiler option.</span></span> <span data-ttu-id="7539c-125">Pour plus d’informations, consultez [Guide pratique pour créer des assemblys friend signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="7539c-125">For more information, see [How to: Create Signed Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).</span></span>  
  
 <span data-ttu-id="7539c-126">La classe <xref:System.Security.Permissions.StrongNameIdentityPermission> offre également la possibilité de partager des types, avec les différences suivantes :</span><span class="sxs-lookup"><span data-stu-id="7539c-126">The <xref:System.Security.Permissions.StrongNameIdentityPermission> class also provides the ability to share types, with the following differences:</span></span>  
  
-   <span data-ttu-id="7539c-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> s’applique à un type individuel, alors qu’un assembly friend s’applique à l’assembly entier.</span><span class="sxs-lookup"><span data-stu-id="7539c-127"><xref:System.Security.Permissions.StrongNameIdentityPermission> applies to an individual type, while a friend assembly applies to the whole assembly.</span></span>  
  
-   <span data-ttu-id="7539c-128">Si vous souhaitez partager des centaines de types de l’assembly *A* avec l’assembly *B*, vous devez ajouter <xref:System.Security.Permissions.StrongNameIdentityPermission> à chacun d’eux.</span><span class="sxs-lookup"><span data-stu-id="7539c-128">If there are hundreds of types in assembly *A* that you want to share with assembly *B*, you have to add <xref:System.Security.Permissions.StrongNameIdentityPermission> to all of them.</span></span> <span data-ttu-id="7539c-129">Si vous utilisez un assembly friend, vous n’aurez à déclarer la relation d’assembly friend qu’une seule fois.</span><span class="sxs-lookup"><span data-stu-id="7539c-129">If you use a friend assembly, you only need to declare the friend relationship once.</span></span>  
  
-   <span data-ttu-id="7539c-130">Si vous utilisez <xref:System.Security.Permissions.StrongNameIdentityPermission>, les types que vous voulez partager doivent être déclarés comme publics.</span><span class="sxs-lookup"><span data-stu-id="7539c-130">If you use <xref:System.Security.Permissions.StrongNameIdentityPermission>, the types you want to share have to be declared as public.</span></span> <span data-ttu-id="7539c-131">Si vous utilisez un assembly friend, les types partagés sont déclarés comme `internal`.</span><span class="sxs-lookup"><span data-stu-id="7539c-131">If you use a friend assembly, the shared types are declared as `internal`.</span></span>  
  
 <span data-ttu-id="7539c-132">Pour plus d’informations sur la façon d’accéder aux types et aux méthodes `internal` d’un assembly à partir d’un fichier de module (avec l’extension .netmodule), consultez [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="7539c-132">For information about how to access an assembly's `internal` types and methods from a module file (a file with the .netmodule extension), see [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7539c-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7539c-133">See Also</span></span>  
 <span data-ttu-id="7539c-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span><span class="sxs-lookup"><span data-stu-id="7539c-134"><xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></span></span>   
 <span data-ttu-id="7539c-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></span><span class="sxs-lookup"><span data-stu-id="7539c-135"><xref:System.Security.Permissions.StrongNameIdentityPermission></span></span>   
 <span data-ttu-id="7539c-136">[Guide pratique pour créer des assemblys friend non signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="7539c-136">[How to: Create Unsigned Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md) </span></span>  
 <span data-ttu-id="7539c-137">[Guide pratique pour créer des assemblys friend signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span><span class="sxs-lookup"><span data-stu-id="7539c-137">[How to: Create Signed Friend Assemblies (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md) </span></span>  
 <span data-ttu-id="7539c-138">[Assemblys et le Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span><span class="sxs-lookup"><span data-stu-id="7539c-138">[Assemblies and the Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md) </span></span>  
 [<span data-ttu-id="7539c-139">Guide de programmation C#</span><span class="sxs-lookup"><span data-stu-id="7539c-139">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)

