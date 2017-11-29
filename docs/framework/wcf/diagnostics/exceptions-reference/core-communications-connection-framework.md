---
title: "Communications principales : infrastructure de connexion"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 61ee00e1-896d-47c8-942f-1db28ac89cdc
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: c485c05c1c54a19a102a8378dc79c908a29aa658
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="core-communications-connection-framework"></a>Communications principales : infrastructure de connexion
Cette rubrique répertorie toutes les exceptions générées par l'infrastructure de connexion [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)].  
  
## <a name="exception-list"></a>Liste des exceptions  
  
|Code de la ressource|Chaîne de la ressource|  
|-------------------|---------------------|  
|CloseTimedOut|La méthode Close a expiré après l'heure spécifiée. Augmentez la valeur du délai d'attente de l'appel à la méthode Close ou la valeur CloseTimeout sur la liaison. Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.|  
|ContentTypeMismatch|Le type de contenu spécifié a été envoyé à un service qui attendait . Il se peut que les liaisons client et service ne se correspondent pas.|  
|DuplexChannelAbortedDuringOpen|Le canal duplex vers s'est fermé pendant le processus Open.|  
|FramingValueNotAvailable|La valeur n'est pas accessible parce qu'elle n'est pas complètement décodée.|  
|OperationAbortedDuringConnectionEstablishment|L'opération a pris pendant l'établissement d'une connexion à .|  
|ReceiveTimedOut2|L'opération de réception a dépassé le délai imparti. Le temps alloué à cette opération peut avoir été une partie d'un délai d'expiration plus long.|  
|SendCannotBeCalledAfterCloseOutputSession|Vous ne pouvez pas envoyer des messages sur un canal après que CloseOutputSession a été appelée.|
