---
title: "Operation, classe | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# Operation, classe
Opération  
  
## Syntaxe  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## Méthodes  
 La classe Operation ne définit pas de méthodes.  
  
## Propriétés  
 La classe Operation a les propriétés suivantes :  
  
### Action  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 L'action WS\-Addressing du message de demande.  
  
### AsyncPattern  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique qu'une opération est implémentée de façon asynchrone à l'aide d'une paire de méthode `Begin` \[signes inférieur à et supérieur à\] et `End` \[signes inférieur à et supérieur à\] dans un contrat de service.  
  
### Comportements  
 Type de données : tableau de comportements  
  
 Type d'accès : lecture seule  
  
 Comportements associés à cette opération.  
  
### IsCallback  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 True lorsque l'opération est une opération de rappel.  
  
### IsInitiating  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si la méthode implémente une opération qui peut initialiser une session sur le serveur.  
  
### IsOneWay  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si une opération retourne un message de réponse.  
  
### IsTerminating  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si une opération retourne un message de réponse.  
  
### MethodSignature  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Signature de méthode de l'opération.  
  
### Nom  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom de l'opération.  
  
### ParameterTypes  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Types des paramètres de l'opération.  
  
### ReplyAction  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur de l'action SOAP pour le message de réponse de l'opération.  
  
### ReturnType  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Type de retour de l'opération.  
  
## Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|------------------------------------|  
|Espace de noms|Défini dans root\\ServiceModel|  
  
## Voir aussi  
 <xref:System.ServiceModel.Description.OperationDescription>