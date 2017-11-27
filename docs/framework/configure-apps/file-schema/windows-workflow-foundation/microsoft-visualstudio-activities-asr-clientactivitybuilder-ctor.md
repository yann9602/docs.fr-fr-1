---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location: Microsoft.VisualStudio.Activities.dll
api_type: Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7b73274a09ae748cdf1ee33c885de86b1f52c105
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a><span data-ttu-id="f2202-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span><span class="sxs-lookup"><span data-stu-id="f2202-102">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor</span></span>
<span data-ttu-id="f2202-103">Crée une instance de la [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) classe.</span><span class="sxs-lookup"><span data-stu-id="f2202-103">Creates an instance of the [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2202-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2202-104">Syntax</span></span>  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2202-105">Paramètres</span><span class="sxs-lookup"><span data-stu-id="f2202-105">Parameters</span></span>  
  
## <a name="parameter-values"></a><span data-ttu-id="f2202-106">Valeurs du paramètre</span><span class="sxs-lookup"><span data-stu-id="f2202-106">Parameter Values</span></span>  
 <span data-ttu-id="f2202-107">*operationDescription*</span><span class="sxs-lookup"><span data-stu-id="f2202-107">*operationDescription*</span></span>  
  
 <span data-ttu-id="f2202-108">Décrit l'opération à effectuer dans l'activité de workflow qui doit être générée, notamment le nom de l'opération, le type de retour et les informations de paramètre.</span><span class="sxs-lookup"><span data-stu-id="f2202-108">Describes the operation to be performed in the workflow activity that is to be generated, including the operation name, return type, and parameter information.</span></span> <span data-ttu-id="f2202-109">La valeur de ce paramètre ne doit pas être **null**.</span><span class="sxs-lookup"><span data-stu-id="f2202-109">The value of this parameter must not be **null**.</span></span> <span data-ttu-id="f2202-110">Elle doit décrire une opération synchrone qui utilise un contrat de message et prend un argument avec un message.</span><span class="sxs-lookup"><span data-stu-id="f2202-110">It should describe a synchronous operation which uses a message contract and takes an argument with one message.</span></span> <span data-ttu-id="f2202-111">Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.</span><span class="sxs-lookup"><span data-stu-id="f2202-111">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="f2202-112">*nom de configuration*</span><span class="sxs-lookup"><span data-stu-id="f2202-112">*configurationName*</span></span>  
  
 <span data-ttu-id="f2202-113">Spécifie le nom de configuration du point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="f2202-113">Specifies the endpoint configuration name.</span></span> <span data-ttu-id="f2202-114">La valeur de ce paramètre ne doit pas être soit **null** ou vide.</span><span class="sxs-lookup"><span data-stu-id="f2202-114">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="f2202-115">Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.</span><span class="sxs-lookup"><span data-stu-id="f2202-115">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
 <span data-ttu-id="f2202-116">*proxyNamespace*</span><span class="sxs-lookup"><span data-stu-id="f2202-116">*proxyNamespace*</span></span>  
  
 <span data-ttu-id="f2202-117">Spécifie l'espace de noms du service pour l'opération.</span><span class="sxs-lookup"><span data-stu-id="f2202-117">Specifies the service namespace for the operation.</span></span> <span data-ttu-id="f2202-118">La valeur de ce paramètre ne doit pas être soit **null** ou vide.</span><span class="sxs-lookup"><span data-stu-id="f2202-118">The value of this parameter must not be either **null** or empty.</span></span> <span data-ttu-id="f2202-119">Si ces conditions ne sont pas satisfaites, le résultat d'exécution du constructeur et des autres méthodes de cette classe est indéfini.</span><span class="sxs-lookup"><span data-stu-id="f2202-119">If these conditions are not satisfied, the runtime result of using the constructor and the other methods of this class are undefined.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2202-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f2202-120">See Also</span></span>  
 [<span data-ttu-id="f2202-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span><span class="sxs-lookup"><span data-stu-id="f2202-121">Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder</span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
