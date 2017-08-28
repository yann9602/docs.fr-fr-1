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
# <a name="friend-assemblies-c"></a>Assemblys friend (C#)
Un *assembly friend* est un assembly qui peut accéder aux types et membres [internes](../../../../csharp/language-reference/keywords/internal.md) d'un autre assembly. Si vous identifiez un assembly comme étant un assembly friend, vous n’avez plus à marquer ses types et ses membres comme publics pour qu’ils soient accessibles aux autres assemblys. Ceci est particulièrement utile dans les scénarios suivants :  
  
-   Pendant un test unitaire, lorsque le code de test s’exécute dans un assembly séparé, mais nécessite l’accès aux membres de l’assembly actuellement testés qui sont marqués comme `internal`.  
  
-   Lorsque vous développez une bibliothèque de classes et que des ajouts à la bibliothèque sont contenus dans des assemblys séparés, mais nécessitent l’accès aux membres des assemblys existants qui sont marqués comme `internal`.  
  
## <a name="remarks"></a>Remarques  
 Vous pouvez utiliser l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> pour identifier un ou plusieurs assemblys friend pour un assembly donné. L’exemple suivant utilise l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> dans l’assembly A et spécifie l’assembly `AssemblyB` comme assembly friend. De cette façon, l’assembly `AssemblyB` a accès à tous les types et membres de l’assembly A qui sont marqués comme `internal`.  
  
> [!NOTE]
>  Lorsque vous compilez un assembly (assembly `AssemblyB`) qui doit accéder aux types ou aux membres internes d’un autre assembly (assembly *A*), vous devez spécifier explicitement le nom du fichier de sortie (.exe ou .dll) à l’aide de l’option **/out** du compilateur. Ceci est nécessaire, car le compilateur n’a pas encore généré le nom de l’assembly qu’il est en train de créer au moment où il effectue une liaison avec les références externes. Pour plus d'informations, consultez [/out (C#)](../../../../csharp/language-reference/compiler-options/out-compiler-option.md).  
  
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
  
 Seuls les assemblys que vous spécifiez explicitement, comme les assemblys friend, peuvent accéder aux types et aux membres `internal`. Par exemple, si l’assembly B est un assembly friend de l’assembly A, et si l’assembly C référence l’assembly B, l’assembly C n’aura pas accès aux types `internal` de l’assembly A.  
  
 Le compilateur effectue une validation de base du nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>. Si l’assembly *A* déclare l’assembly *B* comme étant un assembly friend, les règles de validation sont les suivantes :  
  
-   Si l’assembly *A* porte un nom fort, l’assembly *B* doit également porter un nom fort. Le nom de l’assembly friend qui est passé à l’attribut doit être composé du nom de l’assembly et de la clé publique de la clé de nom fort qui est utilisée pour signer l’assembly *B*.  
  
     Le nom de l’assembly friend soumis à l’attribut <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> ne peut pas être le nom fort de l’assembly *B* : n’incluez ni la version de l’assembly, ni la culture, ni l’architecture, ni le jeton de clé publique.  
  
-   Si l’assembly *A* n’a pas un nom fort, le nom de l’assembly friend doit être constitué uniquement du nom de l’assembly. Pour plus d’informations, consultez [Guide pratique pour créer des assemblys friend non signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Si l’assembly *B* porte un nom fort, vous devez spécifier la clé de nom fort de l’assembly *B* en utilisant le paramètre de projet ou l’option de compilateur `/keyfile`. Pour plus d’informations, consultez [Guide pratique pour créer des assemblys friend signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 La classe <xref:System.Security.Permissions.StrongNameIdentityPermission> offre également la possibilité de partager des types, avec les différences suivantes :  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> s’applique à un type individuel, alors qu’un assembly friend s’applique à l’assembly entier.  
  
-   Si vous souhaitez partager des centaines de types de l’assembly *A* avec l’assembly *B*, vous devez ajouter <xref:System.Security.Permissions.StrongNameIdentityPermission> à chacun d’eux. Si vous utilisez un assembly friend, vous n’aurez à déclarer la relation d’assembly friend qu’une seule fois.  
  
-   Si vous utilisez <xref:System.Security.Permissions.StrongNameIdentityPermission>, les types que vous voulez partager doivent être déclarés comme publics. Si vous utilisez un assembly friend, les types partagés sont déclarés comme `internal`.  
  
 Pour plus d’informations sur la façon d’accéder aux types et aux méthodes `internal` d’un assembly à partir d’un fichier de module (avec l’extension .netmodule), consultez [/moduleassemblyname (C#)](../../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 <xref:System.Security.Permissions.StrongNameIdentityPermission>   
 [Guide pratique pour créer des assemblys friend non signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [Guide pratique pour créer des assemblys friend signés (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Assemblys et le Global Assembly Cache (C#)](../../../../csharp/programming-guide/concepts/assemblies-gac/index.md)   
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)

