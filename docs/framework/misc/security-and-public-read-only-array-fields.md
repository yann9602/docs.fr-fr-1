---
title: "Sécurité et champs de tableau en lecture seule publics"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: security [.NET Framework], public read-only array fields
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d86d054d3a5a4e10b8efcc3292f3a18ea37f9b87
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="security-and-public-read-only-array-fields"></a><span data-ttu-id="b5ce1-102">Sécurité et champs de tableau en lecture seule publics</span><span class="sxs-lookup"><span data-stu-id="b5ce1-102">Security and Public Read-only Array Fields</span></span>
<span data-ttu-id="b5ce1-103">Utilisez jamais les champs de tableau publics en lecture seule à partir de bibliothèques managées pour définir le comportement de limites ou la sécurité de vos applications, car les champs de tableau publics en lecture seule peuvent être modifiés.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-103">Never use read-only public array fields from managed libraries to define the boundary behavior or security of your applications because read-only public array fields can be modified.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5ce1-104">Notes</span><span class="sxs-lookup"><span data-stu-id="b5ce1-104">Remarks</span></span>  
 <span data-ttu-id="b5ce1-105">Certaines classes .NET framework incluent des champs publics en lecture seule qui contiennent des paramètres spécifiques à la plateforme limite.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-105">Some .NET framework classes include read-only public fields that contain platform-specific boundary parameters.</span></span>  <span data-ttu-id="b5ce1-106">Par exemple, le <xref:System.IO.Path.InvalidPathChars> champ est un tableau qui décrit les caractères qui ne sont pas autorisés dans une chaîne de chemin d’accès de fichier.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-106">For example, the <xref:System.IO.Path.InvalidPathChars> field is an array that describes the characters that are not allowed in a file path string.</span></span>  <span data-ttu-id="b5ce1-107">De nombreux champs semblables sont présents dans le .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-107">Many similar fields are present throughout the .NET Framework.</span></span>  
  
 <span data-ttu-id="b5ce1-108">Les valeurs des champs publics en lecture seule comme <xref:System.IO.Path.InvalidPathChars> peut être modifié par votre code ou le code qui partage le domaine d’application de votre code.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-108">The values of public read-only fields like <xref:System.IO.Path.InvalidPathChars> can be modified by your code or code that shares your code’s application domain.</span></span>  <span data-ttu-id="b5ce1-109">Vous ne devez pas utiliser les champs de tableau publics en lecture seule comme suit pour définir le comportement des limites de vos applications.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-109">You should not use read-only public array fields like this to define the boundary behavior of your applications.</span></span>  <span data-ttu-id="b5ce1-110">Si vous le faites, un code malveillant peut modifier les définitions des limites et votre code de façon inattendue.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-110">If you do, malicious code can alter the boundary definitions and use your code in unexpected ways.</span></span>  
  
 <span data-ttu-id="b5ce1-111">Dans la version 2.0 et ultérieures du .NET Framework, vous devez utiliser des méthodes qui retournent un nouveau tableau au lieu d’utiliser les champs de tableau publics.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-111">In version 2.0 and later of the .NET Framework, you should use methods that return a new array instead of using public array fields.</span></span>  <span data-ttu-id="b5ce1-112">Par exemple, au lieu d’utiliser le <xref:System.IO.Path.InvalidPathChars> champ, vous devez utiliser le <xref:System.IO.Path.GetInvalidPathChars%2A> (méthode).</span><span class="sxs-lookup"><span data-stu-id="b5ce1-112">For example, instead of using the <xref:System.IO.Path.InvalidPathChars> field, you should use the <xref:System.IO.Path.GetInvalidPathChars%2A> method.</span></span>  
  
 <span data-ttu-id="b5ce1-113">Notez que les types .NET Framework n’utilisent pas de champs publics pour définir des types de limites en interne.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-113">Note that the .NET Framework types do not use the public fields to define boundary types internally.</span></span>  <span data-ttu-id="b5ce1-114">Au lieu de cela, le .NET Framework utilise des champs privés séparés.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-114">Instead, the .NET Framework uses separate private fields.</span></span>  <span data-ttu-id="b5ce1-115">Modification des valeurs de ces champs publics ne modifie pas le comportement des types .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b5ce1-115">Changing the values of these public fields does not alter the behavior of .NET Framework types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5ce1-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b5ce1-116">See Also</span></span>  
 [<span data-ttu-id="b5ce1-117">Instructions de codage sécurisé</span><span class="sxs-lookup"><span data-stu-id="b5ce1-117">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
