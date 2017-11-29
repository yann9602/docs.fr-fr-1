---
title: "Appels de sécurité non autorisés par seconde"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f189767-8c05-478a-8f0b-9228e5d351e5
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 73500901b89eb2cb61fe34895ce6ba150b7e3357
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="security-calls-not-authorized-per-second"></a><span data-ttu-id="f3ffb-102">Appels de sécurité non autorisés par seconde</span><span class="sxs-lookup"><span data-stu-id="f3ffb-102">Security Calls Not Authorized Per Second</span></span>
<span data-ttu-id="f3ffb-103">Nom du compteur : Appels de sécurité non autorisés par seconde.</span><span class="sxs-lookup"><span data-stu-id="f3ffb-103">Counter Name: Security Calls Not Authorized Per Second.</span></span>  
  
## <a name="description"></a><span data-ttu-id="f3ffb-104">Description</span><span class="sxs-lookup"><span data-stu-id="f3ffb-104">Description</span></span>  
 <span data-ttu-id="f3ffb-105">Nombre d'appels dont l'autorisation a échoué lors de cette opération en une seconde.</span><span class="sxs-lookup"><span data-stu-id="f3ffb-105">Number of calls that failed authorization in this operation in a second.</span></span>  
  
 <span data-ttu-id="f3ffb-106">Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="f3ffb-106">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="f3ffb-107">Il indique que le message entrant provient d’un utilisateur valide et qu’il est correctement protégé, mais que l’utilisateur n’est pas autorisé à exécuter des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="f3ffb-107">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>  
  
 <span data-ttu-id="f3ffb-108">Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.</span><span class="sxs-lookup"><span data-stu-id="f3ffb-108">This counter is of performance counter type [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), whose value is calculated using the following formula.</span></span>  
  
 <span data-ttu-id="f3ffb-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span><span class="sxs-lookup"><span data-stu-id="f3ffb-109">(N 1 - N 0 ) / ( (D 1 -D 0 ) / F)</span></span>
