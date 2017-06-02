---
title: "Traitement ordonn&#233; des messages en mode de concurrence simple | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Traitement ordonn&#233; des messages en mode de concurrence simple
WCF n'offre aucune garantie quant à l'ordre dans lequel les messages sont traités, à moins que le canal sous\-jacent soit un canal de session. Par exemple, un service WCF qui utilise MsmqInputChannel, qui n'est pas un canal de session, ne traite pas les messages dans l'ordre. Il existe quelques cas où un développeur peut souhaiter dans le traitement dans l'ordre mais ne pas utiliser de sessions.Cette rubrique décrit comment configurer ce comportement lorsqu'un service s'exécute en mode de concurrence simple.  
  
## Traitement des messages dans l'ordre  
 Un nouvel attribut nommé <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a été ajouté à la classe <xref:System.ServiceModel.ServiceBehaviorAttribute>.Lorsque <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> a la valeur true et <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> a la valeur <xref:System.ServiceModel.ConcurrencyMode> les messages envoyés au service sont traités dans l'ordre.L'extrait de code suivant illustre comment définir ces attributs.  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
  
```  
  
 Si une autre valeur est affectée à la propriété <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A>, une exception <xref:System.InvalidOperationException> est levée.  
  
## Voir aussi  
 [Sessions, instanciation et accès concurrentiel](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)   
 [Concurrency](../../../../docs/framework/wcf/samples/concurrency.md)