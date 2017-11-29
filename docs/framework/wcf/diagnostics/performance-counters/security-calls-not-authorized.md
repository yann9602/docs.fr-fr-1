---
title: "Appels de sécurité non autorisés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cb6acdcd-7336-42e1-9ae8-ac891336cd58
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: d66e700aa3aee0e577955a978cff0f5cedd84851
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="security-calls-not-authorized"></a><span data-ttu-id="db47b-102">Appels de sécurité non autorisés</span><span class="sxs-lookup"><span data-stu-id="db47b-102">Security Calls Not Authorized</span></span>
<span data-ttu-id="db47b-103">Nom du compteur : Appels de sécurité non autorisés.</span><span class="sxs-lookup"><span data-stu-id="db47b-103">Counter Name: Security Calls Not Authorized.</span></span>  
  
## <a name="description"></a><span data-ttu-id="db47b-104">Description</span><span class="sxs-lookup"><span data-stu-id="db47b-104">Description</span></span>  
 <span data-ttu-id="db47b-105">Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`.</span><span class="sxs-lookup"><span data-stu-id="db47b-105">This counter is incremented when the <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> method returns `false`.</span></span> <span data-ttu-id="db47b-106">Il indique que le message entrant provient d'un utilisateur valide et qu'il est correctement protégé, mais que l'utilisateur n'est pas autorisé à exécuter des tâches spécifiques.</span><span class="sxs-lookup"><span data-stu-id="db47b-106">It indicates that the incoming message is from a valid user and protected properly, but the user is not authorized to do specific tasks.</span></span>
