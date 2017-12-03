---
title: "&lt;synchronousReceive&gt;, élément"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 79d78517b62e4476106ff1ed7978c770a17caf2a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="ltsynchronousreceivegt-element"></a>&lt;synchronousReceive&gt;, élément
Cet élément de configuration est utilisé en vue de spécifier le comportement de réception des messages au moment de l'exécution dans une application cliente ou de service. Il n'a aucun attribut ou élément enfant.  
  
 \<système. ServiceModel >  
\<comportements >  
\<endpointBehaviors >  
\<comportement >  
\<synchronousReceive >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<synchronousReceive />  
```  
  
## <a name="attributes-and-elements"></a>Attributs et éléments  
 Les sections suivantes décrivent des attributs, des éléments enfants et des éléments parents.  
  
### <a name="attributes"></a>Attributs  
 Aucun  
  
### <a name="child-elements"></a>Éléments enfants  
 Aucun.  
  
### <a name="parent-elements"></a>Éléments parents  
  
|Élément|Description|  
|-------------|-----------------|  
|[\<comportement >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Spécifie un comportement de point de terminaison.|  
  
## <a name="remarks"></a>Remarques  
 Utilisez ce comportement pour indiquer à l’écouteur de canal d’utiliser une réception synchrone au lieu de celle par défaut (asynchrone). [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] émet un nouveau thread pour pomper chaque canal accepté. Si le nombre de canaux est important, il est possible de rencontrer une insuffisance de threads.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
