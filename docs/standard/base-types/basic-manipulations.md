---
title: "Comment : effectuer des manipulations de chaînes de base dans .NET Framework"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: strings [.NET Framework], examples
ms.assetid: 121d1eae-251b-44c0-8818-57da04b8215e
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ee9c00d02b7b5d1f391ce60f843c18445efd6edc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-perform-basic-string-manipulations-in-net"></a><span data-ttu-id="e9ab0-102">Comment : effectuer des Manipulations de chaînes de base dans .NET</span><span class="sxs-lookup"><span data-stu-id="e9ab0-102">How to: Perform Basic String Manipulations in .NET</span></span>
<span data-ttu-id="e9ab0-103">L’exemple suivant utilise certaines des méthodes décrites dans le [des opérations de chaîne de base](../../../docs/standard/base-types/basic-string-operations.md) rubriques pour construire une classe qui effectue les manipulations de chaînes d’une manière qui peut être trouvée dans une application réelle.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-103">The following example uses some of the methods discussed in the [Basic String Operations](../../../docs/standard/base-types/basic-string-operations.md) topics to construct a class that performs string manipulations in a manner that might be found in a real-world application.</span></span> <span data-ttu-id="e9ab0-104">La classe `MailToData` stocke le nom et l’adresse d’une personne dans des propriétés séparées et fournit un moyen de combiner les champs `City`, `State` et `Zip` dans une seule chaîne à montrer à l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-104">The `MailToData` class stores the name and address of an individual in separate properties and provides a way to combine the `City`, `State`, and `Zip` fields into a single string for display to the user.</span></span> <span data-ttu-id="e9ab0-105">De plus, la classe permet à l’utilisateur d’entrer la ville, l’état et le code postal dans une chaîne unique ; l’application analyse automatiquement la chaîne unique et entre les informations appropriées dans la propriété correspondante.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-105">Furthermore, the class allows the user to enter the city, state, and ZIP Code information as a single string; the application automatically parses the single string and enters the proper information into the corresponding property.</span></span>  
  
 <span data-ttu-id="e9ab0-106">Pour plus de simplicité, cet exemple utilise une application console avec une interface de ligne de commande.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-106">For simplicity, this example uses a console application with a command-line interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9ab0-107">Exemple</span><span class="sxs-lookup"><span data-stu-id="e9ab0-107">Example</span></span>  
 [!code-csharp[Conceptual.String.BasicOps#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/basicops.cs#1)]
 [!code-vb[Conceptual.String.BasicOps#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/basicops.vb#1)]  
  
 <span data-ttu-id="e9ab0-108">Quand le code précédent est exécuté, l’utilisateur est invité à entrer son nom et son adresse.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-108">When the preceding code is executed, the user is asked to enter his or her name and address.</span></span> <span data-ttu-id="e9ab0-109">L’application place les informations dans les propriétés appropriées et les montre à l’utilisateur, en créant une chaîne unique qui affiche la ville, l’état et le code postal.</span><span class="sxs-lookup"><span data-stu-id="e9ab0-109">The application places the information in the appropriate properties and displays the information back to the user, creating a single string that displays the city, state, and ZIP Code information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9ab0-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e9ab0-110">See Also</span></span>  
 [<span data-ttu-id="e9ab0-111">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="e9ab0-111">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
