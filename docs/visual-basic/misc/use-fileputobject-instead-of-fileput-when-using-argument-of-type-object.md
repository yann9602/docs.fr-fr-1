---
title: "Utiliser &#39; FilePutObject &#39; au lieu de &#39; FilePut &#39; Lorsque l’argument est de type &#39; objet &#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrUseFilePutObject
ms.assetid: d207b9b7-5898-4c13-8b03-9feefac5f726
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8cba4af206e2dbf767fdb883ec81229a67842c57
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="use-39fileputobject39-instead-of-39fileput39-when-using-argument-of-type-39object39"></a><span data-ttu-id="17eb6-102">Utiliser &#39; FilePutObject &#39; au lieu de &#39; FilePut &#39; Lorsque l’argument est de type &#39; objet &#39;</span><span class="sxs-lookup"><span data-stu-id="17eb6-102">Use &#39;FilePutObject&#39; instead of &#39;FilePut&#39; when using argument of type &#39;Object&#39;</span></span>
<span data-ttu-id="17eb6-103">Le `FilePut` méthode inclut un argument de type `Object`.</span><span class="sxs-lookup"><span data-stu-id="17eb6-103">The `FilePut` method includes an argument of type `Object`.</span></span> <span data-ttu-id="17eb6-104">`FilePutObject` doit être utilisé à la place de `FilePut` pour éviter toute ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="17eb6-104">`FilePutObject` should be used in place of `FilePut` to avoid ambiguities.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="17eb6-105">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="17eb6-105">To correct this error</span></span>  
  
-   <span data-ttu-id="17eb6-106">Remplacez `FilePut` par `FilePutObject`.</span><span class="sxs-lookup"><span data-stu-id="17eb6-106">Replace `FilePut` with `FilePutObject`.</span></span>  
  
-   <span data-ttu-id="17eb6-107">Effectuez un cast sur le type de l’argument `Object` pour en faire un type plus spécifique.</span><span class="sxs-lookup"><span data-stu-id="17eb6-107">Cast the `Object` argument to a more specific type.</span></span>  
  
-   <span data-ttu-id="17eb6-108">Utilisez les fonctionnalités disponibles dans l’objet `My.Computer.FileSystem` .</span><span class="sxs-lookup"><span data-stu-id="17eb6-108">Use the functionality available in the `My.Computer.FileSystem` object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17eb6-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="17eb6-109">See Also</span></span>  
 [<span data-ttu-id="17eb6-110">NOT IN BUILD : FilePutObject (fonction)</span><span class="sxs-lookup"><span data-stu-id="17eb6-110">NOT IN BUILD: FilePutObject Function</span></span>](http://msdn.microsoft.com/en-us/a0f52a1c-5ecc-4945-b18c-03147af61d6b)  
 [<span data-ttu-id="17eb6-111">My.Computer.FileSystem (objet)</span><span class="sxs-lookup"><span data-stu-id="17eb6-111">My.Computer.FileSystem Object</span></span>](../../visual-basic/language-reference/objects/my-computer-filesystem-object.md)  
 [<span data-ttu-id="17eb6-112">My.Computer.FileSystem.WriteAllBytes, méthode</span><span class="sxs-lookup"><span data-stu-id="17eb6-112">My.Computer.FileSystem.WriteAllBytes Method</span></span>](http://msdn.microsoft.com/en-us/b1a24dc1-eac8-4e22-8ffa-cc3bacbaf826)
