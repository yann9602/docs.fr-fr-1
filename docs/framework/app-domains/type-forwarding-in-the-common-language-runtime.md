---
title: Transfert de type dans le Common Language Runtime
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 18e580a67d5a983d61ab3c0b71cfc7d294468010
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="94e8f-102">Transfert de type dans le Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="94e8f-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="94e8f-103">Le transfert de type vous permet de déplacer un type vers un autre assembly sans avoir à recompiler les applications utilisant l’assembly d’origine.</span><span class="sxs-lookup"><span data-stu-id="94e8f-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="94e8f-104">Par exemple, supposons qu’une application utilise la classe `Example` dans un assembly appelé `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="94e8f-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="94e8f-105">Les développeurs de `Utility.dll` peuvent décider de refactoriser l’assembly, et dans le cadre du processus sont susceptibles de déplacer la classe `Example` vers un autre assembly.</span><span class="sxs-lookup"><span data-stu-id="94e8f-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="94e8f-106">Si l’ancienne version de `Utility.dll` est remplacée par la nouvelle version de `Utility.dll` et son assembly auxiliaire, l’application utilisant la classe `Example` est mise en échec car elle ne peut pas localiser la classe `Example` dans la nouvelle version de `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="94e8f-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="94e8f-107">Les développeurs de `Utility.dll` peuvent éviter ce problème en transférant les demandes pour la classe `Example` à l’aide de l’attribut <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>.</span><span class="sxs-lookup"><span data-stu-id="94e8f-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="94e8f-108">Si l’attribut a été appliqué à la nouvelle version de `Utility.dll`, les demandes associées à la classe `Example` sont transmises à l’assembly qui contient la classe.</span><span class="sxs-lookup"><span data-stu-id="94e8f-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="94e8f-109">L’application existante continue à fonctionner normalement, sans nouvelle compilation.</span><span class="sxs-lookup"><span data-stu-id="94e8f-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94e8f-110">Dans .NET Framework version 2.0, il est impossible de transférer des types provenant d’assemblys écrits en Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="94e8f-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="94e8f-111">Toutefois, une application écrite en Visual Basic peut utiliser des types transférés.</span><span class="sxs-lookup"><span data-stu-id="94e8f-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="94e8f-112">Autrement dit, si l’application utilise un assembly codé en C# ou C++ et qu’un type de cet assembly est transmis à un autre assembly, l’application Visual Basic peut utiliser le type transféré.</span><span class="sxs-lookup"><span data-stu-id="94e8f-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="94e8f-113">Transfert de types</span><span class="sxs-lookup"><span data-stu-id="94e8f-113">Forwarding Types</span></span>  
 <span data-ttu-id="94e8f-114">Le transfert de type se décompose en quatre étapes :</span><span class="sxs-lookup"><span data-stu-id="94e8f-114">There are four steps to forwarding a type:</span></span>  
  
1.  <span data-ttu-id="94e8f-115">Déplacez le code source associé au type de l’assembly d’origine à l’assembly de destination.</span><span class="sxs-lookup"><span data-stu-id="94e8f-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2.  <span data-ttu-id="94e8f-116">Dans l’assembly où se trouvait le type, ajoutez un <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pour le type qui a été déplacé.</span><span class="sxs-lookup"><span data-stu-id="94e8f-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="94e8f-117">Le code suivant représente l’attribut pour un type nommé `Example` qui a été déplacé.</span><span class="sxs-lookup"><span data-stu-id="94e8f-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  <span data-ttu-id="94e8f-118">Compilez l’assembly qui contient désormais le type.</span><span class="sxs-lookup"><span data-stu-id="94e8f-118">Compile the assembly that now contains the type.</span></span>  
  
4.  <span data-ttu-id="94e8f-119">Recompilez l’assembly dans lequel le type se trouvait, avec une référence à l’assembly qui contient désormais le type.</span><span class="sxs-lookup"><span data-stu-id="94e8f-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="94e8f-120">Par exemple, si vous compilez un fichier C# de la ligne de commande, utilisez l’option [/reference (Options du compilateur C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) pour spécifier l’assembly contenant le type.</span><span class="sxs-lookup"><span data-stu-id="94e8f-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="94e8f-121">Dans C++, utilisez la directive [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) dans le fichier source pour spécifier l’assembly contenant le type.</span><span class="sxs-lookup"><span data-stu-id="94e8f-121">In C++, use the [#using](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94e8f-122">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94e8f-122">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [<span data-ttu-id="94e8f-123">Transfert de type (C++-CLI)</span><span class="sxs-lookup"><span data-stu-id="94e8f-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)  
 [<span data-ttu-id="94e8f-124">Directive #using</span><span class="sxs-lookup"><span data-stu-id="94e8f-124">#using Directive</span></span>](http://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
