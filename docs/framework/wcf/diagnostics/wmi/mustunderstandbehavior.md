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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dca98f1d8d5f868285ecf11c01122f795ee6cfd8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="mustunderstandbehavior"></a><span data-ttu-id="ddebc-102">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="ddebc-102">MustUnderstandBehavior</span></span>
<span data-ttu-id="ddebc-103">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="ddebc-103">MustUnderstandBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ddebc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ddebc-104">Syntax</span></span>  
  
```  
class MustUnderstandBehavior : Behavior  
{  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ddebc-105">Méthodes</span><span class="sxs-lookup"><span data-stu-id="ddebc-105">Methods</span></span>  
 <span data-ttu-id="ddebc-106">La classe MustUnderstandBehavior ne définit pas de méthode.</span><span class="sxs-lookup"><span data-stu-id="ddebc-106">The MustUnderstandBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ddebc-107">Propriétés</span><span class="sxs-lookup"><span data-stu-id="ddebc-107">Properties</span></span>  
 <span data-ttu-id="ddebc-108">La classe MustUnderstandBehavior a la propriété suivante :</span><span class="sxs-lookup"><span data-stu-id="ddebc-108">The MustUnderstandBehavior class has the following property:</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="ddebc-109">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="ddebc-109">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="ddebc-110">Type de données : booléen</span><span class="sxs-lookup"><span data-stu-id="ddebc-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="ddebc-111">Type d'accès : lecture seule</span><span class="sxs-lookup"><span data-stu-id="ddebc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ddebc-112">Lorsque cette propriété a la valeur `true`, tous les en-têtes SOAP avec l'attribut `MustUnderstand` qui ne sont pas gérés font en sorte que le comportement lève une exception.</span><span class="sxs-lookup"><span data-stu-id="ddebc-112">When `true`, all SOAP headers with the `MustUnderstand` attribute that are not handled cause the behavior to throw an exception.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddebc-113">Spécifications</span><span class="sxs-lookup"><span data-stu-id="ddebc-113">Requirements</span></span>  
  
|<span data-ttu-id="ddebc-114">MOF</span><span class="sxs-lookup"><span data-stu-id="ddebc-114">MOF</span></span>|<span data-ttu-id="ddebc-115">Déclaré dans Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ddebc-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ddebc-116">Espace de noms</span><span class="sxs-lookup"><span data-stu-id="ddebc-116">Namespace</span></span>|<span data-ttu-id="ddebc-117">Défini dans root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ddebc-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ddebc-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ddebc-118">See Also</span></span>  
 <xref:System.ServiceModel.Description.MustUnderstandBehavior>
