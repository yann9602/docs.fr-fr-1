---
title: "Comment : déterminer si un objet .NET Standard est sérialisable"
description: "Montre comment déterminer si un type .NET Standard peut être sérialisé en cours d’exécution."
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7c44e350ad4e561f03bf6c598172058a0a9ca41e
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="ff218-103">Comment : déterminer si un objet .NET Standard est sérialisable</span><span class="sxs-lookup"><span data-stu-id="ff218-103">How to: Determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="ff218-104">.NET Standard est une spécification qui définit les types et membres qui doivent être présents sur des implémentations spécifiques de .NET qui se conforment à cette version de la norme.</span><span class="sxs-lookup"><span data-stu-id="ff218-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="ff218-105">Toutefois, .NET Standard ne définit pas si un type est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="ff218-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="ff218-106">Les types définis dans la bibliothèque Standard .NET ne sont pas marqués avec le <xref:System.SerializableAttribute> attribut.</span><span class="sxs-lookup"><span data-stu-id="ff218-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="ff218-107">Au lieu de cela, les implémentations .NET spécifiques, telles que le .NET Framework et le .NET Core, sont libres de déterminer si un type particulier est sérialisable.</span><span class="sxs-lookup"><span data-stu-id="ff218-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="ff218-108">Si vous avez développé une bibliothèque qui cible .NET Standard, la bibliothèque peut être consommée par une implémentation .NET qui prend en charge .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ff218-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="ff218-109">Cela signifie que vous ne pouvez pas savoir à l’avance si un type particulier est sérialisable ; Vous ne pouvez déterminer s’il est sérialisable en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ff218-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="ff218-110">Vous pouvez déterminer si un objet est sérialisable lors de l’exécution en récupérant la valeur de la <xref:System.Type.IsSerializable> propriété d’un <xref:System.Type> objet qui représente le type de l’objet.</span><span class="sxs-lookup"><span data-stu-id="ff218-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="ff218-111">L’exemple suivant fournit une implémentation.</span><span class="sxs-lookup"><span data-stu-id="ff218-111">The following example provides one implementation.</span></span> <span data-ttu-id="ff218-112">Il définit un `IsSerializable(Object)` méthode d’extension qui indique si les <xref:System.Object> instance peut être sérialisée.</span><span class="sxs-lookup"><span data-stu-id="ff218-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="ff218-113">Vous pouvez ensuite passer n’importe quel objet à la méthode pour déterminer si elle peut être sérialisé et désérialisé sur l’implémentation actuelle de .NET, comme le montre l’exemple suivant :</span><span class="sxs-lookup"><span data-stu-id="ff218-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a><span data-ttu-id="ff218-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ff218-114">See also</span></span>

<span data-ttu-id="ff218-115">[Sérialisation binaire](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="ff218-115">[Binary serialization](binary-serialization.md) </span></span>  
<span data-ttu-id="ff218-116"><xref:System.SerializableAttribute?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="ff218-116"><xref:System.SerializableAttribute?displayProperty=fullName></span></span>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
