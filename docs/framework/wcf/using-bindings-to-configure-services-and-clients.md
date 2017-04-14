---
title: "Utilisation de liaisons pour configurer des services et des clients | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "liaisons (WCF), using"
ms.assetid: c39479c3-0766-4a17-ba4c-97a74607f392
caps.latest.revision: 33
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 33
---
# Utilisation de liaisons pour configurer des services et des clients
Les liaisons sont des objets qui spécifient les détails de communication requis pour se connecter à un point de terminaison.  Plus spécifiquement, les liaisons contiennent des informations de configuration utilisées pour créer l'exécution du client ou du service en définissant les caractéristiques des transports, les formats de transmission \(encodage de message\) et les protocoles à utiliser pour le point de terminaison ou canal client respectif.  Pour créer un service [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] opérationnel, chaque point de terminaison dans le service requiert une liaison.  Cette rubrique explique ce que sont les liaisons, comment elles sont définies et comment une liaison particulière est spécifiée pour un point de terminaison.  
  
## Ce que définit une liaison  
 Les informations contenues dans une liaison peuvent être basiques ou très complexes.  La liaison la plus basique spécifie uniquement le protocole de transport \(par exemple HTTP\) qui doit être utilisé pour se connecter au point de terminaison.  Plus généralement, les informations d'une liaison relatives à la procédure de connexion à un point de terminaison appartiennent à l'une des catégories répertoriées dans le tableau suivant.  
  
 Protocoles  
 Détermine le mécanisme de sécurité utilisé, soit une fonction de messagerie fiable, soit des paramètres de flux de contexte de transaction.  
  
 Transport  
 Détermine le protocole de transport sous\-jacent à utiliser \(par exemple, TCP ou HTTP\).  
  
 Encodage  
 Détermine l'encodage de message, par exemple texte\/XML, binaire ou MTOM \(Message Transmission Optimization Mechanism\), qui détermine la façon dont les messages sont représentés comme flux d'octets sur le câble.  
  
## Liaisons fournies par le système  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] inclut un ensemble de liaisons fournies par le système conçues pour répondre à la plupart des conditions et des scénarios de l'application.  Les classes suivantes représentent quelques exemples de liaisons fournies par le système :  
  
-   <xref:System.ServiceModel.BasicHttpBinding> : liaison de protocole HTTP adaptée à la connexion à des services Web conformes à la spécification WS\-I Basic Profile 1.1 \(par exemple, services basés sur les services Web ASP.NET \[ASMX\]\).  
  
-   <xref:System.ServiceModel.WsHttpBinding> : liaison de protocole HTTP adaptée à la connexion à des points de terminaison conformes aux protocoles de spécification des services Web.  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding> : utilise les technologies d'encodage binaire .NET et de tramage conjointement au transport de canal nommé Windows pour se connecter à d'autres points de terminaison [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sur le même ordinateur.  
  
-   <xref:System.ServiceModel.NetMsmqBinding> : utilise les technologies d'encodage binaire .NET et de tramage conjointement à Message Queuing \(également appelée MSMQ\) pour créer des connexions de message en file d'attente avec d'autres points de terminaison [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
 Pour obtenir une liste complète des liaisons fournies par le système, avec leurs descriptions, consultez [Liaisons fournies par le système](../../../docs/framework/wcf/system-provided-bindings.md).  
  
## Liaisons personnalisées  
 Si la collection de liaisons fournie par le système n'a pas la combinaison correcte de fonctionnalités requises par une application de service, vous pouvez créer une liaison <xref:System.ServiceModel.Channels.CustomBinding>.  [!INCLUDE[crabout](../../../includes/crabout-md.md)] les éléments d'une liaison <xref:System.ServiceModel.Channels.CustomBinding>, consultez [\<customBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) et [Liaisons personnalisées](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## Utilisation des liaisons  
 L'utilisation des liaisons implique deux étapes simples :  
  
1.  Sélectionner ou définir une liaison.  La méthode la plus simple consiste à choisir l'une des liaisons fournies par le système et à utiliser ses paramètres par défaut.  Vous pouvez également choisir une liaison fournie par le système et réinitialiser ses valeurs de propriété en fonction de vos spécifications.  En guise d'alternative, vous pouvez créer une liaison personnalisée et définir chaque propriété selon vos besoins.  
  
2.  Créer un point de terminaison qui utilise cette liaison.  
  
## Code et configuration  
 Vous pouvez définir ou configurer des liaisons par le biais de code ou de configuration.  Ces deux approches sont indépendantes du type de liaison utilisé, par exemple si vous utilisez une liaison <xref:System.ServiceModel.Channels.CustomBinding> ou fournie par le système.  En général, l'utilisation de code permet de bénéficier d'un contrôle total sur la définition d'une liaison lorsque vous compilez.  L'utilisation de configuration, en revanche, permet à un administrateur système ou à l'utilisateur d'un service ou client [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] de modifier les paramètres des liaisons.  Cette souplesse est souvent souhaitable car il n'existe aucune méthode pour prévoir les exigences matérielles et conditions réseau spécifiques dans lesquelles une application [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] sera déployée.  Le fait de séparer les informations de liaison \(et d'adressage\) du code permet aux administrateurs de modifier les détails de liaison sans avoir à recompiler ou à redéployer l'application.  Notez que si la liaison est définie dans du code, elle remplace toute définition basée sur la configuration effectuée dans le fichier de configuration.  Pour obtenir des exemples de ces approches, consultez les rubriques suivantes :  
  
-   [Comment : héberger un service WCF dans une application managée](../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md) fournit un exemple de création d'une liaison dans du code.  
  
-   [Comment : configurer un client](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md) fournit un exemple de création d'un client à l'aide de la configuration.  
  
## Voir aussi  
 [Vue d'ensemble de la création de points de terminaison](../../../docs/framework/wcf/endpoint-creation-overview.md)   
 [Comment : spécifier une liaison de service dans la configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)   
 [Comment : spécifier une liaison de service dans le code](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-code.md)   
 [Comment : spécifier une liaison de client dans la configuration](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-configuration.md)   
 [Comment : spécifier une liaison client dans le code](../../../docs/framework/wcf/how-to-specify-a-client-binding-in-code.md)