---
title: "Point de terminaison | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Point de terminaison
Point de terminaison  
  
## Syntaxe  
  
```  
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## Méthodes  
 La classe Endpoint définit la méthode suivante.  
  
|Méthode|Description|  
|-------------|-----------------|  
|[GetOperationCounterInstanceName](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|Récupère le nom d'instance du compteur de performance d'opération|  
  
## Propriétés  
 La classe Endpoint a les propriétés suivantes :  
  
### Address  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 URI qui contient l'adresse du point de terminaison.  
  
### AddressHeaders  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Collection d'en\-têtes d'adresse jointe à ce point de terminaison.  
  
### AddressIdentity  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Identité du point de terminaison.  
  
### AppDomainId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 ID du domaine d'application qui héberge le point de terminaison.  
  
### Comportements  
 Type de données : tableau de comportements  
  
 Type d'accès : lecture seule  
  
 Collection de comportements implémentée par ce point de terminaison.  
  
### Binding  
 Type de données : liaison  
  
 Type d'accès : lecture seule  
  
 Liaison utilisée par ce point de terminaison.  
  
### ContractName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Chaîne qui spécifie quel contrat est exposé par ce point de terminaison.  
  
### CounterInstanceName  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom de l'instance des compteurs de performance du point de terminaison.  
  
### ListenUri  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 URI sur lequel le point de terminaison écoute.  
  
### Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom unique de ce point de terminaison.  
  
### ProcessId  
 Type de données : sint32  
  
 Type d'accès : lecture seule  
  
 ID du processus qui héberge le point de terminaison.  
  
### ref  
 Type de données: contrat  
  
 Type d'accès : lecture seule  
  
 Le contrat exposé par ce point de terminaison.  
  
## Spécifications  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|