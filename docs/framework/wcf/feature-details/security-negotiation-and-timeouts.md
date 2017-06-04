---
title: "N&#233;gociation et d&#233;lais de s&#233;curit&#233; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 02a428f1-84e5-4d28-a11f-53ce31d63196
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# N&#233;gociation et d&#233;lais de s&#233;curit&#233;
Lorsque les clients et les services s'authentifient, [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] prend en charge un mode qui permet la négociation de leurs informations d'identification.Dans un tel cas, un échange potentiellement multi\-segment intervient entre le client et le service. Il permet la propagation des informations d'identification du service vers le client.La propriété <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.NegotiationTimeout%2A> contrôle le délai nécessaire à l'exécution de cet échange.Toutefois, ce délai est appliqué uniquement lorsque l'échange nécessite plusieurs demandes\-réponses.Lorsque la négociation s'effectue en une seule boucle, ce délai n'est pas utilisé.  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>   
 [Comment : définir une inclinaison de l'horloge maximale](../../../../docs/framework/wcf/feature-details/how-to-set-a-max-clock-skew.md)