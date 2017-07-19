---
title: "Cycle de vie de la programmation de base | Microsoft Docs"
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
  - "création de service [WCF]"
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
caps.latest.revision: 36
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 36
---
# Cycle de vie de la programmation de base
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] permet aux applications de communiquer, qu'elles se trouvent sur le même ordinateur, sur Internet ou sur des plateformes d'application différentes.Cette rubrique décrit brièvement les tâches qui sont requises pour générer une application [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].Pour obtenir un exemple d'application fonctionnel, consultez [Didacticiel de mise en route](../../../docs/framework/wcf/getting-started-tutorial.md).  
  
## Tâches de base  
 Les tâches de base à accomplir sont les suivantes, dans l'ordre :  
  
1.  Définition du contrat de service.Un contrat de service spécifie la signature d'un service, les données qu'il échange et les autres données requises contractuellement.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Conception de contrats de service](../../../docs/framework/wcf/designing-service-contracts.md).  
  
2.  Implémentation du contrat.Pour implémenter un contrat de service, créez une classe qui implémente le contrat et spécifiez les comportements personnalisés requis pour le runtime.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
3.  Configuration du service en spécifiant les informations de points de terminaison et d'autres informations de comportement.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Configuration des services](../../../docs/framework/wcf/configuring-services.md).  
  
4.  Hébergement du service.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Hébergement de services](../../../docs/framework/wcf/hosting-services.md).  
  
5.  Création d'une application cliente.[!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Génération de clients](../../../docs/framework/wcf/building-clients.md).  
  
 Bien que les rubriques de cette section suivent cet ordre, certains scénarios ne commencent pas au début.Par exemple, si vous souhaitez générer un client pour un service préexistant, démarrez à l'étape 5.Autrement, si vous générez un service que d'autres utiliseront, vous pouvez ignorer l'étape 5.  
  
 Une fois que vous maîtrisez le développement des contrats de service, vous pouvez également lire [Introduction à l'extensibilité](../../../docs/framework/wcf/introduction-to-extensibility.md).Si vous rencontrez des problèmes avec votre service, vérifiez [Démarrage rapide de la résolution des problèmes WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) pour savoir si d'autres personnes sont confrontées aux mêmes problèmes ou à des problèmes similaires.  
  
## Voir aussi  
 [Implémentation de contrats de service](../../../docs/framework/wcf/implementing-service-contracts.md)