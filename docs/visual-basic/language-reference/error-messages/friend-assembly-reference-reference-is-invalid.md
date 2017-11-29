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
ms.openlocfilehash: 39ae94e309ee8d18e6b5317445b7e4b7f6a42af9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="friend-assembly-reference-ltreferencegt-is-invalid"></a><span data-ttu-id="decc4-102">Référence d’assembly friend &lt;référence&gt; n’est pas valide</span><span class="sxs-lookup"><span data-stu-id="decc4-102">Friend assembly reference &lt;reference&gt; is invalid</span></span>
<span data-ttu-id="decc4-103">Référence d’assembly friend \<référence > n’est pas valide.</span><span class="sxs-lookup"><span data-stu-id="decc4-103">Friend assembly reference \<reference> is invalid.</span></span> <span data-ttu-id="decc4-104">Les assemblys signés avec un nom fort doivent spécifier une clé publique dans leurs déclarations InternalsVisibleTo.</span><span class="sxs-lookup"><span data-stu-id="decc4-104">Strong-name signed assemblies must specify a public key in their InternalsVisibleTo declarations.</span></span>  
  
 <span data-ttu-id="decc4-105">Le nom d’assembly passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut identifie un assembly avec nom fort, mais il n’inclut pas un `PublicKey` attribut.</span><span class="sxs-lookup"><span data-stu-id="decc4-105">The assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor identifies a strong-named assembly, but it does not include a `PublicKey` attribute.</span></span>  
  
 <span data-ttu-id="decc4-106">**ID d’erreur :** BC31535</span><span class="sxs-lookup"><span data-stu-id="decc4-106">**Error ID:** BC31535</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="decc4-107">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="decc4-107">To correct this error</span></span>  
  
1.  <span data-ttu-id="decc4-108">Déterminez la clé publique de l’assembly friend avec un nom fort.</span><span class="sxs-lookup"><span data-stu-id="decc4-108">Determine the public key for the strong-named friend assembly.</span></span> <span data-ttu-id="decc4-109">Inclure la clé publique comme partie du nom de l’assembly passé à la <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> constructeur d’attribut à l’aide de la `PublicKey` attribut.</span><span class="sxs-lookup"><span data-stu-id="decc4-109">Include the public key as part of the assembly name passed to the <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> attribute constructor by using the `PublicKey` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="decc4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="decc4-110">See Also</span></span>  
 <xref:System.Reflection.AssemblyName>  
 [<span data-ttu-id="decc4-111">Assemblys friend</span><span class="sxs-lookup"><span data-stu-id="decc4-111">Friend Assemblies</span></span>](http://msdn.microsoft.com/library/df0c70ea-2c2a-4bdc-9526-df951ad2d055)  
 [<span data-ttu-id="decc4-112">Guide pratique : créer des assemblys Friend signés</span><span class="sxs-lookup"><span data-stu-id="decc4-112">How to: Create Signed Friend Assemblies</span></span>](http://msdn.microsoft.com/library/f5542300-58b4-4e1c-b809-8df11e95e69b)
