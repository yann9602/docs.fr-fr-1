---
title: "Un appel à une propriété ou une méthode ne peut pas utiliser une référence vers un objet privé, que ce soit comme argument ou comme valeur de retour"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cce2bc67beb7e4ac0664b5b7240f5eb3ea0204f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="c4696-102">Un appel à une propriété ou une méthode ne peut pas utiliser une référence vers un objet privé, que ce soit comme argument ou comme valeur de retour</span><span class="sxs-lookup"><span data-stu-id="c4696-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="c4696-103">Cette erreur peut avoir plusieurs causes, dont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="c4696-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="c4696-104">Un client a appelé une propriété ou méthode d’un composant hors processus et a tenté de passer une référence à un objet privé comme l’un des arguments.</span><span class="sxs-lookup"><span data-stu-id="c4696-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="c4696-105">Un composant hors processus a appelé une méthode de rappel sur son client et a tenté de passer une référence à un objet privé.</span><span class="sxs-lookup"><span data-stu-id="c4696-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="c4696-106">Un composant hors processus a tenté de passer une référence à un objet privé comme argument d’un événement qu’il a déclenché.</span><span class="sxs-lookup"><span data-stu-id="c4696-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="c4696-107">Un client a tenté d’assigner une référence d’objet privé à un argument `ByRef` d’un événement qu’il gérait.</span><span class="sxs-lookup"><span data-stu-id="c4696-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c4696-108">Pour corriger cette erreur</span><span class="sxs-lookup"><span data-stu-id="c4696-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="c4696-109">Supprimez la référence.</span><span class="sxs-lookup"><span data-stu-id="c4696-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4696-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c4696-110">See Also</span></span>  
 [<span data-ttu-id="c4696-111">Private</span><span class="sxs-lookup"><span data-stu-id="c4696-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
