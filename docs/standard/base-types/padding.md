---
title: "Remplissage de chaînes dans .NET"
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
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="ee5fc-102">Remplissage de chaînes dans .NET</span><span class="sxs-lookup"><span data-stu-id="ee5fc-102">Padding Strings in .NET</span></span>
<span data-ttu-id="ee5fc-103">Utilisez une des opérations suivantes <xref:System.String> méthodes pour créer une nouvelle chaîne qui se compose d’une chaîne d’origine remplie à l’aide de début ou de fin des caractères à une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="ee5fc-104">Le caractère de remplissage peut être un espace ou un caractère spécifié ; il apparaît donc aligné à droite ou aligné à gauche.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="ee5fc-105">Nom de la méthode</span><span class="sxs-lookup"><span data-stu-id="ee5fc-105">Method name</span></span>|<span data-ttu-id="ee5fc-106">Utilisation</span><span class="sxs-lookup"><span data-stu-id="ee5fc-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="ee5fc-107">Remplit une chaîne à l’aide de caractères de début sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="ee5fc-108">Remplit une chaîne à l’aide de caractères de fin sur une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="ee5fc-109">PadLeft</span><span class="sxs-lookup"><span data-stu-id="ee5fc-109">PadLeft</span></span>  
 <span data-ttu-id="ee5fc-110">Le <xref:System.String.PadLeft%2A?displayProperty=nameWithType> méthode crée une nouvelle chaîne en concaténant suffisamment de caractères de remplissage au début à une chaîne d’origine pour atteindre une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="ee5fc-111">Le <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> méthode utilise l’espace blanc comme caractère de remplissage et la <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> méthode vous permet de spécifier votre propre caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="ee5fc-112">Le code suivant exemple utilise le <xref:System.String.PadLeft%2A> méthode pour créer une nouvelle chaîne qui est de 20 caractères.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="ee5fc-113">L’exemple affiche « `--------Hello World!` » sur la console.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="ee5fc-114">PadRight</span><span class="sxs-lookup"><span data-stu-id="ee5fc-114">PadRight</span></span>  
 <span data-ttu-id="ee5fc-115">Le <xref:System.String.PadRight%2A?displayProperty=nameWithType> méthode crée une nouvelle chaîne en concaténant suffisamment caractères de remplissage de fin à une chaîne d’origine pour atteindre une longueur totale spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="ee5fc-116">Le <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> méthode utilise l’espace blanc comme caractère de remplissage et la <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> méthode vous permet de spécifier votre propre caractère de remplissage.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="ee5fc-117">Le code suivant exemple utilise le <xref:System.String.PadRight%2A> méthode pour créer une nouvelle chaîne qui est de 20 caractères.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="ee5fc-118">L’exemple affiche « `Hello World!--------` » sur la console.</span><span class="sxs-lookup"><span data-stu-id="ee5fc-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ee5fc-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee5fc-119">See Also</span></span>  
 [<span data-ttu-id="ee5fc-120">Opérations de chaînes de base</span><span class="sxs-lookup"><span data-stu-id="ee5fc-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
