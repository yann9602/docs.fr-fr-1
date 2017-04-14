---
title: "TransactionFlowBindingElement | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a9656fe-2400-45ca-ad79-92715c8cf190
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# TransactionFlowBindingElement
TransactionFlowBindingElement  
  
## Syntaxe  
  
```  
class TransactionFlowBindingElement : BindingElement  
{  
  string IssuedTokens;  
  string TransactionProtocol;  
  boolean Transactions;  
};  
```  
  
## Méthodes  
 La classe TransactionFlowBindingElement ne définit pas de méthodes.  
  
## Propriétés  
 La classe TransactionFlowBindingElement dispose des propriétés suivantes :  
  
### IssuedTokens  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Définit les spécifications d'un en\-tête de jetons de sécurité publié \(IssuedTokens de WS\-Trust\).  
  
### TransactionProtocol  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Protocole de transactions utilisé par le service pour transférer les transactions.  
  
### Transactions  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si la transaction entrante est prise en charge.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>