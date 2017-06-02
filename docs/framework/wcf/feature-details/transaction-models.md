---
title: "Mod&#232;les de transaction | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 48a8bc1b-128b-4cf1-a421-8cc73223c340
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Mod&#232;les de transaction
Cette rubrique décrit la relation entre les modèles de programmation de transactions et les composants d'infrastructure que Microsoft fournit.  
  
 Lors de l'utilisation de transactions dans [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], il est important de comprendre que vous ne choisissez pas entre des modèles transactionnels différents, mais que vous évoluez dans des couches différentes d'un modèle intégré et cohérent.  
  
 Les sections suivantes décrivent les trois composants principaux d'une transaction.  
  
## Transactions WCF \(Windows Communication Foundation\)  
 La prise en charge des transactions dans [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vous permet d'écrire des services transactionnels.De plus, avec sa prise en charge du protocole WS\-AtomicTransaction \(WS\-AT\), les applications peuvent transférer des transactions aux services Web construits à l'aide de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ou d'une technologie tiers.  
  
 Dans un service ou une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], les fonctionnalités de la transaction [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fournissent des attributs et la configuration permettant de spécifier de façon déclarative comment et quand l'infrastructure doit créer, transmettre et synchroniser des transactions.  
  
## Transactions System.Transactions  
 L'espace de noms <xref:System.Transactions> fournit un modèle de programmation explicite basé sur la classe <xref:System.Transactions.Transaction>, ainsi qu'un modèle de programmation implicite à utilisant la classe <xref:System.Transactions.TransactionScope>, dans lequel l'infrastructure gère automatiquement les transactions.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] la création d'une application transactionnelle qui utilise ces deux modèles, consultez [Écriture d'une application transactionnelle](http://go.microsoft.com/fwlink/?LinkId=94947).  
  
 Dans un service ou une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], <xref:System.Transactions> fournit le modèle de programmation pour créer des transactions dans une application cliente et pour interagir explicitement avec une transaction, si nécessaire, au sein d'un service.  
  
## Transactions MSDTC  
 MSDTC \(Microsoft Distributed Transaction Coordinator\) est un gestionnaire de transactions qui prend en charge les transactions distribuées.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] le [Guide de référence du programmeur](http://go.microsoft.com/fwlink/?LinkId=94948).  
  
 Dans un service ou une application [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], MSDTC fournit l'infrastructure pour la coordination de transactions créées dans un client ou un service.