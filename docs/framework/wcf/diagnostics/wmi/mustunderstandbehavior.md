---
title: MustUnderstandBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 911ed04a-c4b8-4c72-a5c3-fc7b4e3b4348
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b6838c6ce98e0d373a45c136b12bdedbd8c9eb6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="df8d7-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="df8d7-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="df8d7-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="df8d7-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df8d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df8d7-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="df8d7-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="df8d7-105">Methods</span></span>  
 <span data-ttu-id="df8d7-106">La classe MustUnderstandBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="df8d7-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="df8d7-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="df8d7-107">Properties</span></span>  
 <span data-ttu-id="df8d7-108">La classe MustUnderstandBehavior a la propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="df8d7-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="df8d7-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="df8d7-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="df8d7-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="df8d7-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="df8d7-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="df8d7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df8d7-112">Lorsque cette propriété a la valeur `true`, tous les en-têtes SOAP avec l'attribut `MustUnderstand` qui ne sont pas gérés font en sorte que le comportement lève une exception.</span><span class="sxs-lookup"><span data-stu-id="df8d7-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df8d7-113">Configuration requise</span><span class="sxs-lookup"><span data-stu-id="df8d7-113">Requirements</span></span>  
  
|<span data-ttu-id="df8d7-114">MOF</span><span class="sxs-lookup"><span data-stu-id="df8d7-114">MOF</span></span>|<span data-ttu-id="df8d7-115">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="df8d7-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="df8d7-116">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="df8d7-116">Namespace</span></span>|<span data-ttu-id="df8d7-117">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="df8d7-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df8d7-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="df8d7-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
