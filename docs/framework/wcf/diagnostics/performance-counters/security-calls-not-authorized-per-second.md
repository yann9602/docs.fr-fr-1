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
# <a name="security-calls-not-authorized-per-second"></a>Appels de sécurité non autorisés par seconde
Nom du compteur : Appels de sécurité non autorisés par seconde.  
  
## <a name="description"></a>Description  
 Nombre d'appels dont l'autorisation a échoué lors de cette opération en une seconde.  
  
 Ce compteur est incrémenté lorsque la méthode <xref:System.ServiceModel.ServiceAuthorizationManager.CheckAccess%2A> retourne la valeur `false`. Il indique que le message entrant provient d’un utilisateur valide et qu’il est correctement protégé, mais que l’utilisateur n’est pas autorisé à exécuter des tâches spécifiques.  
  
 Ce compteur est de type de compteur de performances [PERF_COUNTER_COUNTER](http://go.microsoft.com/fwlink/?LinkID=94649), dont la valeur est calculée à l’aide de la formule suivante.  
  
 (N 1 - N 0 ) / ( (D 1 -D 0 ) / F)
