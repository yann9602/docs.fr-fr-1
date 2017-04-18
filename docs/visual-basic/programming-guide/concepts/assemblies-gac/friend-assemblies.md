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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: c6e01ae91b9d5d875bb618993cd9eda82db59399
ms.lasthandoff: 03/13/2017

---
# <a name="friend-assemblies-visual-basic"></a>Assemblys friend (Visual Basic)
A *assembly friend* est un assembly qui est accessible d’un autre assembly [ami](../../../../visual-basic/language-reference/modifiers/friend.md) types et membres. Si vous identifiez un assembly en tant qu’assembly friend, vous n’avez plus marquer des types et membres publics pour qu’ils accessibles par d’autres assemblys. Ceci est particulièrement pratique dans les scénarios suivants :  
  
-   Pendant le test unitaire, lorsque le code de test s’exécute dans un assembly séparé, mais requiert l’accès aux membres de l’assembly en cours de test qui sont marqués comme `Friend`.  
  
-   Lorsque vous développez une bibliothèque de classes et ajouts à la bibliothèque sont contenus dans des assemblys séparés, mais nécessitent l’accès aux membres des assemblys existants qui sont marqués comme `Friend`.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut pour identifier un ou plusieurs assemblys friend pour un assembly donné.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> L’exemple suivant utilise le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>d’attribut dans l’assembly A et spécifie l’assembly `AssemblyB` comme assembly friend.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Cela donne l’assembly `AssemblyB` accès à tous les types et membres de l’assembly A qui sont marqués comme `Friend`.  
  
> [!NOTE]
>  Lorsque vous compilez un assembly (assembly `AssemblyB`) qui accédera aux types ou membres internes d’un autre assembly (assembly *A*), vous devez spécifier explicitement le nom du fichier de sortie (.exe ou .dll) à l’aide de la **/out** option du compilateur. Cela est nécessaire, car le compilateur n’a pas encore généré le nom de l’assembly qu’il génère au moment où qu'il est lié aux références externes. Pour plus d’informations, consultez [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
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
  
 Seuls les assemblys que vous spécifiez explicitement comme Friend peuvent accéder aux `Friend` types et membres. Par exemple, si l’assembly B est un ami de l’assembly A et assembly C référence l’assembly B, C n’a pas accès à `Friend` types dans A.  
  
 Le compilateur effectue une validation de base du nom de l’assembly friend passé à le <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> Si assembly *A* déclare *B* comme assembly friend, les règles de validation sont les suivantes :  
  
-   Si assembly *A* porte un nom, assembly fort *B* doit également être un nom fort. Le nom de l’assembly friend qui est passé à l’attribut doit être composé du nom de l’assembly et la clé publique de la clé de nom fort qui est utilisée pour signer l’assembly *B*.  
  
     Le nom de l’assembly friend qui est passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>attribut ne peut pas être le nom fort de l’assembly *B*: n’incluent pas la version de l’assembly, culture, architecture ou jeton de clé publique.</xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
  
-   Si assembly *A* n’est pas fort nommé, le nom de l’assembly friend doit se composer d’uniquement le nom de l’assembly. Pour plus d’informations, consultez [Comment : créer des assemblys non signés Friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Si assembly *B* porte un nom fort, vous devez spécifier la clé de nom fort pour l’assembly *B* en utilisant le paramètre du projet ou la ligne de commande `/keyfile` option du compilateur. Pour plus d’informations, consultez [Comment : créer les assemblys signés du Friend (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 La <xref:System.Security.Permissions.StrongNameIdentityPermission>classe fournit également la possibilité de partager des types, avec les différences suivantes :</xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission>s’applique à un type individuel, alors qu’un assembly friend s’applique à l’assembly entier.</xref:System.Security.Permissions.StrongNameIdentityPermission>  
  
-   S’il existe des centaines de types dans l’assembly *A* que vous souhaitez partager avec l’assembly *B*, vous devez ajouter <xref:System.Security.Permissions.StrongNameIdentityPermission>à chacun d’eux.</xref:System.Security.Permissions.StrongNameIdentityPermission> Si vous utilisez un assembly friend, vous devez seulement déclarer la relation « friend » qu’une seule fois.  
  
-   Si vous utilisez <xref:System.Security.Permissions.StrongNameIdentityPermission>, les types que vous voulez partager doivent être déclarés comme étant public.</xref:System.Security.Permissions.StrongNameIdentityPermission> Si vous utilisez un assembly friend, les types partagés sont déclarés comme `Friend`.  
  
 Pour plus d’informations sur l’accès d’un assembly à `Friend` types et méthodes à partir d’un fichier de module (fichier avec l’extension .netmodule), consultez [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute></xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>   
 <xref:System.Security.Permissions.StrongNameIdentityPermission></xref:System.Security.Permissions.StrongNameIdentityPermission>   
 [Comment : créer des assemblys Friend non signés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)   
 [Comment : créer des assemblys Friend signés (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)   
 [Assemblys et le Global Assembly Cache (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [Concepts de programmation](../../../../visual-basic/programming-guide/concepts/index.md)
