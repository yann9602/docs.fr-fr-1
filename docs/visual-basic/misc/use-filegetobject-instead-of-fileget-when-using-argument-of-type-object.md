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
ms.openlocfilehash: 996e8a50f90c738bbc64c200125a785c0e9bcd58
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a><span data-ttu-id="b7864-102">Utiliser &#39; FileGetObject &#39; au lieu de &#39; FileGet &#39; Lorsque l’argument est de type &#39; objet &#39;</span><span class="sxs-lookup"><span data-stu-id="b7864-102">Use &#39;FileGetObject&#39; instead of &#39;FileGet&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="b7864-103">La méthode `FileGet` comprend un argument de type `Object`.</span><span class="sxs-lookup"><span data-stu-id="b7864-103">The `FileGet` method includes an argument of type `Object`.</span></span> <span data-ttu-id="b7864-104">`FileGetObject` doit être utilisé à la place de `FileGet` pour éviter toute ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="b7864-104">`FileGetObject` should be used in place of `FileGet` to avoid ambiguities.</span></span>  
  
 <span data-ttu-id="b7864-105">Notez que les fonctionnalités offertes par `My.Computer.Filesystem` proposent une plus grande facilité d’utilisation et des performances accrues par rapport à `FileGet` ou `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="b7864-105">Notice that the functionality offered by `My.Computer.Filesystem` offers greater ease of use and performance than either `FileGet` or `FileGetObject`.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="b7864-106">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="b7864-106">To correct this error</span></span>  
  
1.  <span data-ttu-id="b7864-107">Remplacez `FileGet` par `FileGetObject`.</span><span class="sxs-lookup"><span data-stu-id="b7864-107">Replace `FileGet` with `FileGetObject`.</span></span>  
  
2.  <span data-ttu-id="b7864-108">Effectuez un cast sur le type de l’argument `Object` pour en faire un type plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="b7864-108">Cast the `Object` argument to a more specific type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7864-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7864-109">See Also</span></span>  
 [<span data-ttu-id="b7864-110">NOT IN BUILD : FileGetObject (fonction)</span><span class="sxs-lookup"><span data-stu-id="b7864-110">NOT IN BUILD: FileGetObject Function</span></span>](http://msdn.microsoft.com/en-us/3eda786b-d1ee-4b44-9dd7-0ea6bff072c0)  
 [<span data-ttu-id="b7864-111">My.Computer.FileSystem (objet)</span><span class="sxs-lookup"><span data-stu-id="b7864-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)
