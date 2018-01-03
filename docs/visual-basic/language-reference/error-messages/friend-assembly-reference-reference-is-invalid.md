---
title: "Référence d’assembly friend &lt;référence&gt; n’est pas valide"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31535
- bc31535
helpviewer_keywords: BC31535
ms.assetid: 6540c1d0-bb19-4051-a579-2e4f9094585e
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ab1c7c5cc7a7f4ad899df7722769238e05d96e6b
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="0cd55-102">Référence d’assembly friend &lt;référence&gt; n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="0cd55-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="0cd55-103">Référence d’assembly friend \<référence > n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="0cd55-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="0cd55-104">Les assemblys signés avec un nom fort doivent spécifier une clé publique dans leurs déclarations InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="0cd55-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="0cd55-105">Le nom d’assembly passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut identifie un assembly avec nom fort, mais il n’inclut pas un `PublicKey` attribut.</span><span class="sxs-lookup"><span data-stu-id="0cd55-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="0cd55-106">**ID d’erreur :** BC31535</span><span class="sxs-lookup"><span data-stu-id="0cd55-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0cd55-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="0cd55-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="0cd55-108">Déterminez la clé publique de l’assembly friend avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="0cd55-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="0cd55-109">Inclure la clé publique comme partie du nom de l’assembly passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut à l’aide de la `PublicKey` attribut.</span><span class="sxs-lookup"><span data-stu-id="0cd55-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd55-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cd55-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="0cd55-111">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="0cd55-111">Friend Assemblies</span></span>](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 

