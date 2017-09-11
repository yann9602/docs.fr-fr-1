---
title: "Réflexion (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
ms.assetid: d991bc0f-d16a-4ac5-9351-70e5c5b9891b
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: acfcb519128de0d616757398c94ec70dc7de6ef1
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="reflection-visual-basic"></a><span data-ttu-id="b2197-102">Réflexion (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2197-102">Reflection (Visual Basic)</span></span>
<span data-ttu-id="b2197-103">La réflexion fournit des objets (de type <xref:System.Type>) qui décrivent les types, les modules et assemblys.</xref:System.Type></span><span class="sxs-lookup"><span data-stu-id="b2197-103">Reflection provides objects (of type <xref:System.Type>) that describe assemblies, modules and types.</span></span> <span data-ttu-id="b2197-104">Vous pouvez utiliser la réflexion pour dynamiquement créer une instance d’un type, le type de liaison à un objet existant, obtenir le type d’un objet existant et appeler ses méthodes ou accéder à ses champs et propriétés.</span><span class="sxs-lookup"><span data-stu-id="b2197-104">You can use reflection to dynamically create an instance of a type, bind the type to an existing object, or get the type from an existing object and invoke its methods or access its fields and properties.</span></span> <span data-ttu-id="b2197-105">Si vous utilisez des attributs dans votre code, la réflexion vous permet d’y accéder.</span><span class="sxs-lookup"><span data-stu-id="b2197-105">If you are using attributes in your code, reflection enables you to access them.</span></span> <span data-ttu-id="b2197-106">Pour plus d’informations, consultez [attributs](https://msdn.microsoft.com/library/5x6cd29c).</span><span class="sxs-lookup"><span data-stu-id="b2197-106">For more information, see [Attributes](https://msdn.microsoft.com/library/5x6cd29c).</span></span>  
  
 <span data-ttu-id="b2197-107">Voici un exemple simple de réflexion à l’aide de la méthode statique `GetType` , héritée par tous les types à partir de la `Object` classe - pour obtenir le type d’une variable de base :</span><span class="sxs-lookup"><span data-stu-id="b2197-107">Here's a simple example of reflection using the static method `GetType` - inherited by all types from the `Object` base class - to obtain the type of a variable:</span></span>  
  
```vb  
' Using GetType to obtain type information:  
Dim i As Integer = 42  
Dim type As System.Type = i.GetType()  
System.Console.WriteLine(type)  
```  
  
 <span data-ttu-id="b2197-108">Le résultat est :</span><span class="sxs-lookup"><span data-stu-id="b2197-108">The output is:</span></span>  
  
 `System.Int32`  
  
 <span data-ttu-id="b2197-109">L’exemple suivant utilise la réflexion pour obtenir le nom complet de l’assembly chargé.</span><span class="sxs-lookup"><span data-stu-id="b2197-109">The following example uses reflection to obtain the full name of the loaded assembly.</span></span>  
  
```vb  
' Using Reflection to get information from an Assembly:  
Dim info As System.Reflection.Assembly = GetType(System.Int32).Assembly  
System.Console.WriteLine(info)  
```  
  
 <span data-ttu-id="b2197-110">Le résultat est :</span><span class="sxs-lookup"><span data-stu-id="b2197-110">The output is:</span></span>  
  
 `mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089`  
  
## <a name="reflection-overview"></a><span data-ttu-id="b2197-111">Vue d’ensemble de la réflexion</span><span class="sxs-lookup"><span data-stu-id="b2197-111">Reflection Overview</span></span>  
 <span data-ttu-id="b2197-112">La réflexion est utile dans les situations suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2197-112">Reflection is useful in the following situations:</span></span>  
  
-   <span data-ttu-id="b2197-113">Lorsque vous devez accéder aux attributs dans les métadonnées de votre programme.</span><span class="sxs-lookup"><span data-stu-id="b2197-113">When you have to access attributes in your program's metadata.</span></span> <span data-ttu-id="b2197-114">Pour plus d’informations, consultez [récupération des informations stockées dans les attributs](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).</span><span class="sxs-lookup"><span data-stu-id="b2197-114">For more information, see [Retrieving Information Stored in Attributes](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c).</span></span>  
  
-   <span data-ttu-id="b2197-115">Pour examiner et instancier des types dans un assembly.</span><span class="sxs-lookup"><span data-stu-id="b2197-115">For examining and instantiating types in an assembly.</span></span>  
  
-   <span data-ttu-id="b2197-116">Pour la création de nouveaux types pendant l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b2197-116">For building new types at runtime.</span></span> <span data-ttu-id="b2197-117">Utiliser des classes dans <xref:System.Reflection.Emit>.</xref:System.Reflection.Emit></span><span class="sxs-lookup"><span data-stu-id="b2197-117">Use classes in <xref:System.Reflection.Emit>.</span></span>  
  
-   <span data-ttu-id="b2197-118">Pour effectuer une liaison tardive, l’accès aux méthodes sur les types créés au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="b2197-118">For performing late binding, accessing methods on types created at run time.</span></span> <span data-ttu-id="b2197-119">Consultez la rubrique [à l’aide de Types et de chargement dynamique](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).</span><span class="sxs-lookup"><span data-stu-id="b2197-119">See the topic [Dynamically Loading and Using Types](http://msdn.microsoft.com/library/db985bec-5942-40ec-b13a-771ae98623dc).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="b2197-120">Rubriques connexes</span><span class="sxs-lookup"><span data-stu-id="b2197-120">Related Sections</span></span>  
 <span data-ttu-id="b2197-121">Pour plus d'informations :</span><span class="sxs-lookup"><span data-stu-id="b2197-121">For more information:</span></span>  
  
-   [<span data-ttu-id="b2197-122">Réflexion</span><span class="sxs-lookup"><span data-stu-id="b2197-122">Reflection</span></span>](http://msdn.microsoft.com/library/d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775)  
  
-   [<span data-ttu-id="b2197-123">Affichage des informations de Type</span><span class="sxs-lookup"><span data-stu-id="b2197-123">Viewing Type Information</span></span>](http://msdn.microsoft.com/library/7e7303a9-4064-4738-b4e7-b75974ed70d2)  
  
-   [<span data-ttu-id="b2197-124">Réflexion et Types génériques</span><span class="sxs-lookup"><span data-stu-id="b2197-124">Reflection and Generic Types</span></span>](http://msdn.microsoft.com/library/f7180fc5-dd41-42d4-8a8e-1b34288e06de)  
  
-   <span data-ttu-id="b2197-125"><xref:System.Reflection.Emit></xref:System.Reflection.Emit></span><span class="sxs-lookup"><span data-stu-id="b2197-125"><xref:System.Reflection.Emit></span></span>  
  
-   [<span data-ttu-id="b2197-126">Récupération des informations stockées dans les attributs</span><span class="sxs-lookup"><span data-stu-id="b2197-126">Retrieving Information Stored in Attributes</span></span>](http://msdn.microsoft.com/library/37dfe4e3-7da0-48b6-a3d9-398981524e1c)  
  
## <a name="see-also"></a><span data-ttu-id="b2197-127">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2197-127">See Also</span></span>  
 <span data-ttu-id="b2197-128">[Guide de programmation Visual Basic](../../../visual-basic/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="b2197-128">[Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md) </span></span>  
<span data-ttu-id="b2197-129"> [Assemblys dans le Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)</span><span class="sxs-lookup"><span data-stu-id="b2197-129"> [Assemblies in the Common Language Runtime](https://msdn.microsoft.com/library/k3677y81)</span></span>
