---
title: Operation, classe
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54566bc452baa2e02cef7d8d13d29fcd5864c95c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="operation-class"></a>Operation, classe
Opération  
  
## <a name="syntax"></a>Syntaxe  
  
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
  
## <a name="methods"></a>Méthodes  
 La classe Operation ne définit pas de méthodes.  
  
## <a name="properties"></a>Propriétés  
 La classe Operation a les propriétés suivantes :  
  
### <a name="action"></a>Action  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 L'action WS-Addressing du message de demande.  
  
### <a name="asyncpattern"></a>AsyncPattern  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique qu’une opération est implémentée à l’aide de façon asynchrone un `Begin`[Ouvrir/fermer les crochets pointus] et `End`paire de méthodes [ouverture/fermeture crochets] dans un contrat de service.  
  
### <a name="behaviors"></a>comportements  
 Type de données : tableau de comportements  
  
 Type d'accès : lecture seule  
  
 Comportements associés à cette opération.  
  
### <a name="iscallback"></a>IsCallback  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 True lorsque l'opération est une opération de rappel.  
  
### <a name="isinitiating"></a>IsInitiating  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si la méthode implémente une opération qui peut initialiser une session sur le serveur.  
  
### <a name="isoneway"></a>IsOneWay  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si une opération retourne un message de réponse.  
  
### <a name="isterminating"></a>IsTerminating  
 Type de données : booléen  
  
 Type d'accès : lecture seule  
  
 Indique si une opération retourne un message de réponse.  
  
### <a name="methodsignature"></a>MethodSignature  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Signature de méthode de l'opération.  
  
### <a name="name"></a>Name  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Nom de l'opération.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Type de données : tableau de chaînes  
  
 Type d'accès : lecture seule  
  
 Types des paramètres de l'opération.  
  
### <a name="replyaction"></a>ReplyAction  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Valeur de l'action SOAP pour le message de réponse de l'opération.  
  
### <a name="returntype"></a>ReturnType  
 Type de données : chaîne  
  
 Type d'accès : lecture seule  
  
 Type de retour de l’opération.  
  
## <a name="requirements"></a>Configuration requise  
  
|MOF|Déclaré dans Servicemodel.mof.|  
|---------|-----------------------------------|  
|Espace de noms|Défini dans root\ServiceModel|  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ServiceModel.Description.OperationDescription>
