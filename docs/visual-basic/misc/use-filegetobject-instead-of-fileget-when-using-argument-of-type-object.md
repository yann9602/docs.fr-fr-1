---
title: "Utiliser &#39; FileGetObject &#39; au lieu de &#39; FileGet &#39; Lorsque l’argument est de type &#39; objet &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 090b8088-895a-482a-9362-606596bac304
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c5be466a8a0339bdb57818755d85a26d632d774
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="6cd39-102">Utiliser &#39; FileGetObject &#39; au lieu de &#39; FileGet &#39; Lorsque l’argument est de type &#39; objet &#39;</span><span class="sxs-lookup"><span data-stu-id="6cd39-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="6cd39-103">La méthode `FileGet` comprend un argument de type `Object`.</span><span class="sxs-lookup"><span data-stu-id="6cd39-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="6cd39-104">`FileGetObject` doit être utilisé à la place de `FileGet` pour éviter toute ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="6cd39-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="6cd39-105">Notez que les fonctionnalités offertes par `My.Computer.Filesystem` proposent une plus grande facilité d’utilisation et des performances accrues par rapport à `FileGet` ou `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="6cd39-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6cd39-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="6cd39-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="6cd39-107">Remplacez `FileGet` par `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="6cd39-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="6cd39-108">Effectuez un cast sur le type de l’argument `Object` pour en faire un type plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="6cd39-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd39-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6cd39-109">See Also</span></span>  
   
 [<span data-ttu-id="6cd39-110">My.Computer.FileSystem</span><span class="sxs-lookup"><span data-stu-id="6cd39-110">My.Computer.FileSystem</span></span>](xref:Microsoft.VisualBasic.FileIO.FileSystem)
